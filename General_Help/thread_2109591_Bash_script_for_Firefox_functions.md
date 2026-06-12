---
title: "Bash script for Firefox functions"
date: 2013-01-28
forum: General Help
---

### Post by rodmiles on 2013-01-28
Hi All,

New to the Ubuntu OS (12 months in) and trying to setup a machine with some bash files and shell scripts to take care of some functions we need to make it useable as a bit of a kiosk machine in a certain Australian betting establishment.

Basically the machine is logged in as a restricted user, firefox automatically starts up (startup application with website as homepage) in fullscreen and is directed to the website. I already have a bash file in place that auto opens Firefox if it gets closed. Ultimately I would like to add more lines of code to make Firefox maximised if it it minimised by someone etc etc.

I know there are add-ons for kiosk style machines but they are somewhat lacking in functionality and I would like to make it pretty robust and configure the bash file so every eventuality will be covered.

Thanks in advance for your help....

Rod

---

### Post by stinkeye on 2013-01-28
wmctrl may be useful for a few things
eg 
```
wmctrl -r firefox -b add,fullscreen
```

---

### Post by rodmiles on 2013-02-04
Oh good, well thank you for that...I was aware of wmctrl but unaware of the level of control it has over everything. I'm still learning through trial and error all the while trying not to bother the Linux guru at work too much with my "homework".

The code I am running on start up for Firefox is as follows:

#!/bin/sh

# Checks if Firefox is running and starts it if it has been closed

CHECKPOINT=2  # seconds

while [ true ]
do
  echo -n "`date +%r` Firefox is "
  if [ -z "`pidof firefox`" ]
  then
    echo "not running! Starting Firefox now."
    firefox &
  else
    echo "running. Checking in $CHECKPOINT seconds."
  fi
  sleep $CHECKPOINT
done

I am hoping that someone could tell me how I can incorporate the following operations into this code to get the desired result?

[LIST]
[*]Startup Firefox in fullscreen showing only the Back, Forward, Reload and Home buttons.
[*]Do not allow Firefox to be closed or minimised.
[*]Hide the Minimise, Restore and Close buttons if possible.
[*]Restart Firefox if it is closed (already the basis of the code above)
[/LIST]
Thank you in advance to anyone who might have the time and the inclination to help out with some code :)

---

### Post by zombifier25 on 2013-02-04
> **rodmiles said:**
> Oh good, well thank you for that...I was aware of wmctrl but unaware of the level of control it has over everything. I'm still learning through trial and error all the while trying not to bother the Linux guru at work too much with my "homework".

The code I am running on start up for Firefox is as follows:

#!/bin/sh

# Checks if Firefox is running and starts it if it has been closed

CHECKPOINT=2  # seconds

while [ true ]
do
  echo -n "`date +%r` Firefox is "
  if [ -z "`pidof firefox`" ]
  then
    echo "not running! Starting Firefox now."
    firefox &
  else
    echo "running. Checking in $CHECKPOINT seconds."
  fi
  sleep $CHECKPOINT
done

I am hoping that someone could tell me how I can incorporate the following operations into this code to get the desired result?

[LIST]
[*]Startup Firefox in fullscreen showing only the Back, Forward, Reload and Home buttons.
[*]Do not allow Firefox to be closed or minimised.
[*]Hide the Minimise, Restore and Close buttons if possible.
[*]Restart Firefox if it is closed (already the basis of the code above)
[/LIST]
Thank you in advance to anyone who might have the time and the inclination to help out with some code :)

For the first one, try R-kiosk: [https://addons.mozilla.org/vi/firefox/addon/r-kiosk/?src=search](https://addons.mozilla.org/vi/firefox/addon/r-kiosk/?src=search) (haven't tested it)
For the 2nd and 3rd one, do not launch any WM. Since you're only allowing the user to launch Firefox, create a custom xsession that launches nothing but the script above. Create a file named, for example, firefox.desktop in /usr/share/xsessions:
```
[Desktop Entry]
Encoding=UTF-8
Name=Firefox
Comment=Firefox
Exec=/path/to/script.sh
Icon=
Type=Application
```
You may also want to configure Firefox to be in Private Browsing mode at all times so as to prevent anyone leaving any traces on the computer. Go to Edit > Config > Privacy.

---

### Post by rodmiles on 2013-02-05
Thanks for all the help but I have abandoned the Firefox option and gone to Opera as it seems to have more options available for manipulating it's functions via opera:config, in addition to launch scripts.

Still trying to nail it down so the minimize and maximize buttons are non-operational on top of this code:

#!/bin/bash

rm -rf ~/.opera
cp -rf ./.opera_control ./.opera

opera --kioskmode --kioskwindows --kioskbuttons --kioskresetstation  --nomail --nomaillinks --nosave --nodownload --resetonexit --noexit  --nocontextmenu --nomenu --noprint --nokeys 

The challenge is finding a window of opportunity in between child minding duties ;)

---

