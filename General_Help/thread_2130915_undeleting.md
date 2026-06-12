---
title: "undeleting"
date: 2013-03-30
forum: General Help
---

### Post by kamman3 on 2013-03-30
Hello All,

           So my buddy tell's me about this awesome operating system (Ubuntu) and i thought cool i'll jsut create a partition back up my 100 gigs of pics and music and other stuff and install the operating system... so long story short i lost everything installing the operating system wiped my hard drive and the backup partition does anyone know how i can reverse this? my Fiancée is about to rip my head off if i don't. Upgraded from winblows 7

Let me know.
Thank's a lot 

Kam :)

---

### Post by 3rdalbum on 2013-03-31
Shut down Ubuntu and DO NOT boot from the hard disk or save anything to disk again until after recovering your files.

Boot the Ubuntu CD and use Software Center to install the Photorec utility.

Hit Control-Alt-T to open a terminal and run this command:

sudo photorec

Insert a USB hard disk, it will be mounted in the filesystem under the path /media/Ubuntu

Use Photorec to recover the files from your hard disk and put them onto the USB hard disk.

You really need to be less gung-ho about installing a new OS - it seems you may have chosen the "erase entire disk" option. Also, even though partitioning is supposedly non-destructive these days, you should always back up to a different disk before modifying the partition layout of your disk. Backing up is tedious, losing irreplaceable data is a hundred times worse.

---

