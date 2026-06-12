---
title: "Dark Mode Theme for 16.04"
date: 2016-07-11
forum: General Help
---

### Post by mmbabji on 2016-07-11
I am looking for the dark mode theme for 16.04 
some thing like Night Mode app we see in android apps. 

the theme should be more gray .

basically it should avoid white scale to the max extent possible over the monitor.

 i use 16.04 LTS with flashback. 

(it would be better if it can be done over apt-get only)

---

### Post by CantankRus on 2016-07-12
Try the Arc themes which you can install from the noobslab/themes ppa.
```
sudo add-apt-repository ppa:noobslab/themes
sudo apt update
sudo apt install arc-theme
```

Package contains a number of themes....Arc-dark is probably what you want.

You can also install redshift-gtk.
> redshift adjusts the color temperature of your screen according to your surroundings. 
This may help your eyes hurt less if you are working in front of the screen at night.
The color temperature is set according to the position of the sun. A different color temperature is set during night and daytime. 
During twilight and early morning, the color temperature transitions smoothly from night to daytime temperature to allow your eyes to slowly adapt.
```
sudo apt install redshift-gtk
```

Create a config @ **~/.config/redshift.conf**
You can get your lat/long details from [http://www.latlong.net/](http://www.latlong.net/)
eg: here is my **~/.config/redshift.conf**...
```
; Global settings for redshift
[redshift]
; Set the day and night screen temperatures
temp-day=5000
temp-night=3500

; Enable/Disable a smooth transition between day and night
; 0 will cause a direct change from day to night screen temperature.
; 1 will gradually increase or decrease the screen temperature.
transition=1

; Set the screen brightness. Default is 1.0.
;brightness=0.9
; It is also possible to use different settings for day and night
; since version 1.8.
brightness-day=0.7
brightness-night=0.8
; Set the screen gamma (for all colors, or each color channel
; individually)
;gamma=0.9
;gamma=0.8:0.7:0.8
; This can also be set individually for day and night since
; version 1.10.
gamma-day=0.9:0.8:0.9
gamma-night=0.8:0.7:0.8

; Set the location-provider: 'geoclue', 'geoclue2', 'manual'
; type 'redshift -l list' to see possible values.
; The location provider settings are in a different section.
location-provider=manual

; Set the adjustment-method: 'randr', 'vidmode'
; type 'redshift -m list' to see all possible values.
; 'randr' is the preferred method, 'vidmode' is an older API.
; but works in some cases when 'randr' does not.
; The adjustment method settings are in a different section.
adjustment-method=randr

; Configuration of the location-provider:
; type 'redshift -l PROVIDER:help' to see the settings.
; ex: 'redshift -l manual:help'
; Keep in mind that longitudes west of Greenwich (e.g. the Americas)
; are negative numbers.
[manual]
lat=-32.235044
lon=115.820873

; Configuration of the adjustment-method
; type 'redshift -m METHOD:help' to see the settings.
; ex: 'redshift -m randr:help'
; In this example, randr is configured to adjust screen 1.
; Note that the numbering starts from 0, so this is actually the
; second screen. If this option is not specified, Redshift will try
; to adjust _all_ screens.
[randr]
screen=0

```
When editing your config, you will need to quit and restart redshift to see changes..
If you have indicator-applet-complete installed and added to the panel in the flashback session you will see a redshift indicator.

---

