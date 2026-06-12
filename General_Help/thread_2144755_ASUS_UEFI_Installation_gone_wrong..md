---
title: "ASUS UEFI Installation gone wrong."
date: 2013-05-13
forum: General Help
---

### Post by bronson paul on 2013-05-13
[FONT=arial][FONT=times new roman, serif]Please help. I installed Ubuntu 13.04. on my ASUS UX32A. It gave me the option to install on the 24Gig SSD. I did it but it did not work so put it on the 500Gig drive it still wont work. I made a system image of recovery drive before hand. I have lost recovery partition and now seem to have Ubuntu on both drives I think.[/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif]I cant even get windows to re install.I get a blank Ubuntu color screen. [/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif]
[/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif]Im getting [/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif]
[/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif]fsck from util-linux 2.20.1[/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif]fsck from util-linux 2.20.1[/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif]dosfsk 3.0.14, 23 jan 2023, FAT32, LFN[/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif]/dev/sda2: clean, 168377/30269440 files, 2590830/121052672 blocks[/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif]/dev/sda1: 3 files, 241/189518 clusters[/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif][ 14.505872] FAT-fs (sda1): I0 charset iso8859-1 not found[/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif]mount: wrong fs type, bad option, bad superblock on /dev/sda1[/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif]            missing codepage or helper program, or other error[/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif]            in some cases useful info found in syslog - try[/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif]            dmesg | tail or so[/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif]
[/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif]mountall: mount /boot/efi [1119] terminated with status 32[/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif]mountall: filesystem could not be mounted /boot/efi[/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif]an error occured while mounting /boot/efi.[/FONT][/FONT]
[FONT=arial][FONT=times new roman, serif]keys:press s to skip mounting or M for manual recovery  [/FONT][/FONT]

---

### Post by fantab on 2013-05-13
Boot with Ubuntu DVD/USB and post the output of [BOOTINFO SCRIPT]("http://bootinfoscript.sourceforge.net/").

---

### Post by oldfred on 2013-05-13
Bootinfoscript is also run as part of Boot-Repair's BootInfo and with UEFI you will need Boot-Repair to make some fixes anyway.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Similar model that worked.
      
 Asus Zenbook Prime UX31A (UEFI)  Blank screen resolved by turning secure boot off, many tests of Boot parameters
[http://ubuntuforums.org/showthread.php?t=2086054](http://ubuntuforums.org/showthread.php?t=2086054)

---

### Post by jalirious on 2013-05-14
Hi, not to rub salt in the wound, but for me it runs fine (UX32A).

I installed 13.04, 64 bit.

If it helps, my setup was as follows. I have no interest in dual booting windows, but prefer to run it in a virtual machine if I have to.

(Incidentally, you can download a copy of your registered version of windows [here]("http://malwaretips.com/blogs/download-windows-7-sp1-iso/"), enter your license key (see sticker on your charger) and run a legal registered version on virtualbox or vmware)

Anyway, 1st make a bootable usb of 13.04.

Follow [this]("http://webent.altervista.org/2012/09/16/how-to-install-ubuntu-linux-12-04-or-newer-on-the-zenbook-ux32vd/") to start. I just clicked "Install Ubuntu" without further ado I should note. 

What would have helped me before would have been advice on partitioning.

I deleted every partition, leaving two nice empty discs.

/dev/sda (this is the 500 gb hdd)
/dev/sdb (this is the 24 gb ssd)

First, on /dev/sda (at the disk beginning) create a ~200 mb partition with /boot/efi as the file type
Then, on /dev/sda (at the end of the disk) create a 4 gb swap partition
Then, on /dev/sda, just before the swap partition create an (ext2 format) 6 gb /tmp partition
Then, on /dev/sda, use the rest of the disc for an ext4 /home partition 

Finally, install your root partition over the entire /dev/sdb disc (Use ext4 format and remember to set TRIM on your fstab after the installation).

Hope this helps, G'luck!

---

