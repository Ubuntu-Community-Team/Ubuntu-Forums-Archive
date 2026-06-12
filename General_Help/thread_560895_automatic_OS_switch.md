---
title: "automatic OS switch"
date: 2007-09-26
forum: General Help
---

### Post by prow on 2007-09-26
First i must explain my setup before i say what i need for I dont think it can be done but would be nice.

My setup:

Ubuntu / Windows xp Dual Boot
Grub Bootloader
Maxtor Hard drive that only works on windows (please dont argue with me about this, it works ONLY with windows!!!)
Maxtor Backup software
Scheduled backup of personal data on Sundays at 1:00 AM every week

What i need to do:

Usually i am logged into the Ubuntu installation all the time.  Every Saturday night I would like the computer to restart and boot up into my windows installation to be ready for the Maxtor Backup Software to run its backup script

Things to keep in mind:

The maxtor hard drive i have will not mount in linux....will NOT!!!!
Must restart the machine and tell grub to boot windows all while I sleep soundly, knowing my valuable information in backing up properly
If this can not be done at all please let me know..

---

### Post by amadeus266 on 2007-09-27
I can tell you what you need to do but not how to do it. You need to edit the gub menu to make windows the primary (first) option and then figure out how to cause your computer to reboot at a specified time. I did this with suse 10.0 and windows xp using lilo. But that was a while ago and I don't take good notes.

---

### Post by zvacet on 2007-09-27
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS")

---

### Post by prow on 2007-09-27
ok so now that i have windows as the default operation system, how can i tell ubuntu to restart at 12:00am on Sunday morning every week?

---

### Post by bimmerd00d on 2007-09-27
This makes life easier.

[http://web.telia.com/~u88005282/sum/downloads.html](http://web.telia.com/~u88005282/sum/downloads.html)

thread regarding this

[http://ubuntuforums.org/showthread.php?t=295524](http://ubuntuforums.org/showthread.php?t=295524)

---

