---
title: "ubuntu wont boot up"
date: 2012-11-20
forum: General Help
---

### Post by Cesaar on 2012-11-20
I'm stuck on the white dots loading screen forever on ubuntu 12.10. The only strange thing i did before that happened was to sudo apt-get remove  build-essential git-core cmake libssl-dev libx11-dev libxext-dev libxinerama-dev libxcursor-dev libxdamage-dev libxv-dev libxkbfile-dev libasound2-dev libcups2-dev libxml2 libxml2-dev libavutil-dev libavcodec-dev . 
So i went on the recovery mode,to see if there were broken packages to repair. running that option asked me to mount / and others in /etc/fstab in r/w mode. After selecting 'yes', i got the following on the screen:
```
fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
/dev/sda6: Superblock last mount time is in the future.
        (by less than a day, probably due to the hardware clock being incorrectly set). FIXED.
/dev/sda6: Superblock last mount time is in the future.
        (by less than a day, probably due to the hardware clock being incorrectly set). FIXED.
/dev/sda6: Superblock last mount time is in the future.
        (by less than a day, probably due to the hardware clock being incorrectly set). FIXED.
/dev/sda6: 388496/1703936 files (0.3% non-contiguous), 4200184/6811392 blocks
Lizzy: 150936/31309824 files (4.5% non-contiguous), 66185950/125217024 blocks
mountall: fsck /home [1066] terminated with status 1
```

/ is on /dev/sda6
swap on /dev/sda5
/home on /dev/sda3

it also happens when i tell it to fsck, failsafex, etc.

I also happen to have upgraded to 12.10 from 12.04 about 2 weeks ago but had no problems. i'm also dualbooting with win7.

So do you happen to have any suggestions as to how to proceed?

---

### Post by Cesaar on 2012-12-08
Ok, so i went into a root shell to see if i could do something. I ran fsck on / and /home and fsck said that they were clean. So I went back to the recovery mode and tried to fix broken dependencies again. And again, it asked me to mount everything, to which I again conceded, and I got the following output:
```
 fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
/dev/sda6: Superblock last mount time is in the future.
        (by less than a day, probably due to the hardware clock being incorrectly set). FIXED.
/dev/sda6: Superblock last mount time is in the future.
        (by less than a day, probably due to the hardware clock being incorrectly set). FIXED.
/dev/sda6: clean, 388505/1703936 files, 4201956/6811392 blocks
Lizzy: Superblock last mount time is in the future.
        (by less than a day, probably due to the hardware clock being incorrectly set). FIXED.
Lizzy: clean, 151208/31309824 files, 66295045/125217024 blocks
``` But, it was just stuck there, and it didn't do anything. So I got on a new shell and tried to run vim, vi, and others in shell but it gave me the error ```
vim: error while loading shared libraries: libfreetype.so.6: cannot open shared object file: No such file or directory 
``` I'm kind of stumped there since I can't connect to the internet from the shell to try to install missing dependencies. I'm thinking that perhaps with a livecd/usb I can get the missing dependencies and install them since the options in recovery mode aren't working. Would that work, and how should I go about doing it if it would work?

---

### Post by BertN45 on 2012-12-08
Try "sudo apt-get install -f" while you are in the recovery mode.

---

### Post by Cesaar on 2012-12-10
Hi BertN45 I tried your suggestion and I got the usual 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded message, but nothing else. 

I also tried to do an update but it failed to fetch anything because it's not connected to the internet. I tried the network option from the recovery menu and it doesn't do anything just like the dpkg one i mentioned in my previous post.

---

### Post by Cesaar on 2012-12-30
I ended up running the live CD and using chroot to update the system from there. I reinstalled libfreetype and all was good after that.

---

