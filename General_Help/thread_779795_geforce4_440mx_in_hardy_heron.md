---
title: "geforce4 440mx in hardy heron"
date: 2008-05-03
forum: General Help
---

### Post by gsiliceo on 2008-05-03
Hello, using the restricted drivers i get acceleration(direct rendering: yes) and desktop effects but only 800x600.
Manually adding higher resolution to xorg.conf breaks the desktop effects, actually everything works perfectly but the windows decorations disappear.

If i remove the higher resolution from xorg.conf and restart then use the nvidia-settings tool to change resolution from 800x600 to 1024x768 the desktop effects works perfectly decorations and everything.

What can i do to have this last behaviour (high resolution+desktop effects+decorations) in the startup without having to open the nvidia settings?

things i've tried:
envyng, the three drivers
hardy heron restricted drivers

If i just knew the command equivalent to the change resolution gui in nvidia settings app i would issue it using system/preferences/sessions, i've read the manual for the nvidia-settings app and you can change a lot of values using the command line but not resolution. Anyway i attach the values i can change using that apps command line backend(i got that list doing "nvidia-settings --query all > attributes.txt")
So if you see anything that might help there, please let me know.

---

### Post by gsiliceo on 2008-05-03
Got it working, the leasson here is, dont let nvidia-settings save the configuration to xorg.conf, do it manually, i discovered that it was saving a lot of junk and i just copied the settings i wanted: monitor frequency and screen resolution.
This is my sisters computer, she's being using ubuntu since feisty but i couldnt enable the desktop effects until now, she will be very pleased as she love them when she sees them in my box.

---

### Post by thebluestreak on 2008-08-12
would you be able to tell me a little bit about how you did this:

1) what version of nvidia driver did you use
2) did you install using envy
3) what did you modify / delete in xorg.conf

Glad to hear it works.  I have a similar post, so if you are able to respond it would be greatly appreciated.

---

### Post by gsiliceo on 2008-08-13
1) I can't remember, it was the one that originally came with hardy.
2) No, used the package found in the repos.
3) I can't post the specific text i added, the HD in that pc died =(.
I know it was the monitor frequency and screen resolution values. 
All i remember.

---

