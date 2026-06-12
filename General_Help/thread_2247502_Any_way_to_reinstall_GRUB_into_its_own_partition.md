---
title: "Any way to reinstall GRUB into its own partition??"
date: 2014-10-08
forum: General Help
---

### Post by este.el.paz on 2014-10-08
Folks:

Little bit of a sticky wicket . . . have a triple boot set up, did an upgrade in another partition and it seemed to wipe the Xubuntu 14.04 partition from view.  Got SuperGrub2 CD out and got in, checked GParted and there is an error exclamation next to the bios_grub partition.  Read through the wiki and downloaded the "Boot Repair drive" . . . ran it through its thing, looks like it installed GRUB in the "/" partition (sda6) . . . but seems like that didn't work.  Tried to adjust the settings to get it into sda5 where it was before, but it wouldn't do that, only choices are sda1 or 6 . . . I want 5.

In the wiki I remembered something about booting an alternate install disk and using "rescue system" . . . and went through the steps, tried to get GRUB bootloader to install, and it failed.  I tried to "erase the sda5 data" . . .which it did, but then it would not install GRUB . . . error saying something about "flagging the partition" . . . but tabbing around in the installer menu on that partition, couldn't change the "Boot flag" from "off" to on . . . .  Anyway, now the sda5 partition is empty, but synaptic shows that GRUB is installed . . . but it must be in sda6 which doesn't get the system booted. 

Any chance to get some commands that could run in terminal to get GRUB in its own partition again . . . /dev/sda5 . . . ???  I read through some other threads that showed how to install GRUB to the root directory, but that doesn't get the system to boot.  It might be that nuke and pave is my only next option, but I'd like to avoid that if possible, I've got a number of repo additions that I'd like to save if possible.

Thanks for any help,

e.e.p.

---

### Post by yancek on 2014-10-08
You indicate a triple boot setup but only mention one system, Xubuntu.  It would be helpful if you indicated what the others were.  Also, if you used 'boot-repair', it should output a file with information on drives/partitions and boot files which would also be useful.  Installing to the root partitiion won't cause it to boot unless you have another system with boot code in the MBR.  The same applies if you have a boot partition, you need some code in the MBR pointing to it.  If you are using GPT/UEFI this isn't needed.  Did you previously have a separate boot partition?  Are you using MBR or GPT/UEFI?

---

### Post by este.el.paz on 2014-10-08
> **yancek said:**
> You indicate a triple boot setup but only mention one system, Xubuntu.  It would be helpful if you indicated what the others were.  Also, if you used 'boot-repair', it should output a file with information on drives/partitions and boot files which would also be useful.  Installing to the root partitiion won't cause it to boot unless you have another system with boot code in the MBR.  The same applies if you have a boot partition, you need some code in the MBR pointing to it.  If you are using GPT/UEFI this isn't needed.  Did you previously have a separate boot partition?  Are you using MBR or GPT/UEFI?

@yancek:

Thanks for the reply, the link to the boot repair file is below, but that may or may not be relevant, since trying the "rescue mode" gambit I erased the GRUB data to try to solve the "error" on "installing GRUB" . . . thinking that it might recognize GRUB as being there, etc . . . but, it would not install into the empty partition, which, yes, was already there and was working quite fine until recently . . . .  Not sure on the MBR, I tend to think not . . . probably GPT . . . I used GParted to set up the partitions manually.  sda5 partition is there now, but empty, waiting for a fresh install of GRUB, but Boot Repair doesn't seem to be able to do it, and neither did Rescue mode . . . .

[http://paste.ubuntu.com/8517383](http://paste.ubuntu.com/8517383)

e.e.p.

---

### Post by Dennis N on 2014-10-08
Your disk has GPT partitioning, and you are installing and booting in BIOS mode, so grub should be installed to sda. The bios boot partiton is for part of the grub code, not all of it. So don't try to install grub to sda5.

I have this copied in my notes:

> "In operating systems that support GPT-based boot through BIOS services rather than EFI, the first sector MBR is also still used to store the first stage of the bootloader code, but modified to recognize GPT partitions." 

The exclamation point seen in gparted is because that partition (bios boot) remains unformatted so just ignore it. I see the same thing.

I have one computer set up this way, with GPT partitioning and BIOS boot and it works well. It's a better choice than MSDOS partitioning in my opinion, as it uses only primary partitions (128 can be made by default) and a backup partition table in case the main one is ever damaged.

---

### Post by este.el.paz on 2014-10-08
> **Dennis N said:**
> Your disk has GPT partitioning, and you are installing and booting in BIOS mode, so grub should be installed to sda. The bios boot partiton is for part of the grub code, not all of it. So don't try to install grub to sda5.

I have this copied in my notes:

The exclamation point seen in gparted is because that partition (bios boot) remains unformatted so just ignore it. I see the same thing.

I have one computer set up this way, with GPT partitioning and BIOS boot and it works well. It's a better choice than MSDOS partitioning in my opinion, as it uses only primary partitions (128 can be made by default) and a backup partition table in case the main one is ever damaged.

@Dennis:

Thanks for the reply . . . but, GRUB was installed in sda5 . . . showing some size of data there, and however it was, it worked . . . and then it didn't.  And apparently BR "installed" GRUB to sda6 . . . but, doesn't work to boot the system.  And, now, it's erased from sda5 . . . and the only way to boot is with SG2 disk.  So,lets say that GRUB is in "sda" . . . the "root" . . . how to get the system to "recognize" that GRUB is there so that I can boot into Xubun the way I could before the upgrade in Disk 2??

e.e.p.

---

### Post by Dennis N on 2014-10-08
sda5 is your bios boot partition. You do not install grub there. What you see here is just part of the grub code (core.img). The initial part of the grub code is in the MBR. That's where you install it. Read again the quote in the last post.


```
sda5: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

```

---

### Post by este.el.paz on 2014-10-08
> **Dennis N said:**
> sda5 is your bios boot partition. You do not install grub there. What you see here is just part of the grub code (core.img). The initial part of the grub code is in the MBR. That's where you install it. Read again the quote in the last post.


```
sda5: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

```


@Dennis:

You may be absolutely correct in what you are saying, but, my question and issue remains.  Running through the SG2 list of repairs to GRUB did not revive the capacity to boot into 14.04, same with BR which said it was "installing GRUB into sda" . . . and, again problems with the alt install "rescue" mode . . . .  And, whatever was in sda5 is now gone, whether it is needed or not; however in the past when I did an "automatic" install it would say "GRUB is installed successfully" . . . but, it would not work to boot the system.  So lately I've had to set up the three partitions, the 10MB flagged as "bios_grub" and then whatever gets installed . . . works.  

I had a similar situation a year or so back when I was running LM16 and posted this approximate question on the forum, but, got no response let alone direction . . . wound up with the nuclear option--I'd like to try to avoid that, detente and all.  Only other thought is that the alt installer I tried was for 12.04 64 bit . . . I don't have the alt install for 14.04, but I might try to see if the live desktop for 14.04 I have would offer a better rescue tool???

e.e.p.

---

### Post by Dennis N on 2014-10-08
You need the bios-grub partition whenever you use GPT partitioning with BIOS install and booting (as you have in your setup). That's why it works - grub requires it to be there. Most people use MSDOS partitioning with BIOS installs and booting and for that you don't need the bios-grub partition.

If you have GPT partitioning with UEFI install and booting, you need an EFI system partition instead.

Sorry - I can't give much advice on rescue tools - I never had to use any, just lucky I guess. There is the boot repair script of course, and I used to have System Rescue CD around at one time but never needed to use it. I believe it will allow you to boot into your Ubuntu install on your hard disk from its live cd and once that is done, you can reinstall grub. You can google it and find out about it.

Someone who knows more about those tools hopefully will have more to say. 

As a last resort, you could copy your important files from Ubuntu partition to an external drive using the live cd and then just reinstall it.

---

### Post by este.el.paz on 2014-10-08
```
$ sudo apt-get install grub2-common
[sudo] password for : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub2-common is already the newest version.

```

All these different checks are showing that grub2 is installed, but the grub window is not showing up on restart, and I'm not able to log in to Xubun w/o SuperGrub2 CD . . . .

e.e.p.

---

### Post by Dennis N on 2014-10-08
> **este.el.paz said:**
> ```
$ sudo apt-get install grub2-common
[sudo] password for : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub2-common is already the newest version.

```

All these different checks are showing that grub2 is installed, but the grub window is not showing up on restart, and I'm not able to log in to Xubun w/o SuperGrub2 CD . . . .

e.e.p.
To set up grub in the proper locations on the hard disk, you need to boot into Ubuntu, then run these two commands (in this order) from Ubuntu's terminal:
```
sudo grub-install /dev/sda
sudo update-grub
```
Those will set-up grub correctly on the hard disk and then detect any other operating systems that are present. Normally, the Ubuntu installer does this for you when you first install Ubuntu. The term 'install' is also used for this set-up process, so that is confusing! 
**If you can't boot into Ubuntu**, then by another sequence of special commands this set-up can be redone from a live cd, but I don't know the needed commands or have ever needed to use them. A repair program or repair disk(?) should be able to do this 'set-up' also.

---

### Post by este.el.paz on 2014-10-08
> **Dennis N said:**
> To set up grub in the proper locations on the hard disk, you need to boot into Ubuntu, then run these two commands (in this order) from Ubuntu's terminal:
```
sudo grub-install /dev/sda
sudo update-grub
```
Those will set-up grub correctly on the hard disk and then detect any other operating systems that are present. Normally, the Ubuntu installer does this for you when you first install Ubuntu. The term 'install' is also used for this set-up process, so that is confusing! 
**If you can't boot into Ubuntu**, then by another sequence of special commands this set-up can be redone from a live cd, but I don't know the needed commands or have ever needed to use them. A repair program or repair disk(?) should be able to do this 'set-up' also.

@Dennis:

OK, thanks for those commands . . . I was booted in Xubun and I ran the commands in the Terminal, and it seemed to be good, found the linux kernel and so forth, said, "no error" on the first line, and then "done" after the up-date grub line and showing the "memtest" lines, etc. . . but, on reboot, the "GRUB" screen shows . . . "no bootable device--insert boot disk and press any key." . . . .  Only way to get out of it seems to be to shut down.  Something seems to be "missing."

e.e.p.

---

### Post by Dennis N on 2014-10-08
You don't get a complete Grub Menu? If your computer has UEFI, be sure you are NOT booting in UEFI mode - you need to boot in Legacy (BIOS) mode.

We also have this problem: From your boot info you posted, you have Mac OS X on here, and I was just made aware of this policy: "We cannot help on Hackintosh systems as that is against Code of conduct. We are not allowed to violate other vendors terms of use." The Apple software license does not allow Mac OS X to be used on a computer that is not "Apple-branded". So....

I can suggest you google "no bootable device--insert boot disk and press any key Ubuntu" and you will get lots of matches.

---

### Post by este.el.paz on 2014-10-08
> **Dennis N said:**
> You don't get a complete Grub Menu? If your computer has UEFI, be sure you are NOT booting in UEFI mode - you need to boot in Legacy (BIOS) mode.

We also have this problem: From your boot info you posted, you have Mac OS X on here, and I was just made aware of this policy: "We cannot help on Hackintosh systems as that is against Code of conduct. We are not allowed to violate other vendors terms of use." The Apple software license does not allow Mac OS X to be used on a computer that is not "Apple-branded". So....

I can suggest you google "no bootable device--insert boot disk and press any key Ubuntu" and you will get lots of matches.

@Dennis:

No worries mate, it's not a Hackintosh . . . it's a MBPro . . . I've got rEFInd as the boot loader . . . I get to my rEFInd window, there it shows two linux penguins now, where before there was one . . . .  Neither one works.
e.e.p.

---

### Post by Kirkx on 2014-10-09
If you really want to install Grub2 in a dedicated partition then here are the instructions. Keep in mind that my boot is legacy BIOS and I'm chainloading to Grub2 from Grub4Dos. My dedicated Grub2 partition is /dev/sda20 so you would need to change the device number accordingly.

----------
#) Dedicated Grub2 Partition
x) installing Grub2 to the partition /bootpt

     # boot to any Linux distro that supports Grub2
     # mount /bootpt partition
     # run the following command ( --force is needed to install Grub2 anywhere outside MBR )
     sudo grub-install --force --root-directory=/media/xyz/bootpt /dev/sda20
     
     # this will not work
     sudo grub-install --force /dev/sda20
     
     # unmount /bootpt
     
    - config and module files will be installed in /media/xyz/bootpt
    - boot image will be installed into the first sector in /dev/sda20
    - ref: [http://askubuntu.com/questions/54416/creating-a-dedicated-grub-partition-before-installing-ubuntu](http://askubuntu.com/questions/54416/creating-a-dedicated-grub-partition-before-installing-ubuntu)

x) create a "grub.cfg" file ( /boot/grub/grub.cfg )
    - if the file is missing the computer will boot to Grub2 CLI
    
    sudo grub-mkconfig -o /media/xyz/bootpt/boot/grub/grub.cfg
    
    - parameter "-o" is used to create the actual file (default output = stdout)
    - "grub.cfg" file in a dedicated Grub2 partition can be safely edited
    - "grub.cfg" file installed inside an OS should never be edited as it's linked to other config files

x) after every kernel update run:
    sudo grub-mkconfig -o /media/xyz/bootpt/boot/grub/grub.cfg

x) chainloading Grub2 from Grub4Dos

title Grub2 (Standalone)
kernel (hd0,19)/boot/grub/i386-pc/core.img

x) references
     [http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/](http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/)

---

### Post by este.el.paz on 2014-10-09
> **Kirkx said:**
> If you really want to install Grub2 in a dedicated partition then here are the instructions. Keep in mind that my boot is legacy BIOS and I'm chainloading to Grub2 from Grub4Dos. My dedicated Grub2 partition is /dev/sda20 so you would need to change the device number accordingly.

----------
#) Dedicated Grub2 Partition
x) installing Grub2 to the partition /bootpt

     # boot to any Linux distro that supports Grub2
     # mount /bootpt partition
     # run the following command ( --force is needed to install Grub2 anywhere outside MBR )
     sudo grub-install --force --root-directory=/media/xyz/bootpt /dev/sda20
     
     # this will not work
     sudo grub-install --force /dev/sda20
     
     # unmount /bootpt
     
    - config and module files will be installed in /media/xyz/bootpt
    - boot image will be installed into the first sector in /dev/sda20
    - ref: [http://askubuntu.com/questions/54416/creating-a-dedicated-grub-partition-before-installing-ubuntu](http://askubuntu.com/questions/54416/creating-a-dedicated-grub-partition-before-installing-ubuntu)

x) create a "grub.cfg" file ( /boot/grub/grub.cfg )
    - if the file is missing the computer will boot to Grub2 CLI
    
    sudo grub-mkconfig -o /media/xyz/bootpt/boot/grub/grub.cfg
    
    - parameter "-o" is used to create the actual file (default output = stdout)
    - "grub.cfg" file in a dedicated Grub2 partition can be safely edited
    - "grub.cfg" file installed inside an OS should never be edited as it's linked to other config files

x) after every kernel update run:
    sudo grub-mkconfig -o /media/xyz/bootpt/boot/grub/grub.cfg

x) chainloading Grub2 from Grub4Dos

title Grub2 (Standalone)
kernel (hd0,19)/boot/grub/i386-pc/core.img

x) references
     [http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/](http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/)

@Kirkx:

Many thanks for the detailed response and links . . . your post is appreciated.  I will check into this, but today starting off a little too fast to jump on it.  However, right now I think that Grub2 is "installed" . . . according to synaptic . . . and Boot Repair . . . .  But, what **might*** be the problem is the grub-cfg file??  might have been erased out of the separate "bios_grub" partition? when I used the alt installer to "erase the data" . . . so that I could reinstall it, but which then errored out.  

So, I might start off with that issue and see if it gets me back into the Xubun system . . . using the option key.  In any event I will go through what you've posted here and see what stands out as the issue, and test it out.  Like I said I've been here before with a LM system that got broken by an OSX upgrade . . . and, finally had to accept the nuclear option; this time I have much more time invested in the Xubun 14.04 system that I'd prefer to "negotiate."

Thanks for the help,

e.e.p.

---

### Post by este.el.paz on 2014-10-20
> **este.el.paz said:**
> @Dennis:
 	Code:
 	sudo grub-install /dev/sda
sudo update-grubOK, thanks for those commands . . . I was booted in Xubun and I ran the commands in the Terminal, and it seemed to be good, found the linux kernel and so forth, said, "no error" on the first line, and then "done" after the up-date grub line and showing the "memtest" lines, etc. . . but, on reboot, the "GRUB" screen shows . . . "no bootable device--insert boot disk and press any key." . . . .  Only way to get out of it seems to be to shut down.  Something seems to be "missing."

 
e.e.p.

> **este.el.paz said:**
> @Dennis:

No worries mate, it's not a Hackintosh . . . it's a MBPro . . . I've got rEFInd as the boot loader . . . I get to my rEFInd window, there it shows two linux penguins now, where before there was one . . . .  Neither one works.
e.e.p.

Folks:

The saga continues . . . I again ran these commands and it says "configuring grub cfg file" . . . and "successful install" of GRUB, but on reboot w/o SuperGrub2 the error "no boot disk found" shows up . . . even though SG2 can find and boot the system.  Actually it looks like there might be some corruption in the system, had a problem on Saturday running basic Terminal "update/upgrade" . . . and then today SG2 ran into some problem "finding '/'" . . . a few other problems . . . had to try again, then on second SG2 boot, the log in window appeared to crash . . . and then recover . . . mouse was frozen, blinking cursor was not blinking, etc.  But then was able to log in and try to run the "grub-install" commands . . . Terminal say it "went well" . . . .

So, perhaps my original question about GRUB in its own partition is not the problem?  Question is how to regain ability to boot linux . . . ???

e.e.p.

---

### Post by este.el.paz on 2014-10-22
Tried numerous ways to boot the recovery system and ran through some of the "repairs" . . . nothing worked to revive the system . . . .  Nuked it, repaved . . . couple of reboots gets me back into a working system . . . back to LM w/17 . . . w/MATE . . . .  Have to get the fan control thing set up . . . .

e.e.p.

---

