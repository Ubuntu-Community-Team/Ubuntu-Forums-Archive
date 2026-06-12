---
title: "grub not finding kernel, kernel is in right location"
date: 2013-06-15
forum: General Help
---

### Post by chkneater on 2013-06-15
My grub files point to the kernel being in the boot menu which they are, however when GRUB is started the grub comes up properly but if you select any of the OS options it says it can't find the kernel, then it runs the ramdisk command and lets you choose to edit the grub or try the command line. The kernel is located where the grub says it should be. What is wrong?

---

### Post by ahallubuntu on 2013-06-15
~

---

### Post by chkneater on 2013-06-15
Essentially this was a fresh install of 10.04 that I reformatted with Gparted with another Live Cd.  When I installed the Grub began running its processes, the screen shows and I pick the only partition, then it says its loading vmlinusblahblah, just like the grub.cfg says it should, then it says it can't find the kernel in the location it's supposed to be, but lo and behold it's fricking there, so I don't know if there is a problem with the or install, however I noticed there were no config maps in the grub file.   

Anyway, I decided to install AV Linux 5.0 on another partition, which it has, but I check the grub file again, and there is a system map in there now?!

Could that have been the problem, no system map?  I'd let you know if it were running but I'm downloading another ubuntu to try out while on live cd right now.

---

### Post by ahallubuntu on 2013-06-15
~

---

### Post by chkneater on 2013-06-15
I used Gparted with a LiveCD (since there is no operating system on the HDD) and formatted it blank, nothing left on it.  From there, using a the 10.04 install CD (not LiveCD) I installed it. On reboot after install, the grub couldn't find the kernel claiming it wasn't in the /boot file.  Using the live cd, i checked the Grub file on the HDD and kernel file was indeed there.  

Now the thing about the maps: there is usually a system map in the grub file, the list wasn't in the installed Ubuntu system until AFTER I decided to install AV Linux 5, thus creating a new grub I assume, and now there IS  a system map file in the grub.

I would reboot now and see if my system is working but I'm on a Live Cd and I'm downloading another version of Ubuntu right now and it has 23 mins. left.  So in approx. 30 mins. I'll let you know if the problem was fixed by that or not.

Oh, and I phrased it wrong, I meant "When I installed, the Grub began running ..."  I went back and reread it and saw it was written confusingly.

---

### Post by ahallubuntu on 2013-06-16
~

---

### Post by chkneater on 2013-06-16
.

---

### Post by chkneater on 2013-06-16
I wiped the drive completely, no partiotions, nothing.  Then I added the primary partition as ext4 and a swap partition, I set the boot flag for the primary.  I'm aware that the install cd's do this for you, but I've had bad experiences letting the installer doing the partitioning.  As far as why I wanted 10.04 even tho it's not supported, it's a damn good program and better than 12.04.  Also, the bugs are pretty much worked out with it in most respects. If I can get one OS to run THEN I may try another one like 12.04.

Thanks for the chroot method link.  This way I can I can run update-grub from the actual filesystem while using the livecd.I still don't know if that will fix the problem however.

---

### Post by Bashing-om on 2013-06-16
[COLOR=#000000]chkneater; Hi !

I hate to see you struggle so. I agree, seems grub did not install properly>
See therse tutorilas on how to deal with grub:
[/COLOR][http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
It may be as simple as booting into the install on the one kernel that boots up and  running terminal code:
```
 sudo update-grub
```

Any questions, please ask. We are here to help.[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by ahallubuntu on 2013-06-17
~

---

### Post by chkneater on 2013-06-17
I have a copy of 12.04, but I don't know if it is a bad burn or not because I can't get any of my other previously usable disks to fully install correctly.


The thing is, I've done many installs, and I know if I've done it right or not, but the problem ALWAYS comes down to GRUB not finding files, or Grub crashing and ending up in rescue mode usually (which it is not really a rescue mode, I have no idea why they would call something with so few commands that are totally useless rescuing?) 

Grub will say sometimes it can't finda  file that should be in a certain folder, go there and look and of course it's there.  Grub just doesn't load filesystems for some reason.

Very cool, I was able to get AVLinux 5 to install!!  I'm not sure, but i think that the problem was something to do with externallHDD not mounting or loading unless you physically turn off or unplug the ExtHDD and plug it back in during POST.  So when I finished the instal, when it asked if I wanted to reboot I chose no and shutdown from there.  Then I unplugged the ExtHdd just after I turned on the comp. and sure enough Grub loaded perfectly and the filesystem is working great.  Might try a dual install but not at the moment, since I love AV!!   Anyways thanks for your help, I appreciate it!!

---

