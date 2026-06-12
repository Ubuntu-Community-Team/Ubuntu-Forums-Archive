---
title: "Unable to boot from 14.04"
date: 2014-08-17
forum: General Help
---

### Post by lojay397 on 2014-08-17
I was currently running 13.10 on a Dell latitude d630 laptop. I also have windows 7 pro installed on an external usb hard drive.
When I attempt to boot to windows from 13.10 using the F-key or even the BIOS itself,
Windows  attempts to start, but 13.10 interrupt, stopping the start-up and super-imposing its' own boot sequence.
I ran an update for grub from the terminal in hopes that would solve the issue.
It did not.
I followed up with an upgrade to 14.04. Still no change
At any rate, do you have any suggestions I might try to resolve this issue?

Thanks

---

### Post by Bashing-om on 2014-08-18
lojay397; Hi ! Welcome to the forum .

Booting: All depends on what you have installed where. What you tell bios as to what to boot, and where that boot code is located, that you told bios where to look for the boot code. Confused ?
Let's straighten the situation, Show us what we are working with - partition wise - so we know what is needed to be installed.
Post back the outputs - Between Code Tags - of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we can then discuss how you want to boot the operating systems, and what the options are.

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by lojay397 on 2014-08-19
lorenzo@lorenzo-Latitude-D630:~$ sudo fdisk -lu
[sudo] password for lorenzo: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00050e49

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   147933183    73965568   83  Linux
/dev/sda2       147935230   156301311     4183041    5  Extended
/dev/sda5       147935232   156301311     4183040   82  Linux swap / Solaris
lorenzo@lorenzo-Latitude-D630:~$ 
lorenzo@lorenzo-Latitude-D630:~$ sudo parted -l
Model: ATA WDC WD800BEVS-75 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  75.7GB  75.7GB  primary   ext4            boot
 2      75.7GB  80.0GB  4283MB  extended
 5      75.7GB  80.0GB  4283MB  logical   linux-swap(v1)



lorenzo@lorenzo-Latitude-D630:~$ sudo blkid
/dev/sda1: UUID="01e63f7a-9184-4e61-9ae7-24c335df40e9" TYPE="ext4" 
/dev/sda5: UUID="01fa7d07-d132-43f0-8137-0d035ca049f5" TYPE="swap" 
lorenzo@lorenzo-Latitude-D630:~$ 


As stated earlier, win7 comes up and tries to to start but is halted and 14.04 boot sequence begins and completes

---

### Post by Bashing-om on 2014-08-19
lojay397; Well;

Windows is not in this picture at all !
I must "assume" that on that external usb drive that you have your Windows install on, that the Window's boot code should be installed rather then ubuntu's boot code.

In that event, it is a Windows situation that only Windows can help with.
I do not do Windows, but I am aware that Windows has the tool "fixmbr" to repair the boot code to that of Windows.

With ubuntu's boot code installed on the MBR of drive 'sda' ( the internal drive);
and with Window's boot code installed onto the MBR of the external drive ->
at boot choose which drive to boot from in the bios selection.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Rev2010 on 2014-08-19
Have you tried using a boot repair disk such as Boot-Repair or Super Grub?:

[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

If you have another machine you can burn an ISO to CD or USB stick I'd give that a shot first.


Rev.

---

### Post by lojay397 on 2014-08-20
Will try all you have suggested, but what confuses me... when I reverse the situation...using windows as my primary and 14.04 as the external everything works fine which lead me to believe 14 was the culprit. A little insight, if you care to.

---

### Post by Bashing-om on 2014-08-20
lojay397; Hey;

Let's get a bit more insight into what is the booting method.
Background: What you set in bios to hand off to is the crucial thing. 

Say you set in bios to boot the 1st hard drive, in this case 'sda', that contains ubuntu, now the boot process has started, and bios hands off to the boot code that is located in the 1st sector of the hard drive designated. In your use case I would expect this boot code to contain the code to boot either ubuntu or Windows ( that is on that external drive). Depending on what you select in grub's boot menu. --IS this what happens ? --

OK, now you need to boot Windows separate from ubuntu. Set in bios to boot the external usb .. bios again hands off the boot process to the boot code located in the 1st sector of the external device. In this case that boot code is ONLY to boot Windows, as to Windows there is no other operating system in the world but Windows, "it don't recognize any other !" . So what you MUST have is Windows boot code installed to the MBR of that external device.

Situation at hand: What results for a boot menu when you have the external device plugged in, and set in bios to boot the internal, 'sda', hard drive ? Do you get a grub boot menu that also contains the option to boot Windows ?

What happens when you unplug the external device and boot from bios the internal hard drive ?

What happens when you have the external device plugged in and boot Windows from bios, setting in bios to boot from the external device ?
--------------------------------------

What we are examining here is your thought process and how the boot code must be installed to meet your needs.

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by lojay397 on 2014-08-20
So...if I understand you correctly...when I set BIOS to boot from USB, either from the BIOS menu or the F-key it essentially takes 14.04 out the mix, and anything occurs afterwards rests with windows. And there is no opportunity
for GRUB to interact.

---

### Post by Bashing-om on 2014-08-20
lojay397; Sorta kinda;


Now, we do not know what you have installed for boot code.
Consider:
IF you have the usb device plugged in and you boot the internal drive (sda) and you get the grub menu that has not only ubuntu, but also Windows boot option;
Then we may surmise that ubuntu's boot code is installed onto the MBR of this drive, and in addition Windows boot code is chainloaded onto grub.
From here you may boot your choice of ubuntu or Windows, perfectly fine.
Now also consider, if the external USB device is not connected (Windows), and you choose Windows to boot - in this menu - the boot process will not complete. The remaining boot code required is on that external USB device and grub can not hand off to what is not there.

OK, now you choose in bios to boot from the usb device ( Windows );
IF you now only have the normal boot options to boot Windows;
Then we can conclude that Windows boot code is properly installed onto the MBR of this USB device.
And NO Windows will not talk to ubuntu.

So in essence there are 2 means to boot Windows, from either drive because of the boot code - installed to both devices, and ubuntu's grub has chainloaded Windows to it's boot menu. But, you can only boot ubuntu from the hard drive, as that is the only place the boot code for ubuntu can reside.

[INDENT][INDENT][INDENT]clear as mud ?
[/INDENT][/INDENT][/INDENT]

---

### Post by lojay397 on 2014-08-25
With all that being said which is most appreciated... even though more confusing. Still, 
I have managed to access windows recovery from the usb boot and ran system repair.
Windows said it was unable to repair and that "system volume on disk is corrupt". With
this bit of info...can I now take 14.04 out the loop?

This is a oddity I just notice... When I restart 14.04 and use the F-key to invoke the boot
menu, the usb storage entry is not present. However, when I do a complete shut-down 
and used the key @ system start-up the usb entry is listed. Could this mean it's not 
being recongised by 14.04.

---

