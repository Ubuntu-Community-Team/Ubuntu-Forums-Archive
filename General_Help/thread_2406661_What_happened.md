---
title: "What happened???"
date: 2018-11-23
forum: General Help
---

### Post by l6griffin on 2018-11-23
I left my computer for a bit, came back signed in and the resolution had changed. I usually run 1920x1080 (recommended) on both monitors. It is now set for 1024x768. and I can't change it. If I go to 'Activities'  type in Display and hit enter nothing comes up. I do have the settings icon on the launcher when that is brought up go to Devices, Displays it has defaulted to an RTK 46" for the second monitor I no idea where that came from. My second monitor is a Viewsonic 26". When I left the computer I had been using Firefox and Thunderbird the resolution was 1920x1080. What corrupted the system?

Larry

---

### Post by oldrocker99 on 2018-11-23
That's a new one on me. Try logging out and logging back in again.

---

### Post by l6griffin on 2018-11-23
I'll go along with that. I'm thinking some profile file is corrupted how and why I have no idea. I did try and reboot with out any good results.

---

### Post by ajgreeny on 2018-11-24
Might be useful to know more about your hardware, particularly the graphic card.

Do you have unattended upgrades enabled and has a graphics package been upgraded recently?
Check this with command ```
grep -i " upgrade " /var/log/dpkg.log.1 /var/log/dpkg.log
``` which will list all recently upgraded packages and may give you a clue.

---

### Post by HermanAB on 2018-11-24
Note that the screens have a little processor inside and the PC communicates with the one in the screen over a serial port.  This happens when you log in, or when you plug a screen in.

Therefore the advice above to log out and in again.  Alternatively, you can unplug and replug the screen or turn the screen off/on, which are less disru[tive to what you are doing at the moment.  Any method that will force the computer to communicate with the screen and get the configuration data should bring things back to normal again.

---

### Post by l6griffin on 2018-11-24
First the hardware, it is a Dell Precision 3530 laptop, sorry can't find the video card in settings anymore. The laptop originally had 16.04 LTS installed I upgraded that to 18.04 LTS.
 The dpkg.log is fairly large and I don't remember how to paste as a URL. In any case HermanAB was right disconnect the external monitor. Plug and Play strikes again. ;)  When plugged back in recognized as the Viewsonic that it is.

---

