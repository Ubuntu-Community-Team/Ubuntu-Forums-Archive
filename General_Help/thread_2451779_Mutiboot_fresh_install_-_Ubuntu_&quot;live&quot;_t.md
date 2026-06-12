---
title: "Mutiboot fresh install - Ubuntu &quot;live&quot; then &quot;grub &quot;?"
date: 2020-10-10
forum: General Help
---

### Post by helen314 on 2020-10-10
This a "caution question", I do not want  to screw things up- again.

FOR TEST purposes - I have successfully  used "live USB" and  installed FULL version of 16.04 using UEFI.
By full version I mean I did let installer to do its work erasing , formatting , partitioning FULL disk.
Reboot worked fine. 

AGAIN FOR test and learning purposes I did  repeat the process , again UEFI, only now I let the installer to install another clean copy of OS 
on same disk , ALONGSIDE existing OS - it is one of the install regular option. Nothing special.  

Reboot has given me NO Choice of OS.  

I am assuming I need to configure "grub"  to have choice of OS to boot from. 


ADDENDUM 
This is my next step  link 

[https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples)










From reading few documents -  I need to marry UEFI and "grub" .
I am not sure where to start and  prefer NOT to do this process manually.
I understand  UEFI  is fully capable to "navigate' resources , however I am not sure how to 
pass "stuff" to "grub"
I do not want to repeat my mistakes / mishaps, I ended up with totally different partitions data in "grub" , so I would prefer 
NOT add / build /configure "grubx" manually. 

Again, this is for test / learning purposes,' and NO Windows , just plain Ubuntu. 
Cheers

---

### Post by oldfred on 2020-10-10
If both installs are UEFI, you just need to run:
sudo update-grub

But you cannot mix UEFI & BIOS on same drive and best not to mix on same system.
If UEFI hardware always boot in UEFI mode and only use gpt partitioning.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by grahammechanical on 2020-10-10
After the second installation finished did the reboot load to a working Ubuntu desktop? Was it the second installation. Yes, you are right. There should have been a Grub boot menu. I have no personal experience with UEFI. The best I can do is offer the relevant Ubuntu wiki help page.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I note this comment

> If you aren't multi-booting with another OS and you don't care about  your boot mode, you can forego some of the picky details of the  preceding procedure and install Ubuntu in whatever boot mode your  computer happens to pick. This procedure is **not recommended**  for multi-boot installations alongside existing UEFI-based OSes,  because it can result in a combination of one OS installed in UEFI mode  and the other in BIOS mode. Such setups will require post-installation  repair or other awkward steps to manage switching OSes. 

Could it be that one install was done in BIOS mode and the other in UEFI mode?

As suggested run the command

```
sudo update-grub
```

and see if the printout shows the other installation being detected.

Regards

---

### Post by helen314 on 2020-10-10
Yes,  update_grub is CORRECT , per doc, way to reconfigure grub AFTER new OS add.

It resulted in " choose correct boot device " message and no boot. 

YES ALL MY INSTALLS WERE UEFI, as I said already. 

NO DOS, NO WINDOWS !

HERE is what efibootmsg gives me - **pretty sad basic telling very little**. 
( I am RTFM about efibootmsg ) 

I believe . like it or not, I need to figure out what "ubuntu"  - boot order 5 came from - it has to be related to "grub" . 


b@b-multiboot:~$ efibootmgr
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0004,0005,0003
Boot0003* USB 
Boot0004* ubuntu
Boot0005* Hard Drive 
b@b-multiboot:~$

Here is current  update-grub

b@b-multiboot:~$ sudo update-grub
[sudo] password for b: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-118-generic
Found initrd image: /boot/initrd.img-4.15.0-118-generic
Found linux image: /boot/vmlinuz-4.15.0-45-generic
Found initrd image: /boot/initrd.img-4.15.0-45-generic
Found Ubuntu 16.04.7 LTS (16.04) on /dev/sda2
Adding boot menu entry for EFI firmware configuration
done
b@b-multiboot:~$ 


It identifies first OS on sda2  ONLY , no second OS ( on sda4).


The other entries are leftovers from original OS  -  they used to show in grub , not any more.

There are SEVERAL grub files in my system - which one is being updated ???

/boot/grub/grub.conf ?? 

How does  'ubuntu" (boot 004)  link to what grub file ??

---

### Post by oldfred on 2020-10-10
You have the Ubuntu entry.
If only Ubuntu installed, grub will not show grub menu as just default to your Ubuntu install.
But then if you have other issues or need a boot parameter, then you need to force the grub menu, so you can use recovery mode or ad boot parameter.
If you press escape key at end of UEFI/BIOS screen but before grub, do you get grub menu? You often have to try more than once and have to have UEFI fast boot off in UEFI settings as that assumes you have made no changes to system and boots before you have time to press any key.

---

### Post by helen314 on 2020-10-10
escape key at end of UEFI/BIOS screen but before grub, do you get grub menu? 

No, I get a long message telling me  in an effect I have wrong boot device and need to change it . 
The message does not identify the "FAULTY" device location. 

My best guess it is referring to USB device which is about the only one I could physically   replace . 

When I get UEFI  splash screen I have several options - setup, select  boot device or let UEFI boot from available( set by  UEFI setup)  devices .
ONE OF THE DEVICES IS CALLED "ubuntu" and I still do not know how it fits into scheme of things, BUT when UEFI  boots using "ubuntu" I get into "grub" menu.
That is the menu which gives "advance : options etc. and that is where the second OS options should be. 

At least that how it used to work - grub menus had all available OS data with version / partition identification.



If only Ubuntu installed, grub will not show grub menu as just default to your Ubuntu install.
That is NOT the case - itl shows / enable access to "advanced / recovery " modes and  access option to go back to UEFI setup.

---

### Post by oldfred on 2020-10-10
Always post the detailed version of efibootmgr.
sudo efibootmgr -v
You will only have one ubuntu entry for all installs. And it will then boot the last installed version. There is a 3 line grub.cfg in /EFI/ubuntu that uses UUID to refer to the partition of the Ubuntu install it will use and its full grub.cfg (menu).

Your last install is always the grub that is in control. And then grub adds any other installs to grub menu.

So your install on sda4 must be first grub menu entry as it found another install on sda2 as 16.04 and is shown near bottom of grub menu.
So boot first menu entry.

---

### Post by helen314 on 2020-10-11
Thanks for sticking with me, making progress. 


Here is my current efibootmgr

Note
It does not identify partition used - no sda4, but ID
Yes, UEFI  boots using last OS installed -sda4
Entries 3 and up are different , new when I had single OS 
Entries 3  and up hardware DOes  NOT exists on my system 
I can guess HD , but what is BBS ? 

Booted automatically , no manual interventions.
"grub" had NO entries indicating multi boot system - only sda4 

> 
b@b-multiboot:~$ efibootmgr -v
BootCurrent: 0001
Timeout: 5 seconds
BootOrder: 0001,0002,0003,0004,0005
Boot0001* ubuntu    HD(1,GPT,b03e313d-282a-4fec-9497-95f6e48116fd,0x800,0x100000)/File(\EFI\ubuntu\grubx64.efi)..BO
Boot0002* Hard Drive     BBS(HD,,0x0)..GO..NO........o.S.A.M.S.U.N.G. .H.D.0.8.0.H.J....................A...........................>..Gd-.;.A..MQ..L.0.S.E.8.1.J.Y.0.3.5.8.5.5.5. . . . . . ........BO
Boot0003* UEFI:CD/DVD Drive    BBS(129,,0x0)
Boot0004* UEFI:Removable Device    BBS(130,,0x0)
Boot0005* UEFI:Network Device    BBS(131,,0x0)
b@b-multiboot:~$ 



Question 
Am  I manually updating grub or  grub2?

TODO 
Verify latest UEFI verision, having some uncalled  for behavior( detects uninstalled CD ?)  after last on-line update.


ADDEndum
MY objective was to have dualboot OS on single SATA drive.  
I relied on standard ISO installation using an option to "install OS alongside of existing OS ".
The installations - both single  and "alongside" do not mention anything about "grub", 
It makes some seance to install "grub"  with LAST OS installed, however, not having "grub" entries 
for the first OS  installed makes the ISO "install alongside" questionable.  

I do not have dualboot system - hence my objective was not achieved. 

Please note that I realize that having TWO Ubuntu OS on same drive is of no practical usage.

Stand-by for more comments...

---

### Post by oldfred on 2020-10-11
I had to look up BBS.
> BBS Support means BIOS Boot Specification.
Or booting that device in the old BIOS/Legacy/CSM boot mode.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

Forget about grub (although we often say grub now).
Original Grub is now grub legacy and it was replaced with grub2 in 2010.
Since so old and officially "grub legacy" we may just refer to grub but now mean grub2. If actually referencing old grub we would specify grub legacy.
Grub legacy is still in the repositories. And package name has not changed, still is just "grub" in repository. So if you install grub, you install a 10 year old BIOS boot loader. In repository grub2 is grub-pc for BIOS or grub-efi-amd64 for 64 bit UEFI PCs. 

I have seen users have issues booting when they have CD/DVD configured in UEFI/BIOS, but do not have that device. Best to make sure any hardware you have is correctly listed in UEFI/BIOS.

UEFI uses the GUID/partUUID of the ESP partition to know where to find the .efi boot files.
You can see partUUIDs of partitions with, part UUID of ESP must match UUID in UEFI boot entry.:
lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

Then grub has boot files shimx64.efi and grubx64.efi for booting  in ESP. Ubuntu also then has a three line grub.cfg to configfile(chain) to full grub.cfg in one of your installs specified by UUID. I have edited that grub file to change which is default boot or first in grub menu.
cat /boot/efi/EFI/ubuntu/grub.cfg


```
fred@Z170N-focal:~$ ll /boot/efi/EFI/ubuntu
total 4192
drwxr-xr-x 2 root root    4096 Jan 12  2020 ./
drwxr-xr-x 5 root root    4096 Apr 10  2020 ../
-rwxr-xr-x 1 root root     108 Jan 12  2020 BOOTX64.CSV*
-rwxr-xr-x 1 root root     117 Jan 12  2020 grub.cfg*
-rwxr-xr-x 1 root root 1668984 Jan 12  2020 grubx64.efi*
-rwxr-xr-x 1 root root 1269496 Jan 12  2020 mmx64.efi*
-rwxr-xr-x 1 root root 1334816 Jan 12  2020 shimx64.efi*


```

---

### Post by helen314 on 2020-10-11
/boot/efi/EFI/ubuntu

Is this the mystery file as seen in UEFI ?
I do not have a permission to get into  /boot/efi directory . i'll work on that. 


Aa far as grub versus grub2 I vaguely recall , few years  back, that there is a file "converting " grub name to grub2. 


I am not sure why my vendor's specific UEFI setup has "BBS"  as option. 

I am making sure none of the "new hardware" is UEFI, no more BIOS !


There is a definite issue with USB options, still working on UEFI version update, - since I run my mouse on USB one setup will turn my mouse off ! 
Very nice !!

---

### Post by oldfred on 2020-10-11
Many old BIOS and newer UEFI have settings where you have to turn on or allow USB ports or boot or both.

Back 10 years ago, it was a conversion program that installed grub2 when using grub and you could then fully convert if grub2 worked.
I do not think old grub legacy even works with UEFI.

Almost all UEFI systems have CSM mode for BIOS boot. That was also for backwards compatiblity and use with older systems where large corporations may have mixed BIOS and newer UEFI hardware.
It is just about to the point of eliminating BIOS and the extra complications it causes. Early UEFI had lots of issues, both by vendors UEFI and hardware implementation and grub/kernel on booting.

Before 14.04 the mount of the ESP used defaults. Since then they have changed to use 0077, which is no permissions at all. Probably for security reasons, but I change my mount. And Boot-Repair still updates fstab with new entry. In future may have to change back and only use live installer or have an install with permissions but default boot install without permissions.

```
# /boot/efi was on /dev/sda1 during installation
14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat    defaults        0       1
16.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    umask=0077      0       1

```

---

