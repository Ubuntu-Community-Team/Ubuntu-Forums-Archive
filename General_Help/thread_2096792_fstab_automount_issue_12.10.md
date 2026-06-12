---
title: "fstab automount issue 12.10"
date: 2012-12-21
forum: General Help
---

### Post by loballn on 2012-12-21
new-ish to ubuntu, so bear with me; a few years ago i setup a home computer with 10.10; i edited fstab to automount drives with UUID; no issues. i did a fresh core install of 12.10. and upgraded from there(unsure if i missed a program casusing this). i just copied my fstab file over from 10.10, and now i receive a message during boot that my internal drive isnt ready to mount and press m or s? the difference from other posts is that my OS drive and swap(8gb flash) mounts, my 2nd drive(2tb) mounts, but the other(3tb) doesnt. 
misc info:
bios updated before 12.10 install
core install is from mini.iso loaded with no updates, command line install, and nothing selected for install from list. 
i am using same computer that has 10.10 running currently; OSs installed on identical flashdrives, just pulling os flashdrive and swapping, so same hdd mounting in 10.10, but not 12.10
not sure if its relevant, but in 12.10 the 2tb drive that automounts seems to have 2 mount points /media/ and $home/ and when i mount the 3tb drive, it mounts correctly under /media/ (maybe a hint?)
i have many issues i'm dealing with, this is only the first.
btw, i made an image of the 12.10 core install before beginning my build, and i will make another of it's current state, so if needed i can go to square 1 easily.

---

### Post by oldfred on 2012-12-21
Welcome to the forums.

may be best to post fstab, UUIDs, & what is mounted. 
Post in code tags to preserve formatting. (# in edit panel).

       sudo blkid -c /dev/null -o list
       
 sudo cat /etc/fstab
mount

---

### Post by loballn on 2012-12-22
Thank you for the quick reply; i will post results when i get home tonight.

---

### Post by loballn on 2012-12-23
well, now i feel ashamed by stupidity. never would have thought the uuid in my backup file was incorrect; i was pondering issues with having gpt on the 3tb drive misread.  as for the double mount points; mount is showing one mount point even though it shows in the $home/  and  /media/. maybe it is standard, a glitch or whatever; unfortunately that was the easy issue. now on to bigger issues.

---

### Post by oldfred on 2012-12-23
Glad you figured it out.

With 2TB & 3TB drives are you into gpt partiting issues? I am using gpt on my 16GB flash, SSD, and a 160GB drive to learn about it.

---

