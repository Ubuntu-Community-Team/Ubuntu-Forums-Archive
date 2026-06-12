---
title: "Reinstalling Ubuntu on a Samsung Windows 8 laptop"
date: 2015-03-16
forum: General Help
---

### Post by 1ktmeadows on 2015-03-16
I have posted a thread a year ago about the issue of my laptop and how I'm not able to get access to my Ubuntu side of my laptop; which is dual booted with Windows 8. I want to say Thank you for those that did help me in the past but I was not able to spend the time needed to fix my computer but I do now. My laptop for some reason will not allow me to get into Ubuntu. What I mean by that is, when I choose Ubuntu and then put in my password; all I get is a black screen that will not go away. So my question is, can I reinstall Ubuntu without losing Windows 8 and if so how? OR Is there a way to fix my computer without having to reinstall Ubuntu? 
Thank You

---

### Post by pmi2 on 2015-03-16
I would boot from the old Ubuntu Live CD (or make a new one from the latest release of 14.04.2), then mount the partition your last Ubuntu installation is on. 

 If that works, you can then back up your Home directory and any other data you need to save, run Boot-Repair from the live CD, or upgrade, or write over the old installation, or delete the old Ubuntu partition and start over, etc...

In other words, if you can boot ubuntu from a live CD and at least see the old Linux partition, you have any number of choices.

---

### Post by oldfred on 2015-03-16
What model Samsung and what video chip does it have. Or an Ultrabook with dual video?

Does recovery mode, or second entry in grub menu let you boot or just to a terminal?

If Intel only chip then nomodeset does not usually work and some of the Intel or specific video settings are often required.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by 1ktmeadows on 2015-03-17
[FONT=times new roman][SIZE=4]I have a Samsung NP470R5E-K01UB laptop with a Intel HD Graphics 4000. The processor is a Intel Core i5 processor 3230M. [/SIZE][/FONT][SIZE=4][FONT=times new roman]I can boot in the grub menu but when I sign in with my password on Ubuntu, then my screen goes black and it does not go away. Back when I was trying to fix my laptop I tried doing nomodest but it did not work. I also tried doing e for edit and scrolling to the linux line and replacing quiet splash with [/FONT][/SIZE][FONT=times new roman][SIZE=4]nomodest but it did not work. I can also boot from a Live CD and I can see my partitions. Pmi2 when you mean by mounting do you mean just in my way of thinking, just reinstall over the Ubuntu partition; if that is correct? 
Oldfred and Pmi2, I just want to say is Thank You for helping me I appreciate it a lot.
Lastly, the data on my computer is not important to me.
 [/SIZE][/FONT]

---

### Post by oldfred on 2015-03-17
With Intel nomodeset usually does not work.
But try each of  these instead of nomodeset in grub menu as you boot.

       Force Intel Video mode as boot parameter in grub menu - Must change to your screen size, not 1280x1024

video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60


 acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

---

### Post by pmi2 on 2015-03-17
> **1ktmeadows said:**
> [SIZE=4]...[/SIZE][FONT=times new roman][SIZE=4]I can also boot from a Live CD and I can see my partitions. Pmi2 when you mean by mounting do you mean just in my way of thinking, just reinstall over the Ubuntu partition; if that is correct? ...[/SIZE][/FONT]Yes.  As long as you can boot from a live CD and see that partition, you have lots of options.  Having said that, I would probably try the directions in the post above,  just to see what happens.  After all, if it happened once, it could  happen again, and then you would already know how to fix it.

If repairing your installation does not work, and if there are no files you need to save on the Ubuntu partition, you could just reinstall over the old version of Ubuntu, while keeping Windows intact.  If this goes back a year, installing the latest version of ubuntu may have other benefits.

---

### Post by 1ktmeadows on 2015-03-19
Oldfred,I'm on the grub menu and I push "e" on Ubuntu but I can not find where I can change the video and the other commands that you posted. Do I type in the commands under the "setparams Ubuntu"? Where do I go to so that I can add:

video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

Thank you again Oldfred and Pmi2

---

### Post by oldfred on 2015-03-20
All those are boot parameters just like nomodeset.

From post #3
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&page=2&p=12871710#post12871710]("http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710")

---

### Post by 1ktmeadows on 2015-03-23
I read the links and I tried "**How to temporarily set kernel boot options on an installed OS (not wubi)**" with adding in:
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

But that did not work on both of them. I do not know if this helps but when I get to the black screen I can still see my cursor and I can move it around. What do you think might be the problem? Now Oldfred, I read most of this link: [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) but my question is, can I reinstall Ubuntu over my old Ubuntu partition? From what I read, if I do reinstall over my old partition that I will come across a lot of issues or that Windows 8 will be erased?

---

### Post by oldfred on 2015-03-23
As long as you choose the something else install option and not any of the auto options, you should be ok.
Even the auto option that may say installing over Ubuntu may erase entire drive. You should have full backup of Windows anyway as even hard drives totally fail and how would you reinstall if drive failed?

But if you select the same / (root) partition for your new / , and select ext4 for format, you will be ok. If /home is separate you must also select it, but DO NOT format it if you want to save your data. Otherwise you should have good backups of /home, list of installed applications, if you added a lot and perhaps a few other things if a re-install over a previous working install. 
On a reinstall it seems to automatically find & reuse swap. 

If a video driver issue, I do not think a reinstall will change anything. I have nVidia card and have always had to use nomodeset as a boot option until I install the proprietary nVidia drivers.

Be sure to boot in UEFI mode, as UEFI will give two boot options for the Ubuntu installer. And how you boot is how it installs.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

 [http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by 1ktmeadows on 2015-03-23
Thank you again for the help. I was wondering, would my video driver have issues even if I can still go on the Windows side of my computer? Also, the windows side of my computer works perfectly.

---

### Post by oldfred on 2015-03-23
Should not.

Of course years ago I remember saying that about a network card. And one or the other system did not reset on shutdown or fully reset on reboot. And card saved a setting internally causing issues.

---

### Post by 1ktmeadows on 2015-03-29
Sorry for posting back so late. I will try to reinstall Ubuntu but I was wondering about what you mean by booting from UEFI mode? When I try to boot from my USB I these options: 
Ubuntu, Ubuntu, UEFI OS, and UEFI: Sandisk U3 Cruzer Micro 8.02.

Is booting from the UEFI: Sandisk U3 Cruzer Micro 8.02, what you mean by booting from the UEFI mode?

or

Do you mean when I start my computer and on the grub menu that I choose "Windows Boot UEFI loader"?

---

### Post by 1ktmeadows on 2015-03-29
Lastly, here is an image of my partitions on my computer. I'm not sure if this might help fix the issue going on with my computer.

---

### Post by 1ktmeadows on 2015-04-05
Oldfred, Pmi2, and others, I really need your help. My computer updated to windows 8.1 and know I'm getting an error. I'm getting this error:
error: unknown filesystem.
Entering rescue mode...
grub rescue>

I have tried different things to try and fix this issue. I have tried: 
set boot=(hd0,msdos6)
set prefix=(hd0,msdos6)/boot/grub
insmod normal
normal

This did not work so I tried:
prefix=(hd0,5)/boot/grub
root=hd0,5
insmod normal
normal

When I put in insmod normal, I would get "no such partition". When I put in normal, I would get "Unknown command 'normal' ". I tried to boot from my USB with Ubuntu on it but that did not work. I'm not sure if I did it wrong but I powered off my computer, then powered my computer back on  and then pushed F12. It did not boot from my USB and it went back to:
error: unknown filesystem.
Entering rescue mode...
grub rescue>

Can Someone please help me.
Thank You

---

### Post by oldfred on 2015-04-05
Do you still have the sda8 as ext4 that you showed in above gparted screenshot?
Windows does not know about ext4 partitions and often rewrites partition table without any linux partitions. Then we have to use testdisk to find old partition and add it back. Testdisk is in repository and you can download it into the live installer.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
OR:
 Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)

---

### Post by 1ktmeadows on 2015-04-05
No, that is an old photo of my partitions on my computer but here is an up to date image of my partitions.

---

### Post by 1ktmeadows on 2015-04-05
Here is my partitions. Do you all know what is going on with my computer.

---

### Post by oldfred on 2015-04-05
Those partitions look pretty much normal.
Are you booting in UEFI mode. Did you boot in UEFI mode before or did you only boot from UEFI menu and switch from UEFI to BIOS?

May be best to see details. From live installer post link to Summary report.
              
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

