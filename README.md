# 737AEFCU
XPlane 11 Plugin for the b737 zibo mod

Version: 2021.4.1-alpha

## What works or should work

* AP follow - stick follows yoke movement during AP (CMD A/B) on
* Aileron trim -> stick moves according to trim
* Stall shaker -> no force modulation for now / only shaker effect
* Damper -> stick movement gets dampend
* Independent centering forces for aileron and elevator

## Not yet implemented

* Linux (maybe) & OSX (probably never) support
* Elevator droop on Hydraulics off - is that a thing in the 737?
* airspeed relative forces - probably next in line
* Stall control force modulation
* Stick selection
* open for suggestions
*
* GUI

## Install

extract zip to X-Plane 11\Aircraft\Extra Aircraft\B737-800X\plugins so that you have a zz737AEFCU folder inside plugins

## Config

### Zibo

* Realism Settings -> Yoke Movement OFF
* Hardware -> Yoke Autocenter OFF

### XPlane

* Set stick x & y axis reponse curves to complete linear (otherwise the AP disc might do strange stuff)
* Same goes for control sensitivity - fully linear 

### The Plugin
for now only via texteditor - edit settings.cfg inside zz737AEFCU folder

### settings.cfg

thread_sleep_ms_long=1 <- poll time for the force / joystick thread in ms (1-100) - set to higher values if you get probs with FPS (you shouldn't so please report) 

aileron_max_force_double=0.7 <- set between 0.0 (no force) - 1.0 (max force)  

elevator_max_force_double=1.0 <- same as for aileron

damper_max_force_double=0.6 <- same as for aileron

ap_disco_offset_double=0.2 <- set between 0.1 (very sensitive) - 1.0 (practically off)

stall_shaker_force_double=0.5 <- same as for aileron

* There aren't much safety checks for now - so be carefull with the settings.cfg
* Use PluginAdmin to cycle dis-/enable to reload the config file

## Remarks

* tested this version with XP11.5 and zibo .16 and an MS Sidewinder 2 FF
* force do not mix super well on the sidewinder - I build in some proctection to avoid a "resonance catastrophe" but if you experience wild shaking tune down the damper force
* you need to tape over the "hand-detection-LED" on the Sidewinder otherwise the AP follow won't work
* The plugin indepentently disconnects the AP (via cpt-ap-disco btn trigger) when offset between stick pos in RL and sim > ap_disco_offset_double 
* Plugin grabs the first FF capabable stick/harware it finds - this doesn't always work as indetendet so unplug everything with force feedback until your in the cockpit
* For FF to work plugin need exclusive access - that means it will conflict with other force feedback addons - I buildin a check for XPforce -> gets deactivated on load and reactivated after deactivation of the plugin
