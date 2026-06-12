---
title: "Stuck in 'Grub rescue&gt;' - please help"
date: 2017-07-23
forum: General Help
---

### Post by linuxuser2017 on 2017-07-23
Hi,

I have used Ubuntu for a while, but only as a user.  So, I don't know anything about the deep stuff.

I have an old Acer Netbook on which I have Windows XP, and Ubuntu (I think version 8.??).  I ended up at **'Grub rescue>**' somehow, and am not able to proceed.
I looked around on the forum and saw that I need to provide the output of boot info script. 
I booted with Bodhi Linux on a USB, and then downloaded the boot info script. 
I am including the** output of boot info script  below**.
I would appreciate it if someone could please help me to restore my old dual-boot screen (Windows and Linux).  If that is not possible, I am willing to install a later version of Ubuntu, but I would appreciate it if I could retain the WindowsXP.  If not, that is fine too.  I have a 'rescue' partition for WindowsXP, from which I can restore WindowsXP hopefully.

[B]Acer AspireOne - Windows XP,  1 GB/250GB 

[/B]If you need any other info, please let me know.
Thanks for any help.

--

                   ```
Boot Info Script 0.61      [1 April 2012]



============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       183951352 sectors, but according to the info from 
                       fdisk, it has 183957503 sectors.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr


sda3: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 


sda5: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 debian-20101222 ...........>...s>.......c.)....0...~.~...~...f...M.f.f....f..8~....>E}
    Boot sector info:  Syslinux looks at sector 752656 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________
Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                  63    23,069,339    23,069,277  12 Compaq diagnostics
/dev/sda2    *     23,070,720   207,028,223   183,957,504   7 NTFS / exFAT / HPFS
/dev/sda3         207,030,270   312,576,704   105,546,435   5 Extended
/dev/sda5         308,174,958   312,576,704     4,401,747  82 Linux swap / Solaris




Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 1.9 GiB, 2051014656 bytes, 4005888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *             32     3,998,399     3,998,368   b W95 FAT32




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        084008084007FAE8                       ntfs       PQSERVICE
/dev/sda2        123E5AEE3E5ACA7D                       ntfs       ACER
/dev/sda5        5681e88c-6e61-480f-9ab0-713f271cd743   swap       
/dev/sdb1        5024-F85B                              vfat       PENDRIVE


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)




================================ sda2/boot.ini: ================================


--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------


=========================== sdb1/boot/grub/grub.cfg: ===========================


--------------------------------------------------------------------------------


if loadfont /boot/grub/font.pf2 ; then
  set gfxmode=auto
  insmod efi_gop
  insmod efi_uga
  insmod gfxterm
  terminal_output gfxterm
fi


set default="0"
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
set_background_image "/isolinux/splash.png"
set timeout=7


menuentry "UEFI Boot Bodhi Linux Live Disc" {
  set gfxpayload=keep
  linux /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
  initrd  /casper/initrd.lz
}
#~ # New entry:  ERROR - boots to black screen in VirtualBox
#~ menuentry "Bodhi in safe mode" {
  #~ linux /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper xforcevesa quiet splash
  #~ initrd /casper/initrd.lz
#~ }
#~ # New entry:  ERROR - does not boot into cli
#~ menuentry "Bodhi CLI" {
  #~ linux /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper textonly quiet splash
  #~ initrd /casper/initrd.lz
#~ }
menuentry "Check disc for defects" {
  set gfxpayload=keep
  linux /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
  initrd  /casper/initrd.lz
}
#~ # New entry:  ERROR - /boot/memtest86+.bin not found
#~ menuentry "Memory Test" {
  #~ linux16 /boot/memtest86+.bin
#~ }
#~ # New entry:  ERROR - 
#~ menuentry "Boot from the first hard disk" {
  #~ set root=(hd0)
  #~ chainloader +1
#~ }
--------------------------------------------------------------------------------


============================== sdb1/syslinux.cfg: ==============================


--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100


label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/custom.seed boot=casper quiet splash --


label ubnentry0
menu label live - legacy boot the Live System
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/custom.seed boot=casper  quiet splash --


label ubnentry1
menu label xforcevesa - legacy boot Live in safe graphics mode
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/custom.seed boot=casper nomodeset xforcevesa  quiet splash --


label ubnentry2
menu label memtest - Run memtest
kernel /install/memtest
append initrd=/ubninit -


label ubnentry3
menu label check - check distro integrity
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --


label ubnentry4
menu label hdVB - boot first hard disk (VirtualBox)
kernel /isolinux/chain.c32
append initrd=/ubninit hd0 0


label ubnentry5
menu label UEFI Boot Bodhi Linux Live Disc
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --


label ubnentry6
menu label Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --


--------------------------------------------------------------------------------


=================== sdb1: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




================= sdb1: Location of files loaded by Syslinux: ==================


           GiB - GB             File                                 Fragment(s)




============== sdb1: Version of COM32(R) files used by Syslinux: ===============


 menu.c32                           :  COM32R module (v4.xx)


=============================== StdErr Messages: ===============================


xz: (stdin): Compressed data is corrupt
cat: /tmp/BootInfo-OKQeHEIb/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-OKQeHEIb/Tmp_Log: No such file or directory
```

---

### Post by oldfred on 2017-07-23
Please use code tags, # in advanced editor
Easy to add with Forum's advanced Editor and # icon.

You show a wubi install which is not supported anymore. but you have grub in MBR and lots of space in extened partition that looks like a missing partition.
Did you do some Windows updates. Windows for years has a bug (they think it is a feature?) that forgets to write a Linux partition back into the extended partition. But partition is still there.
Some have been able to just restore partition and grub boots, but most have to reinstall grub also.

You can use testdisk or parted rescue, but be sure to use newer live installer. But I think issue is the same as these newer versions of Windows.
Do not know about Bodhi. Suggest Lubuntu or Xubuntu.

 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462) 

      
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by linuxuser2017 on 2017-07-23
**oldfred**, thanks for your response.
Unless I misunderstand what you mean by 'code tags', I had actually added the tags 'dual-boot' and 'WindowsXP' when submitting the above question, but I don't see them.  After reading your response, I tried to edit my post and then go into advanced editor, but I don't see a field to post tags ( as I had seen earlier). If that is not what you mean, then I didn't quite understand where I should use the "#" (ie which part of my post).  Sorry about this - I feel like an idiot for not being able to do this. 

**Edit**:  Oh, I got it now.  The output of the boot info script should have been in code tags.  I see that you have done that but it did not occur to me earlier.  Thanks.

After reading this link ([https://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue](https://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue)), I realized that I had also chosen the wrong boot option (**Windows recovery environment**).  But I exited out of it (by clicking on the 'Exit' link).    In that post (link in the previous sentence), and some other posts, they talk about using commands such as the following:
```
set root=**(hd0,6)**
set prefix=**(hd0,6)**/boot/grub
insmod normal
normal
```

But, I am not able to figure out if I should also use "6" as above, or some other number as in other posts.  I didn't want to further complicate the situation I am in, so I have not tried it.

I have downloaded lubuntu iso and can make a bootable USB to boot from it if you want me to try something specific using that.

Thank you

---

### Post by oldfred on 2017-07-23
You are missing the Ubuntu partition, so manual boot will not work.
And your update was what caused Windows to rewrite partition table, and it left off your Linux partition in the extended.

You need to use testdisk or parted rescue to see if you can recover missing partition. Not sure if those are on the live installer Bodhi, you have as not familiar with it.
With Lubuntu live installer, any of the several threads posted above discuss recovery of a partition. I just posted several as some explain it a bit more, or somewhat differently which may then help.

You really should update to newest Ubuntu. My 10 year old laptop (XP) was retired with 12.04 and since it only had 1.5GB of RAM had to use fallback as Unity required better system. But I just for fun installed 16.04 and Unity was usable (but not fast) where before it was just way too slow. So newer versions have improvements that help even older systems.

You highlight anything with mouse and click # to add code tags before & at end of highlighted text.
 How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

---

### Post by linuxuser2017 on 2017-07-23
**oldfred**, thank you.  So, I take it that executing commands like [FONT=courier new]'set root=(hd0,6[/FONT])' is not possible for the reasons you mentioned.  For whatever its worth, when I do [FONT=courier new]'ls[/FONT]', I see:
**[FONT=courier new](hd0), (hd0,msdos5), (hd0,msdos2), (hd0,msdos1)[/FONT]**, but when I do [FONT=courier new]'**ls (hd0,msdos1)/**'[/FONT] I get "*error: unknown filesystem*'.

Thank you for the instructions on highlighting and using code tags, and the links.  I  appreciate it.
Also, thanks for telling me that 16.04 is faster than 12.04  I will try installing 16.04.  I have only 1GB.  Not sure if it would be worth spending to upgrade to 2 GB.  

I booted from **lubuntu USB** and chose **'boot from first hard disk'** but it did not work - it stopped in (**initramfs**).  Prior to that I see:
[B]mount: mounting /dev on /root/dev failed: No such file or directory
[FONT=courier new]No init found.  Try passing init=bootarg

[/FONT][/B][FONT=courier new]
However, if I do 'ls' at the (initramfs) prompt, I see:
[B]dev  lib   lib64   bin  run  etc  ... root  conf   var   usr ....
[/B]
[/FONT]I can also do a 'cd' into 'dev' and see a bunch of files.  But there is nothing inside the 'root' dir above.  

Do you think, instead of spending time with learning how to use testdisk or parted, I should just create a USB from the 16.04 iso and install from it?  Or are they two different things? 

Thank you

---

### Post by linuxuser2017 on 2017-07-23
**oldfred**,  I tried parted and testdisk, and must have screwed up something else.  Earlier, I actually did see a partition with 'Linux' mentioned.  But I tried to set primary bootable in the hope that I can boot with Windows and then rebooted, but it still ended up in 'Grub rescue>'.  Obviously, I don't understand these things properly and I am just groping in the dark.  Now, I have ended up with the following:  (output of testdisk).  (Earlier I mentioned that I have a 250GB disk.  That seems to be wrong and I have only a 160GB disk)

```
[B]Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  1435 254 63   23069277
[/B]
```

Do i now do the following steps mentioned in ([https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)) **parted rescue**?  If so, what should I specify for the **Start** and **End** values when it prompts?

Thank you

---

### Post by oldfred on 2017-07-23
Grub does not use Boot flag.
Windows has to have boot flag on the primary NTFS partition with the Windows boot files.
So move boot flag back to sda2.

These were your partitions:
```
/dev/sda1                  63    23,069,339    23,069,277  12 Compaq diagnostics
/dev/sda2    *     23,070,720   207,028,223   183,957,504   7 NTFS / exFAT / HPFS
/dev/sda3         207,030,270   312,576,704   105,546,435   5 Extended
/dev/sda5         308,174,958   312,576,704     4,401,747  82 Linux swap / Solaris

```

Note large gap from 207,030,270 or start of extended partition and 308,174,958 or start of swap.
Those are where missing partition was.
Now if others are missing, it is a bigger issue. I looks like you only left your Compaq diagnostics partition?
Partition table can be rebuilt.

Testdisk shows every version of partitions you may have had. So if changed multiple times you have multiple configurations.
You have to select non-overlapping version that matches what you want or had.

---

### Post by linuxuser2017 on 2017-07-24
**oldfred**, yes, I see only partition shown as (* HPFS - NTFS) in my earlier update.   Yes, so probably Compaq diagnostics is the only one left.  I am afraid that I may have even lost the recovery disk/partition for Windows.   I am very confused at this point ("half knowledge is dangerous" which landed me in this situation).  If possible, could you please tell me what should be my next step?

I booted the netboook with Ubuntu 16.04 on a USB.  And ran Gparted and wanted to include the screenshot, but since I have only 1 GB RAM, it seems to be freezing in Firefox when I try to open this site.  If such a screenshot will be useful, I will try to figure out how to copy to another USB and then post it to the forum from another computer.

Thanks

---

### Post by oldfred on 2017-07-24
Gparted does not really show more than your partition list already posted.
It probably only shows the one partition, now?

Gparted is the gui for parted, and some have posted using it for partition recovery. Have not tried nor know about it, but if you have gparted see what it has in its menu.

If you cannot get parted rescue, testdisk, or gparted to find your old partitions, it is possible to create a file that is your partition table & load that. 
I really should have had you make a backup of your original (but not complete) partition table, but thought so many had posted using testdisk or parted rescue to just recover the one missing partition that is what you would do.

Examples, which I can help you with if absolutely non of the other fixes work.
 Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

### Post by linuxuser2017 on 2017-07-24
**oldfred**, it shows one partition as ** HPFS-NTFS** and the other one as '**unallocated**'.  (as seen in Gparted)

 I read through the link you included where caljohnsmith helped recover ([https://ubuntuforums.org/showthread.php?t=1036600](https://ubuntuforums.org/showthread.php?t=1036600)).  I *think* i have done the same thing mentioned in[ #8]("https://ubuntuforums.org/showthread.php?t=1036600&p=6532868#post6532868") of that posting. (I am quoting the relevant part from #8 here:** "Testdisk does not erase everything on the HDD, it merely changes the  HDD's partition table stored in the MBR (Master Boot Record) and the  partition tables in the EBRs (Extended Partition Records) associated  with each of the logical partitions. So all the data on the HDD is still  there, but it is just not easily accessible since the partition table  is currently invalid.")   **Could this be the case?   

Does it still make sense to  try** parted rescue**?  However, I am not clear on what I should specify as the **Start** and **End** values when it prompts.  Could you please tell me how to figure out what values to specify?  If parted rescue is not the right thing now, then I would appreciate it if you could help me as you mentioned at the end of your last response.  

BTW, I looked through the menus of Gparted, but I could not figure out which of the menu options, if any, are relevant.  I was looking for something like 'rescue' or 'recover' or 'undelete' or something to that effect.  But, to tell you the truth, I am now afraid to do anything on my own for the fear of making it unsalvageable. 

Thank you

---

### Post by oldfred on 2017-07-24
First try parted rescue.
The starts & ends are just the partitions shown from your BootInfoScript and I reposted in post #7.
Use each of numbers. One user said he had to use one sector before & one after, so if exact numbers shown do not work, try adjusting by one. But he may have just had partition before & after.
Try for each missing partition (I think it works, one at a time, not all at once) and try also for the space (original missing partition) between start of extended & start of swap.
If you do not recover swap that is ok, as easily recreated & edit of fstab with new UUID.

---

### Post by linuxuser2017 on 2017-07-25
OK, I will try parted rescue.   I am copying the last two entries from the partitions you posted in #7 because I have a couple of  questions.

**```
**[B]/dev/sda3         207,030,270   312,576,704   105,546,435   5 Extended
/dev/sda5         308,174,958   312,576,704     4,401,747  82 Linux swap / Solaris[/B][B]
```

 
1[/B]. I noticed that the **end** value is the same for **sda3** and **sda5**.  Is that strange?[B]
2.[/B] The partition **/dev/sda4** seems to be missing.  Is that what you mean by "[B][I]try also for the space (original missing partition) 
   between start of extended & start of swap[/I].[/B]"?  If so, what should be the value for **start** and **end** for the missing **sda4**?

Thank you

---

### Post by oldfred on 2017-07-25
You do not recover extended partition, it acts as a container for all  your logical partitions.
So the first logical partition normally starts a few sectors after the start of the extended and last logical partition ends at or just before end of extended partition.

Your swap was probably sda6 and the missing partition at beginning of extended was probably sda5.
All logical partition start at sda5. Partitions sda1 thru sda4 are primary partitions and any one of the primary partitions can be used as the extended partition.
It is ok for missing Linux partition to now be sda6 and its start is one or two sectors after the start of the extended and its end is a sector or two before the start of the swap partition. (If you only had one logical Linux partition).

Do parted rescue on sda2 and then post results.

---

### Post by linuxuser2017 on 2017-07-25
**oldfred**, I did parted rescue on sda2 as you said and here is the log. I looked at your other posting you had in the links ([https://ubuntuforums.org/showthread.php?t=1775331&page=3&p=10905805#post10905805)]("https://ubuntuforums.org/showthread.php?t=1775331&page=3&p=10905805#post10905805"), and did a sfdisk -l before and after doing the parted rescue.  

Does the output look OK?  If yes, what should I do next?  Thanks

```

ubuntu@ubuntu:~$ [COLOR=#0000cd]**sudo fdisk -l**[/COLOR]
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1497772032 bytes, 2925336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc006a2ce

Device     Boot Start      End  Sectors Size Id Type
/dev/sda1  *       63 23069339 23069277  11G  7 HPFS/NTFS/exFAT


Disk /dev/sdb: 1.9 GiB, 2051014656 bytes, 4005888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start     End Sectors  Size Id Type
/dev/sdb1  *       32 3998399 3998368  1.9G  b W95 FAT32
ubuntu@ubuntu:~$ pwd
/home/ubuntu
ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda > PT.txt
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA Hitachi HTS54501 (scsi)
Disk /dev/sda: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

[B]Number  Start  End        Size       Type     File system  Flags
 1      63s    23069339s  23069277s  primary  ntfs         boot[/B]

[B]ubuntu@ubuntu:~$ sudo parted
GNU Parted 3.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s                                                           
(parted) rescue                                                           
Start? [COLOR=#ff0000]23070720[/COLOR]                                                           
End? [COLOR=#ff0000]207028223[/COLOR]                                                            
searching for file systems... 49%       (time left 00:03)Information: A ntfs primary partition was found at 23070720s -> 207022071s.  Do
you want to add it to the partition table?
Yes/No/Cancel? yes
(parted) quit                                                             
Information: You may need to update /etc/fstab.[/B]

**ubuntu@ubuntu:~$ [COLOR=#0000ff]sudo fdisk -l[/COLOR]**
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1497772032 bytes, 2925336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc006a2ce

[B]Device     Boot    Start       End   Sectors  Size Id Type
/dev/sda1  *          63  23069339  23069277   11G  7 HPFS/NTFS/exFAT
/dev/sda2       23070720 207022071 183951352 87.7G  7 HPFS/NTFS/exFAT[/B]


Disk /dev/sdb: 1.9 GiB, 2051014656 bytes, 4005888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start     End Sectors  Size Id Type
/dev/sdb1  *       32 3998399 3998368  1.9G  b W95 FAT32
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 



```

---

### Post by oldfred on 2017-07-25
This is what we are trying to get to:
```
 /dev/sda1                  63    23,069,339    23,069,277  12 Compaq diagnostics
/dev/sda2    *     23,070,720   207,028,223   183,957,504   7 NTFS / exFAT / HPFS
/dev/sda3         207,030,270   312,576,704   105,546,435   5 Extended
/dev/sda5         308,174,958   312,576,704     4,401,747  82 Linux swap / Solaris 

```
The new end of sda2 is just a few sectors different. It may have been empty space or something else.
Windows will not be happy. You have to at least run chkdsk from Windows install disk or repair disk repair console(cannot do from Linux). And first move boot flag to sda2. Windows has to have the same partition start & size info in the PBR - partition boot sector as the partition table. And now they  are slightly different.

Try to recover the missing Linux partition. It may just make it sda3, but that also would be ok.
It should be between these sectors.

Start of extended 
 207,030,270 
Start of swap was
      308,174,958 

when you said you ran sfdisk was this what you did, and saved to another drive?

 sudo sfdisk -d /dev/sda > PT_sda.txt 
Run that again, or if run, that is ok, but post the data from inside that file. It should be start & size of partition, which is slightly different than start & end info normally seen.

---

### Post by linuxuser2017 on 2017-07-25
> **oldfred said:**
> 
The new end of sda2 is just a few sectors different. It may have been empty space or something else.
Windows will not be happy. You have to at least run chkdsk from Windows install disk or repair disk repair console(cannot do from Linux). And first move boot flag to sda2. Windows has to have the same partition start & size info in the PBR - partition boot sector as the partition table. And now they  are slightly different.


I am a bit confused about the sequence.  Should I first move the boot flag to sda2, then boot into Windows from it, and then run chkdsk?     Or, you mean that I won't be able to boot into Windows, so I would need a repair disk from which I should run chkdsk first, and then set the boot flag to sda2?

I don't have an external CD drive to connect to the Netbook.  I hope I can create a Windows repair disk  on a USB from some website.  If not, I will have to first get hold of an external CD drive and then proceed.

Also, how do I set the boot flag on sda2?  Should I use the following command?  But I couldn't figure out how to specify 'sda2' there.
[B][FONT=courier new](parted) disk_set pmbr_boot on

Edit: [/FONT][/B][FONT=courier new]Please ignore this question (how to set boot flag on sda2).  I found that in **Gparted**, there is a column for '**Flags**' and by right-clicking on it, I can choose '**Manage Flags**' for that particular partition.[/FONT]

> **oldfred said:**
> 
when you said you ran sfdisk was this what you did, and saved to another drive?
sudo sfdisk -d /dev/sda > PT_sda.txt 
Run that again, or if run, that is ok, but post the data from inside  that file. It should be start & size of partition, which is slightly  different than start & end info normally seen.


I forgot to save it to another drive, although your instructions in the other thread clearly said so.  So, now I have run it again and here is how it looks:

```
[B]label: dos
label-id: 0xc006a2ce
device: /dev/sda
unit: sectors

/dev/sda1 : start=          63, size=    23069277, type=7, bootable
/dev/sda2 : start=    23070720, size=   183951352, type=7[/B]
```

Could sda1 (bootable) be the recovery disk that came with the Netbook?

Thank you

---

### Post by oldfred on 2017-07-25
You want boot flag on sda2 as it was with your original listing.
Use gparted, and only have boot flag one one primary NTFS partition.
You can use command line, but since you have figured out gparted that is fine.

Windows only does repairs on NTFS partitions and only fixes boot on the NTFS partition with the boot flag.

As I copied in post #15, it now shows the size in sectors. And that is then the correct value.
[FONT=arial][SIZE=1]/dev/sda2 : start=    23070720, size=   [COLOR=#ff0000]183951352[/COLOR], type=7

Correct value. 183,957,504 
[/SIZE][/FONT]You can use any Linux editor and replace the red value with the correct value into the backup file, but without the commas.
Then restore that edited file to partition table. And that may make the Windows partition correct & bootable?

I am guessing at sizes and starts of sda5 & sda6, but final result should be close to this:
From review of old threads (now very old) I see new format has changed some. I only use gpt, not MBR(msdos) so cannot compare any of my sfdisk outputs.
```
/dev/sda1 : start=          63, size=    23069277,  type=7
/dev/sda2 : start=         23070720, size=   183951352, type=7, bootable
/dev/sda3 : start=       207030270, size=   105546435, type= f
/dev/sda5 : start=       207030272, size=   101144686, type= 83
/dev/sda6 : start=       308174958, size=      4401747,  type=82 
```

I would like you to keep trying to recover one partition at a time and them compare to above.
Only as last resort we could edit your backup to match above, but I have too many approx. values that may or may not work. Better to try recover first.

---

### Post by linuxuser2017 on 2017-07-26
oldfred, thank you.  I will try to recover first as you said.  I have a couple of questions:

1. After setting the boot flag on sda2, shall I try to reboot?  (without recovering other partitions)   
2. I found some sites which enable booting Windows XP from USB.  Shall I boot from such a Windows recovery USB and then run chkdsk before trying to boot from sda2?

Thank you

---

### Post by oldfred on 2017-07-26
With BIOS/MBR only one boot loader is in MBR. 
You can temporarily restore a Windows boot loader and see if sda2 will boot.
But you may need to run chkdsk from Windows or Windows repair disk. Do not remember if XP would boot into a recovery mode & let you run chkdsk or not.

I have not used XP for about 5 years. But did have to run chkdsk. But my Windows 7 repair disk ran a better chkdsk that fixed more issues, but created a new issue. NTFS partition have in the PBR - partition boot sector code for booting. The Windows boot loader in MBR jumps to PBR of partition with boot code. With XP the ntldr is referenced in PBR, but Windows 7 & later uses bootmgr. So I had to run another set of repairs to fix PBR and convert back to XP(ntldr) type of PBR.

I am pretty sure the sda3 & sda6(was sda5 in all your posts) is correct as the start & sizes were in your partition listing. Only the Linux partition sda5 (was missing) is an estimate. But start is most important. Often start is just a couple of sectors after start of extended, but it may not be. End may not be critical as often just unused space, anyway. 
You could edit your partition table file & restore it just to see if it works.

see
man sfdisk
       sudo sfdisk --no-reread -f /dev/sda -O PTsda.save < PTsda.txt
"--no-reread" means don't check if disk is unmounted
-f force
"-O PT.save" means save a backup of original partition table in PT.save. PT.save is in binary format.

---

### Post by linuxuser2017 on 2017-07-26
I set the **boot** flag on **sda2** using Gparted (and removed the boot flag from sda1).   In Gparted, it showed an exclamation mark in a red circle in the left-most column for sda2 (it was so even before I set the boot flag on sda2).  I am assuming this has to do with what you had mentioned earlier - ie the sda2 is not quite set to the original limits.

When I tried to reboot (without the USB live CD), I ended up again with the **'Grub rescue**>' prompt.

In your last response, you mentioned '**PTsda.txt'**.  The PT.txt I had got as an output of **sfdisk -d**  had only two lines (as seen at the bottom of #16).  Should I use these two lines or should I created a PTsda.txt with the values in your #15?  If I do the steps in your last response (trying to restore the partition table), and if it works, will it automatically get rid of the 'grub rescue>' prompt, or will I need to update the Grub as I have seen in some postings?

It looks like it is going to take some for me to create the USB recovery disk as I will need to create it from my old Windows XP CDs (don't even know where they are now - need to search).  


Thank you for your patience.

---

### Post by oldfred on 2017-07-26
I would start with your backup of the partition table. The name can be anything.
Make a copy of that file & edit the copy and use whatever name you use as the filename to import. The < means to copy from a file. Example happened to use PTsda.txt, but that is just an example.

There are some third party Windows repair disks that may include chkdsk. And I think the free download of Windows 10 has the repair/recovery console and can be used for free for at least 30 days. But it may convert PBR. Then you have to use bootsect.exe to fix PBR.
       How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later 
    
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 

You can use Boot-Repair in your Ubuntu installer (if current version) to restore a Windows type boot loader to MBR. And then use it to restore grub to MBR after restoring the Linux partition.

---

### Post by linuxuser2017 on 2017-07-27
**oldfred**,  thank you very much for explaining everything patiently again and again.  I really appreciate it.  I am sorry that I am unable to understand even the basics so I have to ask questions again and again.
I will try to do chkdsk and/or boot-repair and then post here again.  Just wanted to let you know that this may take some time.

Thank you

---

### Post by oldfred on 2017-07-27
If the NTFS partition is restored, but still need chkdsk you may get mount errors from Linux.
But if otherwise ok, you may be able to mount read only and see if it is ok.

       Manual mount read only may work to copy data
sudo mount -o ro /dev/sda2 /mnt
or, but may have to make mount point /media/windows, /mnt is already a mount point.
sudo mount -t ntfs-3g -o ro /dev/sda2 /media/windows

---

### Post by linuxuser2017 on 2017-07-27
You are right, I am able to mount the NTFS partition manually and see the files in it. =d>
Among the many files, I can see the **ubuntu** directory and the **WINDOWS** directory and  also the files **wubildr** and **wubildr.mbr**.  Don't know if anything can be done with these.

Here is my latest partition table:

```
Model: ATA Hitachi HTS54501 (scsi)
Disk /dev/sda: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

[B]Number  Start       End         Size        Type     File system     Flags
 1      63s         23069339s   23069277s   primary  ntfs
 2      23070720s   207022071s  183951352s  primary  ntfs            boot
 3      207029718s  308174893s  101145176s  primary  ext4
 4      308174958s  312576693s  4401736s    primary  linux-swap(v1)[/B]

label: dos
label-id: 0xc006a2ce
device: /dev/sda
unit: sectors

[B]/dev/sda1 : start=          63, size=    23069277, type=7
/dev/sda2 : start=    23070720, size=   183951352, type=7, bootable
/dev/sda3 : start=   207029718, size=   101145176, type=83
/dev/sda4 : start=   308174958, size=     4401736, type=82[/B]
```


Now, should I try to reinstall **grub**, or should I try to do **fixmbr**?    Sorry, confused about these.  

BTW,when I booted using Live USB, I chose 'Check disc for defects', and it returned with 'no defects' found.  Since the test finished in about 2-3 minutes, I was wondering if it did the check on the USB files itself rather than the hard disk.


Thank you.

---

### Post by oldfred on 2017-07-27
If you can see your file, backup anything you might want to save, before doing anything else.
You shoud always have good backups.
Also make sure you have the backup of this partition table, so it could be restored in case of further issues.
Are all these partitions from parted rescue or editing the sfdisk file?

It converted your two logical partitions into primary partitions and then you cannot add any more partitions as with MBR there is a 4 primary partition limit. You have to have an extended partition, and then can have many logical partitions inside the extended. We could convert back to logical, but at this point I am glad to see you have partitions.

I do not think Windows will boot without chkdsk or perhaps other repairs. Grub really only boots working Windows, so I would temporarily install a Windows boot loader with either Boot-Repair or your Windows repair disk. And run chkdsk. And see if Windows boots.

I would also reinstall grub, although there is a slim chance that grub would still boot. But I think you may still have issues as start of ext4 partition is now a few sectors before where it must have been. Not sure then if fsck from Ubuntu live installer  will update it, and a reinstall of grub or if we have to attempt to move partitions slightly by editing your new saved sfdisk file.

---

### Post by linuxuser2017 on 2017-07-28
The partitions are from **parted rescue** (not from editing the sfdisk file).

I had already backed up the files on the Linux partition recently (before this situation arose).    I will backup any important files from Windows.  

I was wondering if it would be possible (and more convenient) to boot from the Windows rescue partition and restore Windows from there in case there are problems with the chkdsk.  And the linux install can be a fresh one (using the 16.04 release).   In other words, I don't mind losing the Windows and Linux that are on it now, but if possible, would like to save the Windows rescue partition.  I think I have a backup of that too, but it is a bit of a problem using that since I will need to borrow an external CD drive to read that backup.

I will try to use Boot-Repair first since that would be easier than making a Windows repair disk/usb.   It is all a bit mystery to me why the partition table is not the same as before in spite of specifying the start and end values from it when I ran parted rescue.

Thank you

---

### Post by oldfred on 2017-07-28
If you have nothing in Linux, it would have been a lot easier just to have reinstalled it in the unallocated space you originally had.

Running the Windows rescue will typically erase the Linux partitions. One of the most common questions we get.

So it depends on what you want? You could still edit the sfdisk file with same start & end values and it then may not need chkdsk.

Actually we do not recommend anyone run obsolete software particularly Windows XP or Vista. Nor old versions of Ubuntu. 
With Windows you just might as well post all your confidential info in plain text on the Internet as XP is not secure.

---

### Post by linuxuser2017 on 2017-07-29
Points taken re old versions.  Thank you.  The only reason I have XP on it is that I can print things from it on an old HP printer.   When i print from Ubuntu (8.??) it prints faster than from XP, but it somehow doesn't print the same font size, and the Excel formatting is screwed up for some reason (since I use OpenOffice on Ubuntu, but it also happens with PDF, which is surprising).  Also, scanning from the  HP printer-scanner is faster by  using Ubuntu (SimpleScan) but, it only scans in black-and-white.  I just haven't figured out ways around this, so at times I go back to XP to deal with these issues, else I always use Ubuntu.  

**Update** - I** installed Boot-Repai**r after booting from live USB (16.04) and chose the "**recommended repair**" option, after which it tried to repair **/dev/sda3 (only**), but then it seems to have got stuck in creating a boot info summary.  It says- "**Create a Bootinfo summary.  This may require several minutes**'.  It has been over an hour. I don't know if i can/should try to interrupt it, or it will damage the HD.

**Update 2** - After letting it spin for over 4 hours and still being stuck in that state, I had to forcibly power off as I could not get to stop it (ctrl-c, ctrl-d did not work, and when i tried to bring up 'term', it just appeared to freeze, presumably because there isn't enough memory).  I booted again with live USB, installed **boot-repair** again and this time chose the option of creating **boot-info**.  It said it will create a pastebin URL, but it did not create a URL and showed me the output in an editor, which I then saved to an other USB drive.  I am copy-pasting the lines that looked relevant (the beginning and the end summary).  If you wish to see the entire output (650 lines), I will copy it to pastebin.

```

Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 debian-20101222 ...........>...s>.......S......0...~.~...~...f...M.f.f....f..8~....>E}
    Boot sector info:  Syslinux looks at sector 3182272 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    23,069,339    23,069,277   7 NTFS / exFAT / HPFS
/dev/sda2    *     23,070,720   207,022,071   183,951,352   7 NTFS / exFAT / HPFS
/dev/sda3         207,029,718   308,174,893   101,145,176  83 Linux
/dev/sda4         308,174,958   312,576,693     4,401,736  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 1.9 GiB, 2051014656 bytes, 4005888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     3,998,399     3,998,368   b W95 FAT32


[... *more output from boot-info not included in the interest of space* ...]

No OS or WinEFI system


=================== Suggested repair
[COLOR=#ff0000][B]The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems  fix-windows-boot
[/B][/COLOR]

=================== Final advice in case of suggested repair


[COLOR=#ff0000][B]A broken Wubi has been detected. Please fix it this way:
https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu[/B][/COLOR]


=================== User settings
The settings chosen by the user will not act on the boot.


```

I looked up the URL in the '**suggested repair**' section of the output, and found that I will have to **boot into Windows and run chkdsk**.  If that doesn't work, it asks to check if there is  **C:\ubuntu\disks\root.disk** file  and if not, then it suggests some more steps.

I checked c:\ubuntu\disks **without** running chkdsk and did not find a root.dsk.  I don't know if running chkdsk will restore the root.dsk if there was one before, or I will have to go ahead and do the steps its asks to do if this file is missing.

I will try to boot into Windows and run chkdsk and then post an update.

---

### Post by oldfred on 2017-07-29
The root.disk is from wubi. You were not still using the wubi install were you?
Since you had a full install with grub booting, I assumed you did not use wubi.
Wubi runs inside the NTFS partition and uses the Windows boot loader, not grub.

Wubi was last available with 12.04 and is obsolete.
 Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)
[https://bugs.launchpad.net/wubi/+bug/1478239](https://bugs.launchpad.net/wubi/+bug/1478239) 

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by linuxuser2017 on 2017-07-29
I know this will sound really stupid, but sorry, I don't know which one I had (whether wubi or not).    I don't even remember what version of ubuntu i had.  I remember I had 8.?? initially, which I kept upgrading and then at one point the copying to usb or ext HD became painfully slow, so I I had reinstalled an older version.  I think I might have installed 8, and then either upgraded to 10, or I might have installed 10 directly.  Sorry, just not able to remember.  

Since I see wubildr and wubildr.mbr in sda2, I thought i might have had wubi.

If I am running through wubi, would I still get a boot menu with a choice of which OS to boot?  I used to see a boot menu where it would choose ubuntu by default.

---

### Post by oldfred on 2017-07-29
Grub in MBR, would have Ubuntu as first menu item.
Wubi adds a menu item to Windows boot menu. Those only booting Windows never see the Windows boot menu. If XP it is another entry in boot.ini, but Windows would be first in menu unless you manually changed it.

---

### Post by linuxuser2017 on 2017-07-30
OK. Thanks.  Sorry, I am not able to remember if I had changed it or not.  The (re)install of Ubuntu was done 6-7 years ago. Most likely I have grub in mbr and not wubi.

I was able to boot with  a  Windows rescue USB (using poweriso) after a lot of attempts with other software (such as unetbootin, isobuster and imgburn).  It is built with Windows PE 3.11 with Win 7 kernel (according to the instructions on how to build a Windows XP USB disk).    chkdsk showed some errors but was able to fix it (chkdsk /f).  If you wish to see the log, I will attach it here.  I ran chkdsk on c: and d: and now there are no errors.  It only shows the Windows partitions.  C: is the Windows XP install and D: is the recovery partition.  I am unable to get a screenshot, but here is the info I see.

Sorry about the formatting below. 
```

[B]Name                Type        Total size    Free space    File system

ACER (C:)            Local disk  87.7 GB        51.4 GB        NTFS
PQSERVICE (D:)         Local disk    11 GB          3.2 GB        NTFS
07_31_2017 (E:)       Removable    7.5 GB        6.8 GB        NTFS
Boot (X:)            Local disk    33.5 MB        31 MB        NTFS[/B]


```

I shut down, removed the pendrive and powered on, but it did not boot into Windows or show me a boot menu.   I still see the 'Grub rescue>' prompt.

I don't see any other utilities on the USB.  It did not boot into the blue screen and it did not prompt me to run recovery console.  So, I don't know if this USB rescue disk is much useful other than to let me see what is in C and D drives.

Should I try to run **fixmbr** now? I don't see it in any folder, but I can probably try to copy it from some other disk and get it to the netbook.

Thank you

---

### Post by oldfred on 2017-07-30
If you want to boot Windows you have to have the Windows boot loader in the MBR.
The fixMBR command should do that or Boot-Repair.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 

If you install a current version of Ubuntu that will reinstall grub to MBR. But grub only boots working Windows, so you need to make sure it boots before reinstalling Ubuntu.

---

### Post by linuxuser2017 on 2017-07-31
I will have to figure  out  how to get fixmbr to work (since it is only a part of the rescue mode), and currently, I am not able to boot in the rescue mode at present.  
I had tried Boot-Repair but it did its work on /dev/sda3 only.  (see update [#28]("https://ubuntuforums.org/showthread.php?t=2366917&p=13670994#post13670994"))  So, I can't quite know how to use Boot-Repair to fix the MBR.  It doesn't give a choice - there are only two buttons (1. recommended repair, 2. create boot-info).  I need to see if there is something in the advanced options.

---

### Post by oldfred on 2017-07-31
In advanced options should be the choice to choose an operating system and install a boot loader to a drive.
If it can see the Windows boot files in the NTFS partition then it should offer to install.
Since the official Windows boot loader is only allowed to be part of Windows, Boot-Repair installs syslinux boot loader to MBR which works just like the Windows boot loader.
You can also manually install syslinux bootloader to MBR, but be sure to only install the MBR part, not the full boot loader as that would corrupt the NTFS boot parts.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by linuxuser2017 on 2017-08-02
I tried** boot-repair** again.  The **MBR tab in Advanced** options was grayed out. After running boot-repair  it said that the boot was successfully repaired but when I restarted, I saw the 'Grub rescue>' prompt again.  I have not been able to use fixmbr from windows yet as I am not able to boot into windows recovery console (using the windows USB that I created).  I have pasted the **logs** of boot-repair to pastebin and have  included  the links below.   Should I still try to run fixmbr from windows when I can?   ie. I will try to borrow an ext CD drive and try to boot from the Windows backup CD and then fun fixmbr from rescue mode.  

[Boot-repair log ]("http://pastebin.ubuntu.com/25224654/")

Latest[URL="http://pastebin.ubuntu.com/25224649/"] boot-info

[/URL]

---

### Post by oldfred on 2017-08-02
Boot-Repair says it did not do anything.
And grub in MBR is looking for sda6 (msdos6) and your install is in sda4.

And Windows is corrupted as the Linux NTFS driver will not mount read/write if it needs chkdsk or is hibernated.
 ntfsfix /dev/sda2
Refusing to operate on read-write mounted device /dev/sda2. 

And if you ran ntfsfix before that may be the issue as it does not really fix much and turns on chkdsk flag so Windows will run chkdsk when booted. But then on reboot it is in needing chkdsk and cannot be mounted read/write.

You need to use Boot-Repair's advanced options and do a full uninstall/reinstall of grub. Just make sure Internet is working as then it has to download new copy of grub to reinstall.

And you need Windows tools to run chkdsk.

Not verified if these are still good:

 Partition Wizard -  boot CD or flash also, chkdsk & other Windows repairs
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html) 
   Third party chkdsk tools
Hiren's Boot CD, and do a chkdsk on the XP
[http://www.hirensbootcd.org/](http://www.hirensbootcd.org/)

---

### Post by linuxuser2017 on 2017-08-02
I had not noticed that (ntfsfix /dev/sda2 - refusing to operate on mounted device).  I just now booted with the Live Ubuntu (16.04) again and mounted the /dev/sda2 as per the commands you had given in a previous update.  I am still able to see the files on that partition.  So, I umounted and then mounted again with '-o rw' and then copied a text file to /mnt/windows and I am able to see the file on /dev/sda2.   So,* /dev/sda2 *seems ok.  I don't know why ntfsfix failed in Boot-Repair. After mounting manually, I again tried to run 'ntfsfix /dev/sda2' manually, but it gives me the same error message (Refusing to operate on read-write mounted device /dev/sda2).

Also, at the bottom of the same log ([http://pastebin.ubuntu.com/25224649/](http://pastebin.ubuntu.com/25224649/)) it says - '**Boot successfully repaired**'.  So that is also confusing.

---

### Post by oldfred on 2017-08-02
Even if you can mount the NTFS read only, the auto mount read/write is not working because of it needing chkdsk.
Forget about ntfsfix, it really do not do much, you need chkdsk.

This is what Boot-Repair says you chose:
=================== User settings
The settings chosen by the user will not act on the MBR.
Additional repair will be performed:  repair-filesystems  fix-windows-boot

So it tried to do ntfsfix, but failed. And then could not fix Windows boot.
But you did not select any grub fixes.

---

### Post by lisa85 on 2017-08-05
After numerous attempts to fix this issue, I unplugged all USB devices from my laptop, shut down my laptop and then everything booted perfectly.  Apparently my 32GB thumb drive was the culprit.

---

### Post by linuxuser2017 on 2017-08-08
**Update**:  Still no success with making a windows xp boot/repair USB.  Waiting to get access to an external CD drive.

---

