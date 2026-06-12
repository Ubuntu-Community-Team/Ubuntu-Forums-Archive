---
title: "How to find cause of crashes"
date: 2012-11-12
forum: General Help
---

### Post by gorellana09 on 2012-11-12
Hello folks. Hopefully someone here can help me. I have been putting up with this problem since the release of Ubuntu 12.04 and since then I have been stuck on Xubuntu 11.10 and unable to upgrade any further. Seeing how 11.10 will no longer be supported after April I really need to find a fix. 

My problem is that Ubuntu 12.04 and newer (and any distro based on the same), crashes my computer randomly. Sometimes it just freezes (keyboard and mouse also become non-responsive) and the only way out is to do a hard reboot with the power switch. Other times the computer will reboot on its own. 

Logically I thought of several culprits, overheating, bad gpu, bad hard drive. However I have narrowed the problem down to the Kernel version. 

The only way I have figured out to reproduce the problem without fail is by launching up a game I sometimes play called Second Life. The game itself does not cause a crash however teleporting to un ancached location does. Let me explain. This game will save on your hard drive textures and game data from each location within the game. If I stay on the same location no crashes occur. The crashes occur only if I go to a new location and the computer starts pulling and saving data to my hard drive. Because of this I thought ok, it must be the GPU or my hard drive. 

**But here is how I have ruled these out:**

The GPU - If I boot on Windows vista no crashes occur and I cannot reproduce. If I boot on Ubuntu/Xubuntu 11.10 no crashes occur and I cannot reproduce

The Hard drive - My hard drive was bad so I replaced it. It is now a brand new hard drive.

**How I narrowed it down to the Kernel Version:**

I noticed that Xubuntu/Ubuntu 11.10 did not crash. Ubuntu/Xubuntu 12.04 (and linux mint 13) do crash.

I tested on a fresh install of Xubuntu 11.10 wich comes with Kernel 3.0.0-12-generic. No crashes occur with this fresh install. However as soon as I apply an update (update manager asks to update to kernel 3.0.0-23 or something) the crashes start happening. 

So I have been stuck on Xubuntu/Ubuntu 11.10 and Linux Mint 12 not being able to even apply updates to the kernels, I have to use Kernel 3.0.0-12 so that I don't have a problem.

I have checked dmesg but I cannot ever see any error messages that could have caused a crash. 

I am sorry if this post is so long but I am trying to be as detailed as possible to illustrate the problem. Please note that it is not specific to the Second Life game. Second Life is the only way I can surely reproduce a crash however this happens randomly also when doing other things. 

**tl;dr** I cannot update to any ubuntu version that uses anything newer than kernel 3.0.0-12. 

Any help would be greatly appreciated.

---

### Post by ercherramon on 2012-11-12
usually when installing a much newer kernel that supports the version of the distribution must also update some repositories that host controllers that adapt to the kernel. so, sometimes you get kernel panic or crash.

---

### Post by gorellana09 on 2012-11-12
Thanks for the reply ercherramon. The thing is these crashes will occur with a brand new install of Ubuntu 12.04 or 12.10, Linux Mint 13, etc. So it is not an update issue.

---

### Post by wojox on 2012-11-12
Have you tried anything outside the Ubuntu family like Fedora, OpenSuse, or Arch out of curiosity ?

---

### Post by gorellana09 on 2012-11-12
Hello wojox, thanks for the reply. No I have not tried any of them because I am new to Linux (almost 2 years but still a newb) and I am afraid that without the Ubuntu type installer I would be lost so I am afraid really. I am currently triple booting Windows Vista, Xubuntu 11.10 (which is my primary use) and Ubuntu 12.10 ( a partition I keep for testing distros), but never anything outside of the Ubuntu family.

---

### Post by wojox on 2012-11-12
Well you got it down to the kernel versions which is awesome. That helps narrow it down. 
What Graphics card/chip do you run?

---

### Post by gorellana09 on 2012-11-12
Graphics chip is ATI Radeon HD3200. I know it is no longer supported.

---

### Post by gorellana09 on 2012-11-13
Hello wojox. I was thinking about your earlier question about trying a distro outside of the Ubuntu family and got to thinking I should probably try it. I looked at Fedora and also openSuse and I think I would like to try Opensuse Gnome because it looks like something that I could get used to. 

I have been doing some research about the installing and all but I would like some advice. I found this thread: [http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/451068-install-opensuse-11-3-over-ubuntu-10-04-dualboot-setup.html](http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/451068-install-opensuse-11-3-over-ubuntu-10-04-dualboot-setup.html)

which walks through installing opensuse over an existing Ubuntu installation. However my setup is a bit more complicated than that.

Currently I have: Windows Vista, Xubuntu 11.10 (my primary os), and Ubuntu 12.10

I believe that Xubuntu 11.10 is handling the grub part. I would like to install Opensuse over the Ubuntu 12.10 install and keep Xubuntu 11.10 as my primary os. 

All threads I find on google suggest that I will have problems after installing opensuse because the Grub2 will fail to see Xubuntu. So my question is, if I follow the instructions on the above link for installing opensuse over ubuntu, what problems can I expect when I reboot and what can I do to avoid them?

I still do want to find a solution to my crashes as I would love to update to Xubuntu 12.04 LTS at the very least but 12.10 prefered. Any help would be greatly appreciated.

EDIT: I should add my fdisk -l output (sorry code option is not available on edit) Also note sda6 is where I want to install opensuse.

geo@geo-Xubuntu:~$ sudo fdisk -l
[sudo] password for geo: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000688ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   409602047   204800000    7  HPFS/NTFS/exFAT
/dev/sda2       409602048   429510655     9954304    7  HPFS/NTFS/exFAT
/dev/sda3       429512702   976773119   273630209    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       429512704   695752703   133120000   83  Linux
/dev/sda6       695754752   961994986   133120117+  83  Linux
/dev/sda7       961996800   969385983     3694592   82  Linux swap / Solaris
/dev/sda8       969388032   976773119     3692544   82  Linux swap / Solaris

---

### Post by quentinl on 2012-11-13
the hardrive may need to be reformatted because it's default may have been set up for a different configuration

---

### Post by gorellana09 on 2012-11-13
Hello quentinl, thanks for the reply. What exactly do you mean?

---

### Post by gorellana09 on 2013-07-13
I'd like to update this thread. My suspicions were correct in the Kernel being the culprit. I have now after some months installed Mint 15 which comes with Kernel 3.8 and the crashes are no longer present. So whatever was causing problems for me between kernel 3.0 and 3.8 has been fixed. I am so happy to finally be able to use the latest, being stuck on the now no longer supported Xubuntu 11.10 was no fun at all.

---

