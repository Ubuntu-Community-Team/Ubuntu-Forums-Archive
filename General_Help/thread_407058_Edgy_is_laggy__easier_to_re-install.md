---
title: "Edgy is laggy | easier to re-install?"
date: 2007-04-11
forum: General Help
---

### Post by remick182 on 2007-04-11
I have seen a few other posts in here about a laggy OS, and I, too have this problem now.  I have never had it before and this current Edgy is a 2nd one as well.  I have another Edgy installed on another partition with the -11 kernel and it runs fine.  This Edgy is a new one.  I've had it for less than 2 weeks.

I installed the nVidia drivers using Envy and the rest of the essentials using Automatix2.  No problems.  I've upgraded to the -11 kernel and still no probs.  So, somewhere between installing some new programs and updating files (I suspect it was some update) I started getting a laggy OS.  I have some gdesklets on displaying my system specs so I can monitor them.  If I have gedit open, and only gedit, and I move the window over to the side a bit, my CPU usage jumps from 12% to 100% instantly.  My memory usage is stable at 21%.

I've tried to re-install the nVidia drivers using Envy...no change.
I've checked my xorg.conf for any errors, but it's about the same as my other Edgy which has no issues.
I've loaded Failsafe Gnome to cut back on processes running...still slow.
I've removed Beryl, Compiz, some games...can't figure out the problem.

Any suggestions?

---

### Post by CarloMagno on 2007-04-12
I am having the same problem, the system was working smoothly until yesterday when after sudo-ing apt-get dist-upgrade I saw that the new kernel 2.6.17-11-generic was installed. I rebooted the machine and grub stopped loading the system

I checked /boot/grub/menu.lst and saw that the entries to the kernel (both new and old) were wrong (hd(0,6) and hda9 when it should be hd(0,4) and hda7) I solved the problem editing this file in winXP (hd(0,0)) that curiosly had no problems to load through grub.

Well, I replaced the entries for the good ones and got it starting. To my surprise, it took really looooong to start gnome and whenever I start a program it takes ages to appear in the screen. Even pushing the shut-down button doesn't work.. or I don't have enough patience to wait more than 3 mins for the shut-down menu to appear, so I have to press CTRL-ALT-Backspace and shut-down from the login menu.

I thought it could be a problem of the new kernel, but if I choose the old one in the grub menu the result is the same, very slow system, for me completely unusable.

I have a generic i386 installation with open-source drivers, those automatically installed by Ubuntu, if that helps. The problem with grub seems to be related with a partition I had previously in my hd that I deleted with PartitionMagic in WinXp (it was NTFS) and in the space it left I created an ext3 partition with Gparted under Ubuntu. Now, whenever I do a kernel update I have to edit menu.lst to be able to boot.. It is as if the installer will look for the description of my Hd partitions in a file created before the Gparted operations and know it has got incorrect information.

Hope someone could help us. When I get home this afternoon I will check boot log and dmesg to see if there is some kind of error.

---

### Post by CarloMagno on 2007-04-12
I will answer my problem with grub loader. It seems the forums are pagued with similar experiences and that the solution is misunderstanding the information in grub.lst
What shocked me more is that it seems there are some lines commented in the file (with #) in the begining that contain information used to rewrite the file (groot) and the manual additions to the file must be written in the correct place if we want them to persist after a kernel update:

[http://ubuntuforums.org/showthread.php?t=407419&highlight=kernel+2.6.17-11+problem](http://ubuntuforums.org/showthread.php?t=407419&highlight=kernel+2.6.17-11+problem)

---

### Post by remick182 on 2007-04-12
The reason that I don't think this is a kernel issue is because I have another Edgy OS running -11 and it is fine.  I have different apps on it, so it has to be something else...I'll keep troubleshooting if I get a chance this weekend.

---

### Post by CarloMagno on 2007-04-13
An update on the problem. It seems the problem is solved... I restarted the system again everything was slow. I edited the file /boot/grub/menu.lst to avoid future problems with kernel updates: I changed In the file, the #groot = (hd0,6) for #groot = (hd0,4).

The problem was that when I installed EDGY, I had a windows partition that afterwards I deleted to give more space to linux... well, during the installation the #groot line was created pointing to the partition where /boot was. After the changes in the structure in my Hard disk, the order in the partitions changed, but this line was not updated in menu.lst so whenever a program automatically modifies it (for example adding a new boot option when a new kernel is installed) it looks for #groot entry to generate the boot options... the result is the system no longer boots. I hope that after changing this line I will no suffer the problem again. Another mistake I made was that, as suggested in some guides, I made a different partition for /boot, so the lines that load the linux kernel are:

root	(hd0,4)
kernel	/vmlinuz-2.6.17-11-generic root=/dev/hda7 ro quiet splash

Note tha the root system points to /dev/hda7 because my root partition (/) is diferent from the boot partition (/boot is /dev/hda5) that is the mistake I had made (so No 'root=/dev/hda5')

Finally, I read in some post that supressing 'quiet' in the loading kernel line will improve speed, so I deleted it and the line is as follows:

root	(hd0,4)
kernel	/vmlinuz-2.6.17-11-generic root=/dev/hda7 ro splash

I think this is the only change that could have solved my speed problem (the quiet option), so I would give it a try if you are having long boot times and slow responsiveness in gnome. I am very new to linux, so my explanation may be wrong, but I Hope this help anyone.

---

