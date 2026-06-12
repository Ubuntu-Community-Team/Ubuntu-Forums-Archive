---
title: "Monuted problems with Hda1 help please"
date: 2007-09-25
forum: General Help
---

### Post by gerath60804 on 2007-09-25
I have a dual boot with WinXp and ubuntu up until today i have had no real issues with it excepte today i notice i had an updates icon so i updated and restarted.  One i restarted the computer did a fsck check and crash at 78% state that unmounted dev/hda1 was busy. the dev/hda1 was no longer mounted and  i could not access it anymore.  I have tried Execute this command: sudo vol_id -u /dev/hda1 and try to make the right chagens in the /etc/fstab i only have read only permission i can't make any chages to it.  Please if someone could help i have tried everything  i could to get the mounted drive back but still it is no longer there.  :confused: I also have tried the commands to mount back the drive but still nothing is there.  please help

---

### Post by Adramelech on 2007-09-25
? thats weird... you cant fschk a munted drive so i suppose its no mounted in first place. 

I have a problem with fschk at boot time, it checks root partition twice, the second fschk fails cause the drive is mounted by the first one and the cause is a bug in the fstab parser, my solution? change the field <pass> (last number in each entry) on fstab to 0, it will disable the fschk chek at boot time. 

oh, if you cant write into the fstab file, try the livecd, mount your parttion and then change the file. Gparted have a CHECK option, so you can run gparted from the livecd and check your partiton.

---

