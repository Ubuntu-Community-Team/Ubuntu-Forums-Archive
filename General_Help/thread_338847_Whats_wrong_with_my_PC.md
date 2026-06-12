---
title: "Whats wrong with my PC?"
date: 2007-01-15
forum: General Help
---

### Post by SishGupta on 2007-01-15
OK, so im freakin out here trying to figure out what is wrong with my computer.

It started earlier today, i booted out of windows and into ubuntu, which are located on the same drive, but separate partitions.

Ubuntu appeared to freeze during the boot splash after about 2.5 little segments. I restarted and attempted to boot back into windows, again frozen during boot. I didnt wait long for either of these boots.
I try the ubuntu live cd and it boots eventually but its MASSIVELY slow. It takes over 5 minutes to boot the live cd. It never takes this long. 

My stuff is backed up, so i say what the hell and i decide to reformat. The ubuntu installer stalls at 15% which is something about listing partitions, i wait maybe 5 minutes and give up.
I open gparted and it trys to list the partitions when it starts up and everything is greyed out, the parititons never list after 5 minutes.

So now im a little irked. I can't even reformat. My last resort isn't very resort-like.

I try booting ubuntu again, and it stops at the 2.5 segment again but this time i wait 5 minutes. Ubuntu boots! once booted it works, and it works well.
Hard drives are fully accessible, so is my thumbdrive, net works, beryl works.
When i boot ubuntu in recovery mode, i get these two lines:
```

ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.

```
I am unaware if these lines are relevant to my situation. A google search pulls up a multitude of results with these lines, and each situation differs. Some logs get these 2 lines yet their system seems to have a different error.


So now i try booting windows. It locks up. I try it in safemode and windows stops at alim1541.sys. If i just sit there for 5 minutes or so, windows loads, but with varying degrees of success. The first time i booted win with my problem everything seemed OK, the next time everything seemed to be amazingly slow.


In order to troubleshoot i ran memtest86+. The test ran for an hour and a half before i quit it. I got 1 pass and no errors. Memory seems ok.

I booted the live CD w/o hard drives, everything is the same.
I have also been getting the messages:
```

sda: assuming drive cache: write through
Buffer I/O error on device sda, block 0

```
What is SDA in this case? normally it is my thumbdrive but right now, it isnt even plugged in....
Is this message even relevant to my situation?


To the best that I can tell this isn't a hard drive problem.
I doubt its a memory problem.
It doesnt seem to be a gfx problem as i can see desktops and 3d worked in beryl.


Is this a mobo problem? the ali15x3 messages above likely correspond to my mobo chipset which is ali1543...but i have no issue with my BIOS or POST or even grub.

Please help me!


edit: i also tried the windows xp setup to reformat but the installer doesn't get past loading drivers.

---

### Post by ~LoKe on 2007-01-15
SDA is generally your sata hard drive, but not the problem in this case since you said you tried without it.

Perhaps your SATA controller?  Not sure if it'll try to load without anything attached, though.

---

### Post by SishGupta on 2007-01-15
Sorry i forgot to mention that all drives are PATA. This mobo doesnt even support SATA.

I just ran gparted on my HD install of ubuntu and it doesnt recognize my ntfs partition. It just shows one large hda1 partition, hda2 (ext), and hda5 (swap). It shows hda1 of its correct size however, which is that it is minus the ntfs partition.

The good news is that it lists the partitions, albeit some.

---

### Post by peabody on 2007-01-15
You have a hardware problem for sure.  I hate to say it, but everything is likely to be speculation without trying your hardware out on another computer.  I honestly think your harddrive has a problem.  The only way you're likely to know for sure is to take your hard drive and put it in a friend's machine.  If that works fine, try installing on a brand new hard drive (I know you're probably not made of money, lie, cheat, steal or beg yourself a hard drive from someone you know).  If that doesn't work, it's likely your RAM or something on your motherboard.

Hardware failure's a b****.

---

### Post by SishGupta on 2007-01-15
Well heres hoping its the mobo thats shite cuz i already have a new replacement.
I'm just waiting for the fan for my core2duo.

The problem with testing hardware out on another computer is that i don't have one readily available.

Since im replacing the cpu and mobo, if the problem still persists after i get the fan I'll know its the HD, the ram, or the gpu.

oh well, ill be back in 2 days (hopefully). Until then if anyone has any ideas let me know.

thanks
-sish

---

