---
title: "[SOLVED] Samba Install Broke My System"
date: 2007-08-09
forum: General Help
---

### Post by moore.bryan on 2007-08-09
*so... i tried installing samba, everything went fine, then i rebooted and my latop (lenovo thinkpad z61e) hangs at a blank line after "checking battery state [ok]".  help?*

---

### Post by GMachine_24 on 2007-08-09
Hi:

HELP! We need more information. How did you install Samba? (P.S. You do not need to reboot your comp, with a few exceptions, after installing or upgrading software as you do in Windows).

Have you removed Samba to see if the problem goes away? That's an easy one.

Are you running off your battery when this happens? Is your battery charged enough to run the computer?

I did a quick search-engine look to see what help might be out there in cyberland - I think if you do that you will probably come up with an answer. Of couse I could do it but that's not what these forums are about.

good luck

gm

---

### Post by moore.bryan on 2007-08-09
*thanks for the response... i'm a little frustrated with this problem, having been working on it since early this morning, so  please excuse me if my responses seem short and/or angry...*> **GMachine_24 said:**
> Hi:
HELP! We need more information. How did you install Samba? (P.S. You do not need to reboot your comp, with a few exceptions, after installing or upgrading software as you do in Windows).
*```
sudo aptitude install samba smbfs
``` as per the ubuntu guide.  i didn't reboot because i installed samba, i was working out a problem with alsa and needed to reboot to see if my settings remained the same.*
> Have you removed Samba to see if the problem goes away? That's an easy one.
*this was the FIRST thing i did...```
sudo aptitude remove --purge samba smbfs
```*
> Are you running off your battery when this happens? Is your battery charged enough to run the computer?
*i'm running off of ac, but i unplugged to see if that was the issue... it wasn't.  battery is fully charged.  i do not believe the battery check is hanging because in rescue mode i can ```
sudo /etc/init.d/acpi-support start
``` and get no errors.*
> I did a quick search-engine look to see what help might be out there in cyberland - I think if you do that you will probably come up with an answer. Of couse I could do it but that's not what these forums are about.
*thanks, but i thought of this one and the "search-engine look" didn't return diddly... that's why i posted here, for help.*

---

### Post by moore.bryan on 2007-08-09
*after much bashing of the head against the wall, my wife reminded me one of my favorite sayings for my students: ockham's razor... "with all things equal, the simplest answer is always correct."  so, i went back to basics.  i ran every script in /etc/init.d which corresponded to a runlevel command by hand and everything worked, all without errors.  baffled, i checked the /etc/event.d folder and noticed something odd... all my tty# files were gone.  i don't know why--or better yet how--but the uninstall of samba saw fit to delete my tty's.  nice.  put them back and everything's a-ok.*

---

### Post by GMachine_24 on 2007-08-09
glad you fixed it. i use occam's razor a lot. simple is usually correct and software is usually  the culprit rather than hardware.

i found a lot of posts concerning the computer hanging after the battery notice; they mostly had to do with video drivers and other things. the old nvidia devil, etc.

i wasn't trying to be a wise guy - i just wasn't sure where to begin. and was trying to knock out the simplest possible problems --- which is why i asked about samba install/reinstall.

i'm having a problem (listed in another of my posts) and i'm pretty sure it has to do with cron/anacron/startup whatever issues..........so far i have been flummoxed. wow. i actually got to use that word. :guitar: 

best of luck.

gm

---

### Post by moore.bryan on 2007-08-09
*no worries... as i said, i was just a little frustrated.  what's your other problem?*

---

