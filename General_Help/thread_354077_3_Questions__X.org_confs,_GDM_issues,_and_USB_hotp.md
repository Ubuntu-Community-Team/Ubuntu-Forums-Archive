---
title: "3 Questions:  X.org confs, GDM issues, and USB hotplug scripts"
date: 2007-02-05
forum: General Help
---

### Post by KyPeN on 2007-02-05
1) I have 2 different x.org scripts that I would like to load as x.org loads. Which one would depend on if the system detects a specific monitor. Can this/How would this be done?

2) I'm having a GDM issue. Every time GDM starts from a reboot/cold boot, it seems to be broken. It will attempt to load (I see the nVidia screen), stalls, tries again, stalls, and loads the default look (and beeps, this is the big problem in class). If I go to tty1 and stop GDM, copy over /etc/gdm/factory-gdm.conf to /etc/gdm/gdm.conf and reload gdm, everything is fine. If I logout and come back, it is fine. If I kill x.org via ctrl+alt+backspace, it is fine. But on a reboot, it is back to broken. Suggestions?

3) I use an M-Audio Transit soundcard which must load the firmware in the device every time it is plugged in. As I understand it, this is normal. I got some software that does this, but not automatically. I was doing it manually, and now I have a little script I wrote that does this, but I must still run this when it is plugged in. Is it possible to do this when the device is plugged in based on a kernel event or something? I've been looking at hotplug, but have yet to find much.

---

### Post by KyPeN on 2007-02-05
I have worked around the GDM thing by just autologging in and apparently both monitors will work on a single xorg.

---

### Post by KyPeN on 2007-02-05
Bump

---

### Post by Aifel on 2007-02-05
you could TRY to set the script to auto-run every time you login, which can be done by going to System-->Preferences--->Sessions, and setting it up from there. As for issue #1, I have no idea.

---

### Post by KyPeN on 2007-02-05
I'm sure that would work, but only if the soundcard is plugged in on login.  It may or may not be.

---

### Post by KyPeN on 2007-02-06
Bump

---

### Post by bodhi.zazen on 2007-02-06
As far as your monitors, you can have more then 1 server section in xorg.conf and select which server to run with the -layout flag.

Take a look at these 3 threads:

[http://www.ubuntuforums.org/showthread.php?t=240150](http://www.ubuntuforums.org/showthread.php?t=240150)

[http://www.ubuntuforums.org/showthread.php?t=271045](http://www.ubuntuforums.org/showthread.php?t=271045)

[http://www.ubuntuforums.org/showthread.php?t=271674](http://www.ubuntuforums.org/showthread.php?t=271674)

That should get you started in the right direction ...

Second piece of advice, IMO it is better to start 3 threads as your subject matter will intertwine with these 3 questions.

As for #2 - can you post /etc/gdm/factory-gdm.conf and /etc/gdm/gdm.conf ?

Also, try booting to the CLI (No gui) and start gdm after a fresh boot. Error messages ?

# 3 ?

---

