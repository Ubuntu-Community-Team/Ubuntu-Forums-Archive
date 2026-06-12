---
title: "Cannot write bytes: broken pipe"
date: 2013-08-16
forum: General Help
---

### Post by spencer3 on 2013-08-16
Hello,

I am a first-time Ubuntu user, and just installed Ubuntu from a pre-installed version of Windows 8. I followed said instructions, disabling SecureBoot and such in the BIOS. The installation works fine, and the first boot of Ubuntu without the disk goes perfectly. However, after rebooting, I get a screen that tells me "cannot write bytes: broken pipe". I've reinstalled Ubuntu about two times now, with the same thing happening again. I have tried updating drivers, and updating Ubuntu before the reboot, but nothing seems to work. I ran Boot Repair, and got this output: [http://paste.ubuntu.com/5994456/](http://paste.ubuntu.com/5994456/)

I would greatly appreciate it if someone could help!
~Spencer

---

### Post by Boab1993 on 2013-08-16
[FONT=arial]Hello Spencer,

Have you followed the suggestion at the bottom of boot-repair :

 "[/FONT][FONT=arial]The boot files of [The OS now in use - Ubuntu 12.04.2 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)"[/FONT][FONT=arial][/FONT]

---

### Post by spencer3 on 2013-08-16
I'm unsure of how to do such. I've installed Ubuntu over my old Windows files, so Ubuntu is the only OS. How would I do as it says?

---

### Post by Boab1993 on 2013-08-16
Sadly, if the 'write to bytes' error is the first thing you see, i think you'd need to do another reinstall, and perform the suggestion on the first boot.

If you boot up to a point, please describe which point, as you might be able to access a terminal.

---

### Post by spencer3 on 2013-08-16
So I reinstalled for the fourth time, ran boot repair before doing anything, ran updates. After installing updates I can restart fine, but as soon as I install any of the graphics drivers, the error occurs. I am really lost at this point. What do I do? (I currently am at the point before restarting for the updates)

---

### Post by Boab1993 on 2013-08-16
Right, just for clarification broken pipe errors generally means a file path is broken, missing or has restrictions, so what the error is saying is it can't write the data because it can't access the filepath. Given this appears to be related to graphics drivers my assumption is that something is wrong with filepath of a graphics driver.

So, since once you reboot its back to square one, to make sure we do this in a oner heres all the information i could get on the situation.

[http://ubuntuforums.org/showthread.php?t=2067086](http://ubuntuforums.org/showthread.php?t=2067086)

[http://askubuntu.com/questions/105857/ubuntu-11-10-not-booting-could-not-write-bytes-broken-pipes](http://askubuntu.com/questions/105857/ubuntu-11-10-not-booting-could-not-write-bytes-broken-pipes)

Also remember to try the above suggestion. Visit here for the documentation on boot partitions : [FONT=arial]https://help.ubuntu.com/community/BootPartition[/FONT]

---

