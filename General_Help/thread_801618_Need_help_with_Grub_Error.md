---
title: "Need help with Grub Error"
date: 2008-05-20
forum: General Help
---

### Post by jobyjoe on 2008-05-20
Hi all, I need some help here. I just upgraded to Ubuntu 8.04 from 7.10. I never had any problems with 7.10. But now, after upgrading, I can't even run Ubuntu! I'm dual booting XP and linux, and everytime I start my computer it says 

"GRUB Loading stage1.5Read Error_"

I don't really know what this means. It doesn't give me any specific error number. What do I do now. I'm not too computer savvy, so I really don't know what to do, and I really need to use my computer. Thanks for any help.

---

### Post by anystupidname on 2008-05-20
[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

---

### Post by hrhodes3 on 2008-05-20
I had a similar  error when I tried a version of lime linux .  I think I might have set partitions wrong or something.

---

### Post by jobyjoe on 2008-05-20
Yeah it's just that it worked fine till I upgraded. What is supergrub and what do I do with it?

---

### Post by jobyjoe on 2008-05-20
I'm probably not understanding this right, but do I have to use the supergrub cd every time I boot my computer?

---

### Post by MythosLegend on 2008-05-20
> **jobyjoe said:**
> I'm probably not understanding this right, but do I have to use the supergrub cd every time I boot my computer?

You can download supergrub as an ISO and burn it to a cd. Then you boot from the cd. Hopefully it will solve your problem. 

No. You shouldn't need it everytime you boot.

---

### Post by jobyjoe on 2008-05-21
Ok, I really need help here guys. I can't burn a cd because I can't boot my computer. Can i put the .iso image on a usb drive and try to boot from there?  Also, the file i got was "supergrubdisk_0.9677.iso" is this the correct file? Or did I download the wrong one? thanks for any help

---

### Post by jobyjoe on 2008-05-21
bump

---

### Post by roe_polak on 2008-05-21
Boot the Ubuntu live cd and burn from there.

In fact, when you boot up the live cd you can just repair grub from there. Search the forums on how to reinstall grub.

There you go: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by jobyjoe on 2008-05-21
Thanks for the help, but I have another question. The only Ubuntu cd I have is from when I installed 7.10. I upgraded to 8.04 by using the ubuntu updater. Can I use the 7.10 cd??? or do I have to have the 8.04 cd. Sorry if this is a dumb question.

---

### Post by logos34 on 2008-05-21
> **jobyjoe said:**
> I upgraded to 8.04 by using the ubuntu updater. Can I use the 7.10 cd??? or do I have to have the 8.04 cd.

yep, no prob

---

### Post by jobyjoe on 2008-05-21
Ok, I followed the instructions about using the live cd to go in and change grub. Everything went smooth. I restarted, I get to the grub menu, so I was happy. I try to start Ubuntu, and this message comes up: 

Error 21: Selected disk does not exist

Ok, so now I'm frustrated. So I go back to the grub menu and I try to start XP. This is the message I get: 

NTLDR is missing

I have no idea what to do and/or what is going on. Any help????

---

### Post by logos34 on 2008-05-21
You might want to post your menu.lst and output of sudo fdisk -l

---

### Post by jobyjoe on 2008-05-21
Thanks for your help, and sorry for this, BUT i don't know how to do that. Could you give me some instructions? do I have to use the Live cd again?

---

### Post by strabes on 2008-05-21
> **jobyjoe said:**
> Error 21: Selected disk does not exist

This means you put the wrong disk as your root partition. See the link in my signature for more information on reinstalling grub. See [this link](http://www.gnu.org/software/grub/manual/html_node/Naming-convention.html) for more information about grub partition naming conventions. (hd0,1) Would indicate that the root partition is on the first disk and the first partition. The disk numbers start with 0 and the partition numbers start with 1.

---

### Post by jakupl on 2008-05-21
> **jobyjoe said:**
> Thanks for your help, and sorry for this, BUT i don't know how to do that. Could you give me some instructions? do I have to use the Live cd again?

yes. boot from the live cd, open up the terminal (Applications --> accessories--> terminal.)

and enter

```

sudo fdisk -l 
```
and

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by anystupidname on 2008-05-21
How are you able to post to this forum?!? You obviously have another PC you could burn the supergrub ISO to a CD with... Supergrub makes repairing grub problems extremely easy which is why I had suggested it. We're talking about a simple 10 second fix here. Sorry you're having such difficulty...

---

### Post by jobyjoe on 2008-05-21
Damn, now I can't even run off of the Live cd. It freezes every time it gets to the black screen that says Ubuntu and has the little status bar under it. It just freezes at this point. Any suggestions?

Edit: I have laptop, but it is without a cd burner. That is how I can post.

---

### Post by jobyjoe on 2008-05-21
Ok another update. I was able to go over to my neighbors and burn a copy of supergrub. So I booted the CD, and it sort of worked, but again, it would just freeze when it got to the ubuntu loading screen. So I booted without the CD, and it would go to the grub menu. Now when I choose Ubuntu from the menu, I get: 

Error 18: Selected cylinder exceeds maximum supported by BIOS

And if I try to run XP, i still get the NTLDR is missing message. 

I'll keep trying to get into Ubuntu so I can get those logs. Any suggestions about why I can't get into ubuntu?

---

### Post by anystupidname on 2008-05-22
Are you running the latest BIOS firmware for that mobo? Have you triple checked all your ribbon cable and power connections and jumpers for the hard drive(s) in question? Does the BIOS properly detect the hard drive? (correct size and sectors shown in BIOS)
Regarding the NTLDR problem, theres a disk for that too heh:
[http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm](http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm)
Note: this will likely break grub so you'll have to rerun supergrub disk after fixing NTLDR.

---

### Post by jeffjohn on 2008-05-22
Help! I can not load any version of Ubuntu (7.04 7.10). The Hard drive is accessed and then the message:-

Stage 1.5
Grub Loading Error ....wait..

Error 18.

I have tried many reinstalls which look to be successful until I reboot; has something in the BIOS prevented this??  Any help deeply appreciated! Thanks jeffjohn

I can run from the live disc, no trouble.

---

### Post by cdtech on 2008-05-22
The BIOS reads the MBR from a disk.

It starts executing the bootloader (GRUB stage 1).
The bootloader jumps to the next stage. This sector number is stored at a location in the bootloader “code” during the GRUB install and it usually points to the stage 1.5 location immediately after the MBR.

It sounds to me that the GRUB bootloader code isn't being installed completely and halts at the end of stage 1 looking for the stage 1.5 location.

I personaly would fix the MBR in windows and see if you can boot into windows first. Then update the MBR using GRUB so that it corrects the issue at hand.

Just my thoughts.....

---

### Post by jeffjohn on 2008-05-22
CDTech- many thanks indeed! I'm sure you are correct; I was messing around in Partition Magic to try to sort dual booting and prob. screwed it, as nothing works now, except live Linux CD such as I am using - Knoppix.  Question...if I clone an XP disk using Acronis to make an identical copy of a working drive on to the faulty one, can I expect my MBR problem to be sorted?  Sorry if this is verging away from Ubuntu but I am tring to install latest!  Thanks again, jeffjohn

---

### Post by jobyjoe on 2008-05-22
Ok, I think something is really messed up now. Now my usb keyboard isn't working with the computer. I plug it into my laptop, and it works fine. Try it on the desktop, and I get nothing. It doesn't work at all. Now, can anyone give me any  pointers here. Or is something really messed up. Is the motherboard messed up?

---

### Post by cdtech on 2008-05-23
If you did clone the drive, it would correct the MBR for your Windows, then you can go from there. Did you clone the drive with the Linux partition or before?

I just got back from out of town and need sleep. I'll try to be back later to see what the outcome is.

Good Luck and sorry for your problems.

---

### Post by jeffjohn on 2008-05-23
Hi Cdtech!  thanks for your vigilance!  I'm deeply in a mess I think.  
I set the linux drive to Slave and used Acronis to convert it back to Windows XP NTFS by cloning on my main PC; that worked fine and I can see that it has copied successfully.  Replacing the drive as Master in the Linux PC, I can re-install Ubuntu (using the entire space available); however when I reboot, I always get the Grub loading error!  I can run Live CDs fine on the PC but can not get the BIOS to boot the HD, only from CDs or A-drive. 
When I get back from France in Sept. with the disk, I might try loading XP on the drive to check whether that works and if so go from there! 
Is there a 'kicker' diskette or USB that would boot up the HD rather than using the BIOS??  It fails again if I go from the Live distro menu to 'start HD'.  I looked in BOOT and the various Stage 1, 1.5, 2 seem to be there ok.  I also ran the Grub restore, which did identify errors and 'correct' things in Setup but no solution on reboot.
All this came about after I tried unsuccesfully installing XP on the Drive using an Autostreamer +SP2 disk; this mucked up the MBR apparently permanently.  Supposing I buy another small HD and use that to Boot.....?  Should work, shouldn't it...
Is there an XP version of FDISK /CMBR; no I'm going round in circles!!!  sorry!  Jeff

---

### Post by jeffjohn on 2008-05-23
The PC is a very modest Asus A7V 800 MHz AMD Athlon with 1 Gb RAM. The BIOS settings are all standard except 'Disabled BIOS virus detection'.  The Drive is a 'new' 200MB Samsung PATA 133.

If nothing comes to mind; don't worry - I'll try the XP install in Sept and report back, if I may!  Thanks jeffjohn

---

### Post by jobyjoe on 2008-05-23
yeah I really don't know what to do here. My keyboard isn't working with this computer now (but it works on all other computers) so I can't really do anything. I wish I could get into Bios. Any suggestions?

---

### Post by jobyjoe on 2008-05-23
OK!!! Now I have the keyboard up and working again. It just started working all of a sudden. But I still can't boot into anything. I still get that error 18 message when trying to load ubuntu.

---

### Post by jobyjoe on 2008-05-23
Ok I found something in BIOS that could/could not be wrong (I really don't know too much about BIOS). But when I go to my Standard CMOS features tab, it says IDE Primary Master is my DVD burner and my IDE Primary Slave is my other DVD burner. My first hard drive is actually the IDE Third Master and my other hard drive is the IDE Fourth Master. 

Maybe I'm wrong, but shouldn't the HD be in the IDE primary master spot. And if so how do you change it?

---

### Post by VMC on 2008-05-23
> **jobyjoe said:**
> Ok I found something in BIOS that could/could not be wrong (I really don't know too much about BIOS). But when I go to my Standard CMOS features tab, it says IDE Primary Master is my DVD burner and my IDE Primary Slave is my other DVD burner. My first hard drive is actually the IDE Third Master and my other hard drive is the IDE Fourth Master. 

Maybe I'm wrong, but shouldn't the HD be in the IDE primary master spot. And if so how do you change it?

I've read the entire post and I'm a little confused. Are you the one with the laptop or desktop? If desktop how did the BIOS get the drives swapped around? Did you change something? Without being in front of your computer I have no idea as how to make the changes, but you need to get the HD on the Primary and the DVD on the secdonary or slave. Can you do that?

Also, I think it was asked several pages ago to output the 'fdisk -l' and 'cat /boot/grub/menu.lst' commands from a terminal. Can you do that?

---

### Post by jobyjoe on 2008-05-23
Yeah I'm the one with the desktop. Yeah I have no Idea how the drives got switched. My computer worked fine till I upgraded to ubuntu 8.04. I have no idea how to switch the drives. They are both SATA, does that matter? I'll try to get the command lines, but whenever I try and use the Ubuntu Live CD, it freezes when it starts loading. I'll keep trying though.

---

### Post by jobyjoe on 2008-05-23
ok here you go: 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004c47b

  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15837   127210671    7  HPFS/NTFS
/dev/sdb2           15838       38160   179309497+  83  Linux
/dev/sdb3           38161       38913     6048472+   5  Extended
/dev/sdb5           38161       38913     6048441   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by VMC on 2008-05-23
> **jobyjoe said:**
> ok here you go: 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004c47b

  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15837   127210671    7  HPFS/NTFS
/dev/sdb2           15838       38160   179309497+  83  Linux
/dev/sdb3           38161       38913     6048472+   5  Extended
/dev/sdb5           38161       38913     6048441   82  Linux swap / Solaris
ubuntu@ubuntu:~$
Okay thanks. Now usually they would be /dev/sdax, but maybe your BIOS switch causes them to appear as /dev/sdbx.
Right now I can't go back to first page to check, but the 320GB HD is that IDE?

The SATA shouldn't matter. Is their any option to put the BIOS back to default or is there an AUTO detect option for the drives?
You mentioned the your BIOS stated the drive were IDE. Now your telling me you have SATA installed.

At any rate can you boot your Windows system with this setup?
Yoou could use the grub message:

grub-install /dev/sdb
=OR=
grub
find /boot/grub/stage1
root (sdb0,0) <==this is from above ouput. your will be different
setup (sd0)    <==same as above output
quit


The problem with the above commands is you have to have a Linux running to use it. You need to be able to boot from the livecd in order to fix the grub or reinstall grub. Do you have another minicd like Puppy Linux or Knoppix?

---

### Post by jeffjohn on 2008-05-24
CDtech - latest update!  Installed Win98 on the would-be Linux PC.  It installed no problem at all and boots from the HD no prob!  Apparently it is/was the Gutsy install that wrecked it!  Question now is how to proceed; would you think an Ubuntu install on a new partition is the way to go?  Thanks Jeff

---

### Post by cdtech on 2008-05-24
Yes, and during your new install be sure that the GRUB bootloader code is installed to the proper MBR of that primary drive.

Good luck.....

---

