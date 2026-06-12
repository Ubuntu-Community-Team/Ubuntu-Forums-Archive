---
title: "[SOLVED] dvd drive randomly unmounts"
date: 2008-05-12
forum: General Help
---

### Post by bryncoles on 2008-05-12
hey people. having an odd problem with hardy. my dvd drive sometimes randomly unmounts itself if i watch a dvd, after about 40 minutes. running sudo mount -a does nothing to bring it back, rebooting into windows (i dual boot with XP) sometimes shows the drive and sometimes doesnt, and checking i can still boot from cd sometimes works and sometimes doesnt. 

this happened a week ago, when i was watching 'the prisoner' on dvd (1960's sci-fi series. cold war paranoia!). i rebooted, and the dvd drive came back, so i was able to finish watching the episode i was watching. yay!

then it happened again last night, while i was watching daywatch (russian vampires). this time, rebooting didnt help at all. so i went to sleep, and upon booting up this morning, my dvd drive is back again. 

im running a packardbell easynote laptop, r4360 i think is the series number. i had a similar dvd issue about a month and a half ago (detailed here [http://ge.ubuntuforums.com/showthread.php?t=740129](http://ge.ubuntuforums.com/showthread.php?t=740129)), where the upshot was we decided the drive was shot, and i got a new one. which worked flawlessly for a month, and now is playing up. 

is hardy eating my dvd drives, or am i just lucky? anyone got any ideas? and do i need to post some more info so people know what im talking about?

any help appreciated ;-)

---

### Post by njparton on 2008-05-12
Can you post your /etc/fstab file please?

---

### Post by bryncoles on 2008-05-12
hi njparton! thanks for replying. here is the fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=81b72f41-fdaf-4bc5-9b40-d7e712e6934e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f82ba6db-46e1-44e3-b07e-b41cdb3e7186 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0



i had read that hardy mounts cd/dvd drives from the kernel, so the last line there might not even be necessary....?

---

### Post by njparton on 2008-05-12
> **bryncoles said:**
> 
i had read that hardy mounts cd/dvd drives from the kernel, so the last line there might not even be necessary....?
 
Well try commenting it out with a # at the start and rebooting to see.
 
If what you say is true then you'll have to fix something then recompile your kernel to fix it!
 
Try commenting it out first to establish whether that fstab entry is used or not.

---

### Post by bryncoles on 2008-05-12
erk! recompiling sounds 'advanced'... im not sure i like the sound of that... 

will get back to you in a moment or two with notes on whether fsatb works all commented out...

it seems this unmounting problem only occurs when im trying to watch dvds though. i can use the drive for other things (its playing music from a dvd now...)

---

### Post by bryncoles on 2008-05-12
ok, i have commented out that line, rebooted and computer///: still see's the dvd drive, and its still playing my music dvd. 

so i guess it works without fstab...

---

### Post by njparton on 2008-05-12
So it sounds like it's a kernel problem then.  I suggest you head over to launchpad and search it for similar issues to see if they're recorded/fixed.  If not you may want to add a new entry so that the issue can be resolved in future versions.

---

### Post by bryncoles on 2008-05-12
ok cool, ill get on it. thank you for your input! 

:-D

---

