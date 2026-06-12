---
title: "[SOLVED] No system sound, normal sound works fine"
date: 2007-10-21
forum: General Help
---

### Post by luisjorge on 2007-10-21
Hello everyone!

I just upgraded from Feisty to Gutsy yesterday, and the network upgrade was a nightmare. Deciaded to make a clean, fresh install of Gutsy and everything worked perfectly, except for the system sounds (meaning logout music, "click" sounds, when checking a box or selecting something, etc). Everything else works fine, I can hear music through amarok, play movies with sound, same thing with games, and I checked that the system sounds are enabled under the sound management tool. I can even hear the preview of the sound assigned to a specific event, but when that event happens, no sound. The only sound that really works is the startup sound, but the Login Screen sound before that doesn't, instead I get the horrendous "system beep" to type in my username and password.

Is there any solution to this? I already tried many solutions, from re-enabling my sound card (onboard Intel HD) to compiling and installing new Alsa drivers.

Thanks in advance!

Luis Jorge.

---

### Post by luisjorge on 2007-10-24
I would greatly appreciate any help. Does anyone know something about this?

Thanks!

---

### Post by unebaguettesvp on 2007-10-24
i just posted about something similar here:

[http://ubuntuforums.org/showthread.php?t=588708]("http://ubuntuforums.org/showthread.php?t=588708")

do a:

ls /dev/*dsp*

and if /dev/dsp doesn't show up then that might be a problem. i don't know for sure but that was my problem. i submitted a bug about it here:

[https://bugs.launchpad.net/ubuntu/+bug/121433]("https://bugs.launchpad.net/ubuntu/+bug/121433")

---

### Post by luisjorge on 2007-11-10
Hi! I'm really sorry for taking so long to reply. I tried that, but everything seems fine. The outcome is:

/dev/adsp  /dev/dsp


Any ideas?

Thanks in advance, and sorry once again!

Luis Jorge.

---

### Post by FuturePilot on 2007-11-10
If it's only the system sounds that are not working and your are using Gutsy than this is normal. They removed the ESD sound server which is what the system sounds were pipped through.

---

### Post by rfrey74 on 2007-11-11
I don't think that is the problem.  I have a desktop and a laptop that I upgraded via the net from Feisty to Gutsy.  The desktop plays all system sounds just fine, but the laptop only plays the drum roll when my login screen appears on boot up, and the log in music.  Once I'm logged in, I get no system sounds at all.  For me, ls /dev/*dsp* results in

/dev/dsp   /dev/adsp

with a black background and a yellow foreground.  If I had no system sounds at all, then I would buy the no ESD explanation, but the fact that my desktop has full system sounds and my laptop has partial system sounds seems to be at odds with the no ESD theory.  If anyone knows how to fix the no system sounds syndrome under Gutsy, please enlighten us.

---

### Post by luisjorge on 2007-11-13
Hi everyone! Well, it turns out my problem was indeed with the ESD. I just did

sudo apt-get install esound

and after rebooting, I had system sounds fully working! Thanks to everyone for your help, I hope this solution helps others as well.

Thanks!

Luis Jorge.

---

### Post by macabro22 on 2007-11-14
Cool. AfterInstalling esounds I get sounds when I click but I still can't get sounds when the panel menus unfold and refold.

---

### Post by Derspankster on 2007-11-14
Both my desktop and laptop only play login sounds. I get no other system sounds. Haven't figured this one out yet myself but it's no too irritating.

---

### Post by rfrey74 on 2007-11-24
Sweet, I guess it was lack of ESD.  I stand corrected.  I guess there was a fluke in the upgrade to Gutsy on my desktop that allowed esound to remian installed.  Anyway, I have system sounds on my lappy now.

---

