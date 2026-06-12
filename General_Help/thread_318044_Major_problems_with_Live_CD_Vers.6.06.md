---
title: "Major problems with Live CD Vers.6.06"
date: 2006-12-13
forum: General Help
---

### Post by KMJones1 on 2006-12-13
I am trying out Linux for the first time, so I have used a PCPro mag disk version 6.06 of Ubuntu as a live CD. Loads and unloads fine.
Prob 1. Display is 640x480 and there is no way to change it (normally use 1280x1024). The drop down list only has the one value.
Prob 2. I cannot see the hard disks on the computer, only the removable media drives. I can see the computer on the network and the hard drives on the other machines, but not on the host machine.

Any ideas please?
:(

---

### Post by darco on 2006-12-13
Sounds like the xorg.conf needs a fixin'....try this
[http://www.cyskat.de/dee/progxorg.htm](http://www.cyskat.de/dee/progxorg.htm)
Good luck

dr

---

### Post by hikaricore on 2006-12-13
> **KMJones1 said:**
> I am trying out Linux for the first time, so I have used a PCPro mag disk version 6.06 of Ubuntu as a live CD. Loads and unloads fine.
Prob 1. Display is 640x480 and there is no way to change it (normally use 1280x1024). The drop down list only has the one value.
Prob 2. I cannot see the hard disks on the computer, only the removable media drives. I can see the computer on the network and the hard drives on the other machines, but not on the host machine.

Any ideas please?
:(

1. This could crash your live cd's xserver but...  that's not really as bad as it sounds, and it's worth it if it works.  Go up to your Applications Menu, and choose Accessories / Terminal.  This should open a terminal box on your desktop.  In the box type:

```
sudo dpkg-reconfigure xserver-xorg
```

Now go through the automated process of configuring X, there are quite a few questions but just answer them as best you can or possibly guess.  Finally the configuration will be near complete, it will detect your video chipset and monitor type.  There will be a page asking you to flag useable resolutions, make sure 1280x1024 is one of them that you do flag.  The last two questions will be about your monitor resolution.  When presented with the choice of Simple, Medium, or Advanced.  Choose medium.  Then pick 1280x1024@60hz or whatever your monitor supports (use your basic judgement here) and continue.  The last page will ask you about your colour depth.  If you know your video card and monitor can handle 1280x1024 @ 24bit (aka 32bit in windows) colour, then mark 24.  If you want to be safe, just make it 16bit colour as this will usually work.

Finally the config file will be saved again and you will be back at a prompt in your terminal.  Hit ctrl+alt+backspace.  If you did this correctly, X and GDM will restart in a much better resolution, or if your computer hates you like mine often has you'll just end up having to reboot.  Either way can't hurt to try and you won't damage anything trying.

2.  Do you mean you can't see them in the list?  This is because they are not mounted by linux.  This is normal.  Goto your Preferences / Administration / Gparted  (or Partition Editor) and see if they show up there.  If they do then there is no problem.  The live cd does not automount any partitions on your system by defualt with the exception of a swap partition (i believe) if one is found to be availible.

---

### Post by KMJones1 on 2006-12-14
I have just discovered this: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) which has some useful info. on the HDD prob.

---

