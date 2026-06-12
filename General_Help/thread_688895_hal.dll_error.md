---
title: "hal.dll error"
date: 2008-02-05
forum: General Help
---

### Post by nosushi4you on 2008-02-05
Yesterday I installed Wubi without a hitch. But then I uninstalled it so I could reinstall it with more space on my hard drive. Now when I try to boot up my Wubi, it says I'm missing my hal.dll file. I checked, and it's there. I tried this solution:[http://ubuntuforums.org/showthread.php?t=466234&highlight=hal.dll](http://ubuntuforums.org/showthread.php?t=466234&highlight=hal.dll)
but that didn't work either. I completely formated my hard drive and reinstalled windows, but still no good. What can I do?

---

### Post by ago on 2008-02-06
That might be beacuse of a hard reboot.
Try booting using a windows CD or recovery CD, go into the recovery console and type 

chkdsk /r

---

### Post by nosushi4you on 2008-02-06
Alright, thanks very much, I'll try that. Also, I should mention that Windows boots fine.

---

### Post by ago on 2008-02-06
Sorry I misread, I thought you couldn't load Windows,

Look for wubildr and wubildr.mbt under C:\ if the are not there they should be in /ubuntu/winboot, copy them over to C:\ (or whatever is your boot drive). Corrupted filesystem requiring chkdsk /r might also have similar symptoms though.

---

### Post by nosushi4you on 2008-02-06
So this might just have to do with the file locations? I hope that's it. Thanks, I'll check and get back to you.

---

### Post by Wesley on 2008-02-06
just let you guys know. 

i had problem wtih networking in ubuntu 8.04, came up with error message with connect a remote computers. 

so i binned wubi 8.04 and installed wubi 7.04 from wubi website. when installing completeled. i upgraded to 7.10 via update manager. 

after the first reboot. had a HALL.dll error message on ubuntu desktop, frozen! had to hard reboot. 

it wouldnt boot up XP, wouldnt go far to dual boot menu, its kept reboot itself all the time. i feared that i lost XP partition. 

so i booted up with XP CD and went in recovery console, did chkdsk r/

it worked!!! phew!!!! :)

---

### Post by nosushi4you on 2008-02-06
> **Wesley said:**
> just let you guys know. 

i had problem wtih networking in ubuntu 8.04, came up with error message with connect a remote computers. 

so i binned wubi 8.04 and installed wubi 7.04 from wubi website. when installing completeled. i upgraded to 7.10 via update manager. 

after the first reboot. had a HALL.dll error message on ubuntu desktop, frozen! had to hard reboot. 

it wouldnt boot up XP, wouldnt go far to dual boot menu, its kept reboot itself all the time. i feared that i lost XP partition. 

so i booted up with XP CD and went in recovery console, did chkdsk r/

it worked!!! phew!!!! :)
Congrats on figuring it out. My computer is very strange. I decided to throw caution to the wind and re-install windows for the the second time, hoping maybe this time my problem would be solved. Guess what? It worked perfectly! I don't know what I did, but it's a big relief. Thanks for all the help:)

---

### Post by wcorder on 2008-08-27
> **ago said:**
> Sorry I misread, I thought you couldn't load Windows,

Look for wubildr and wubildr.mbt under C:\ if the are not there they should be in /ubuntu/winboot, copy them over to C:\ (or whatever is your boot drive). Corrupted filesystem requiring chkdsk /r might also have similar symptoms though.

Thank you, worked like a charm.

---

