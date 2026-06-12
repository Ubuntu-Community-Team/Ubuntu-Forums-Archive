---
title: "night light not working properly - the sun already set but it still doesn't starts"
date: 2019-11-16
forum: General Help
---

### Post by ronjjjg8885 on 2019-11-16
do you have a clue about that?

thanks!!!

---

### Post by jetsam on 2019-11-16
What sort of night light?  Can you link to a picture?  Does it run Linux?

---

### Post by uRock on 2019-11-16
> **ronjjjg8885 said:**
> do you have a clue about that?

thanks!!! You can configure the time manually. [https://www.omgubuntu.co.uk/2017/07/adjust-color-temperature-gnome-night-light](https://www.omgubuntu.co.uk/2017/07/adjust-color-temperature-gnome-night-light)

> **jetsam said:**
> What sort of night light?  Can you link to a picture?  Does it run Linux?

Really?

---

### Post by jetsam on 2019-11-16
> Really? 

Yep :)

Home automation, especially a DIY setup, often has a Raspberry Pi guiding the show...  

Here's another one I just found, adjusting monitor color temperature after dark.  I guess blue light has gotten a bad reputation in the last few years for causing eye strain and insomnia.

Edit:  This is similar to your link, but there's command line options and a few more details...

[How to Activate Night Light on Ubuntu Desktop]("https://vitux.com/how-to-activate-night-light-on-ubuntu-desktop/")

One more edit (last one here):   Here's a crib sheet of open source home automation software platforms.  It's almost all linux based, but differs in hardware and network architecture: [6 open source home automation tools]("https://opensource.com/tools/home-automation").

---

### Post by Skaperen on 2019-11-16
it would be nice if you could just tell it your location (lat,long), sync your clock, and enable your camera, and it will just do it right based on knowing your sun position, seeing your actual color change, and knowing what is optimal.  if you live close to or beyond arctic circles, the light value can vary less by hour and more by season.

---

### Post by jetsam on 2019-11-16
...or connect with the solar garden and driveway lights and use them as sensors.  Then it could vary based on weather, the time someone arrives at the house, and also change seasonally with the annual time cycle shifts.  It is sort of dizzying to think of the potential for stuff like that to work.  I'm so skeptical of IOT based devices, but some of it could be pretty great if it were reliable and secure.

---

### Post by ronjjjg8885 on 2019-11-16
my clock is synced

---

### Post by ronjjjg8885 on 2019-11-16
> **uRock said:**
> You can configure the time manually. [https://www.omgubuntu.co.uk/2017/07/adjust-color-temperature-gnome-night-light](https://www.omgubuntu.co.uk/2017/07/adjust-color-temperature-gnome-night-light)



Really?

i will do that manualy but i still prefer automatic if it is possible

---

### Post by ajgreeny on 2019-11-16
This does not really answer your query about night-light, but I use Xubuntu, not gnome and I suspect night-light is just for gnome
Redshift gives you an alternative to use which can change the colour temperature of your display using geoclue2 very easily.

Install redshift and redshift-gtk and geoclue-2.0.  You then need to edit the /etc/geoclue/geoclue.conf file by adding 
```
[redshift]
allowed=truedoes
system=false
users=
``` to the bottom of the file.  Perhaps you need a similar edit of some file for night-light to work automatically?

Finally edit for the configuration you need in ~/.config/redshift.conf.
As an example, here's my config file.
All lines starting with a semi-colon ; are commented out and do nothing, but all the uncommented lines are the ones you can change to your own preferences.
```
[redshift]
; Set the day and night screen temperatures
temp-day=6500
temp-night=3500

; Enable/Disable a smooth transition between day and night
; 0 will cause a direct change from day to night screen temperature.
; 1 will gradually increase or decrease the screen temperature
transition=1

; Set the screen brightness. Default is 1.0
; brightness=0.9
; It is also possible to use different settings for day and night since version 1.8.
; brightness-day=0.7
; brightness-night=0.4
; Set the screen gamma (for all colors, or each color channel individually)
; gamma=0.9
; gamma=0.8:0.7:0.8
; This can also be set individually for day and night since
; version 1.10.
; gamma-day=0.8:0.7:0.8
; gamma-night=0.6

; Set the location-provider: 'geoclue', 'gnome-clock', 'manual'
; type 'redshift -l list' to see possible values
; The location provider settings are in a different section.
location-provider=geoclue2

; Configuration of the location-provider:
; type 'redshift -l PROVIDER:help' to see the settings
; e.g. 'redshift -l manual:help'
; [manual]
; lat=
; lon=

; Set the adjustment-method: 'randr', 'vidmode'
; type 'redshift -m list' to see all possible values
; 'randr' is the preferred method, 'vidmode' is an older API
; but works in some cases when 'randr' does not.
; The adjustment method settings are in a different section.
adjustment-method=randr

; Configuration of the adjustment-method
; type 'redshift -m METHOD:help' to see the settings
; ex: 'redshift -m randr:help'
; In this example, randr is configured to adjust screen 1.
; Note that the numbering starts from 0, so this is actually the second screen.
[randr]
screen=0

```

---

### Post by Dennis N on 2019-11-16
> i will do that manualy but i still prefer automatic if it is possible 

Latitude and Longitude should be updated at startup by location services so that Night Light works correctly. Location services could be set to OFF. Check:
**Settings > Privacy > Location Services**
and be sure Location Services is set to ON.

---

### Post by ronjjjg8885 on 2019-11-17
ok
thank you for helping

---

