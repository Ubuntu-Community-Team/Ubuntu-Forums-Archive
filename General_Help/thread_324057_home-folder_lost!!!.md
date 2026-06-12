---
title: "home-folder lost!!!"
date: 2006-12-23
forum: General Help
---

### Post by berggren on 2006-12-23
Major problem!!
Everything seems to be lost and I cant log in.
I come to the login-screen.
I type my name and password.
Then it says: There is no /home/peter -folder. and I'm back at the login-screen!
The only way to do anything is to login failsafe with the x-term.
When I do ls at root, I can see the home folder.
But when I try cd home it says: home is not a folder!

Is there any way to save my data?

My computer is a thinkpad t23 with a 30 GB disk.
The cause of the failure is probably that I was using 99% of the disk (300 MB free)

Peter.

---

### Post by kidders on 2006-12-23
Hi there,

It's hard to know what's happened without a little more detail. You could start by logging in as root, using a text only terminal (rather than X), and checking whether /home is mounted. Assuming it's not, see if you can find out why. Post the output of the following commands, and maybe there'll be an obvious solution...

[LIST]
[*]cat /etc/fstab
[*]mount
[*]ls -l /
[*]ls -l /home
[*]ls -l /dev/?d*
[/LIST]

**Edit:** Your dmesg might also contain useful information, but it's hard to say what to look for. Maybe we'll have a better idea after your next post :-)

---

### Post by melancholeric on 2006-12-23
Try booting from the liveCD and see if you can see the folder from there. Then backup somewhere if you can. Then remove stuff to get free space. Then reboot to see if that helped.

Linux doesn't exactly like too full hard drives.

---

### Post by kidders on 2006-12-23
> **melancholeric said:**
> Linux doesn't exactly like too full hard drives.That's certainly true! It can make a *terrible* mess! One advantage in working as root in such circumstances is that many filesystems reserve a small amount of space for use by the superuser, even though it appears there's none left.

---

### Post by berggren on 2006-12-23
Hi, and thanks for answering so fast!

> **kidders said:**
> 

...Post the output of the following commands, and maybe there'll be an obvious solution...

[LIST]
[*]cat /etc/fstab
[*]mount
[*]ls -l /
[*]ls -l /home
[*]ls -l /dev/?d*
[/LIST]



I had problems getting the output to a friends computer. But here it is. in order:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
----------------------------------------------------------------------------------------

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/fd0 on /media/floppy type ext2 (rw)
----------------------------------------------------------------------------

totalt 2160
drwxr-xr-x   2 root  root     4096 2006-11-29 01:31 bin
drwxr-xr-x   3 root  root     4096 2006-12-15 03:27 boot
lrwxrwxrwx   1 root  root       11 2006-10-11 10:43 cdrom -> media/cdrom
drwxr-xr-x  16 root  root    14980 2006-12-23 11:28 dev
drwxr-xr-x 118 root  root     8192 2006-12-23 12:47 etc
-rwxr--rwx   1 peter peter 2091612 2006-11-21 23:53 home
drwxr-xr-x   2 root  root     4096 2006-08-06 02:24 initrd
lrwxrwxrwx   1 root  root       29 2006-10-11 11:16 initrd.img -> boot/initrd.img-2.6.15-27-386
lrwxrwxrwx   1 root  root       29 2006-10-11 10:44 initrd.img.old -> boot/initrd.img-2.6.15-26-386
drwxr-xr-x  19 root  root     4096 2006-10-16 22:14 lib
drwxr-xr-x   2 root  root    49152 2006-10-11 10:43 lost+found
drwxr-xr-x   5 root  root     4096 2006-12-23 12:01 media
drwxr-xr-x   2 root  root     4096 2006-12-23 12:00 mnt
drwxr-xr-x   2 root  root     4096 2006-08-06 02:24 opt
dr-xr-xr-x  88 root  root        0 2006-12-23 11:27 proc
drwxr-xr-x  11 root  root     4096 2006-12-14 20:47 root
drwxr-xr-x   2 root  root     8192 2006-11-22 14:28 sbin
drwxr-xr-x   2 root  root     4096 2006-08-06 02:24 srv
drwxr-xr-x  10 root  root        0 2006-12-23 11:27 sys
drwxrwxrwt   6 root  root     4096 2006-12-23 11:30 tmp
drwxr-xr-x  10 root  root     4096 2006-12-23 10:15 usr
drwxr-xr-x  14 root  root     4096 2006-08-06 02:31 var
lrwxrwxrwx   1 root  root       26 2006-10-11 11:16 vmlinuz -> boot/vmlinuz-2.6.15-27-386
-------------------------------------------------------------------------------------------------------

-rwxr--rwx 1 peter peter 2091612 2006-11-21 23:53 /home
------------------------------------------------------------------------------------------------------

crw-rw---- 1 root audio   14, 12 2006-12-23 11:27 /dev/adsp
lrwxrwxrwx 1 root root        13 2006-12-23 11:27 /dev/fd -> /proc/self/fd
brwxrwxrwx 1 root floppy   2,  0 2006-12-23 11:27 /dev/fd0
brw-rw---- 1 root disk     3,  0 2006-12-23 11:27 /dev/hda
brw-rw---- 1 root disk     3,  1 2006-12-23 11:27 /dev/hda1
brw-rw---- 1 root disk     3,  2 2006-12-23 11:27 /dev/hda2
brw-rw---- 1 root disk     3,  5 2006-12-23 11:27 /dev/hda5
brw-r--r-- 1 root root     9,  0 2006-12-23 11:28 /dev/md0
brw-r--r-- 1 root root     9,  1 2006-12-23 11:28 /dev/md1
brw-r--r-- 1 root root     9, 10 2006-12-23 11:28 /dev/md10
brw-r--r-- 1 root root     9, 11 2006-12-23 11:28 /dev/md11
brw-r--r-- 1 root root     9, 12 2006-12-23 11:28 /dev/md12
brw-r--r-- 1 root root     9, 13 2006-12-23 11:28 /dev/md13
brw-r--r-- 1 root root     9, 14 2006-12-23 11:28 /dev/md14
brw-r--r-- 1 root root     9, 15 2006-12-23 11:28 /dev/md15
brw-r--r-- 1 root root     9, 16 2006-12-23 11:28 /dev/md16
brw-r--r-- 1 root root     9, 17 2006-12-23 11:28 /dev/md17
brw-r--r-- 1 root root     9, 18 2006-12-23 11:28 /dev/md18
brw-r--r-- 1 root root     9, 19 2006-12-23 11:28 /dev/md19
brw-r--r-- 1 root root     9,  2 2006-12-23 11:28 /dev/md2
brw-r--r-- 1 root root     9, 20 2006-12-23 11:28 /dev/md20
brw-r--r-- 1 root root     9, 21 2006-12-23 11:28 /dev/md21
brw-r--r-- 1 root root     9, 22 2006-12-23 11:28 /dev/md22
brw-r--r-- 1 root root     9, 23 2006-12-23 11:28 /dev/md23
brw-r--r-- 1 root root     9, 24 2006-12-23 11:28 /dev/md24
brw-r--r-- 1 root root     9,  3 2006-12-23 11:28 /dev/md3
brw-r--r-- 1 root root     9,  4 2006-12-23 11:28 /dev/md4
brw-r--r-- 1 root root     9,  5 2006-12-23 11:28 /dev/md5
brw-r--r-- 1 root root     9,  6 2006-12-23 11:28 /dev/md6
brw-r--r-- 1 root root     9,  7 2006-12-23 11:28 /dev/md7
brw-r--r-- 1 root root     9,  8 2006-12-23 11:28 /dev/md8
brw-r--r-- 1 root root     9,  9 2006-12-23 11:28 /dev/md9
brw-rw---- 1 root plugdev  8,  0 2006-12-23 11:27 /dev/sda
brw-rw---- 1 root plugdev  8,  1 2006-12-23 11:27 /dev/sda1

--------------------------------------------------------------------------------------

PS. I haven't got a live-cd here. I'll have to go home to test that.
Thanks, Peter

---

### Post by kidders on 2006-12-23
Oh hell. Much of what I requested was based on the assumption that you probably had your personal files on a dedicated partition, which doesn't seem to ever have been the case. In any case, as I'm sure is obvious to you, your /home directory seems to have been replaced by a 2MB file. This is very bad, because (assuming you can recover it at all, which is _very_ unlikely given the amount of space you say you've used up), you would more than likely lose all the filenames.

I fear you may not be able to get your lost data back, but we can at least try to figure out what happened, so it doesn't ever happen again. There are perhaps three possibilities:

[LIST=1]
[*]You overwrote the directory somehow or other ... I can't imagine how. Check your .bash_history for questionable references to /home.
[*]The filesystem is corrupted. fsck it and check /lost+found ... just in case.
[*]You've accidentally moved /home to another location. Type **find -iname** followed by the name of a file you know is in your /home, and nowhere else.
[/LIST]

Out of interest, what does **file /home** tell you? I find it hard to understand how this could have come about, especially given that you (and not root) seem to have acquired ownership of /home. Perhaps melancholeric will have something more positive to say.

---

### Post by berggren on 2006-12-23
Yes, my files are probably lost in, well, hell!

> **kidders said:**
> Oh hell. 

[LIST=1]
[*]You overwrote the directory somehow or other ... I can't imagine how. Check your .bash_history for questionable references to /home.
[*]The filesystem is corrupted. fsck it and check /lost+found ... just in case.
[*]You've accidentally moved /home to another location. Type **find -iname** followed by the name of a file you know is in your /home, and nowhere else.
[/LIST]

Out of interest, what does **file /home** tell you? say.

1. I didn't, I'm sure. But I used gthumb and nautilus to check pictures. And I uploaded a picture to my webmail. It was strange, but the cpu went to 100%, and because of that I turned off the computer. Normal, from within gnome. When I started ubuntu again, I couldn't reach my home-directory. Instead of the directory there is now a picture of my two cats. Very cute, but wrong place.
PS. How can I check .bash_history?

2.I did fsck. No problems. In /lost+found there is nothing.

3. No, there is no finding the files with find -iname

4. find /home gives  "JPEG image data, EXIF standard".

I've taken out the harddisk an put it in an external case and can now access it witth USB. So I can now look at it in nautilus with another ubuntu-machine. But there is no trace of my files in the old home-directory...

When I look at the properties of the disk, it says that only 300 MB are free, but when I check all the directories in it, they don't add upp to half that.

Peter.

---

### Post by bobpaul on 2006-12-23
> **berggren said:**
> 
4. find /home gives  "JPEG image data, EXIF standard".

I've taken out the harddisk an put it in an external case and can now access it witth USB. So I can now look at it in nautilus with another ubuntu-machine. But there is no trace of my files in the old home-directory...

When I look at the properties of the disk, it says that only 300 MB are free, but when I check all the directories in it, they don't add upp to half that.

In a case of obvious file system corruption like this, I like to make a backup of the partition onto a spare hard drive.

Do you have a computer with enough free space to fit your whole hard drive? Before we proceed you can make an image of your disk using ```
dd if=/dev/sd?1 of=drivebackup.img
```
where /dev/sd?1 is your root partition on the USB disk. ? needs to be replaced with the correct letter, such as /dev/sda1. If you aren't sure which letter the ? should be, you can check for mounted file systems using the mount command and determine the device name of your USB drive.

If you try something to attempt to recover your files that ends up damaging the filesystem further, you can restore from backup using ```
dd if=drivebackup.img of=/dev/sd?1
```

It seems to me that your filesystem still thinks all of your files exist, which is a good thing maybe and is demonstrated by the lack of freespace. However, your /home is now a jpeg image file rather than a directory node.

I think EXT3 has multiple (redundant) file allocation tables (map which data on the drive belongs to which files) so you might not be entirely up a creek without a paddle, but I honestly have no idea how to proceed. I just strongly encourage you backup now with dd, as it's saved my *** in similar situations.

---

### Post by bettlebrox on 2006-12-23
I'd suspect that your hard-drive is overheating or failing. Look at the output of dmesg and see if there are complaints about the drive.

U said you fsck'd the drive, but did you force a fsck to ensure it checked for bad-blocks and so on?

---

### Post by berggren on 2006-12-24
Merry Christmas! 

I do not think it's a hardware-problem with the harddrive, because everything else, apart from the home-dir is perfectly readable. But maybe I'm wrong, and such a circumscript failure is possible.

Here's the output from ls -l /media/usbdisk/
(the corrupted hd from my thinkpad is mounted as a usbdisk on a desktop)

---------------------------------------------------------------------------------------
peter@ubuntu-dell:~$ ls -l /media/usbdisk/
totalt 2176
drwxr-xr-x   2 root  root     4096 2006-11-29 01:31 bin
drwxr-xr-x   3 root  root     4096 2006-12-15 03:27 boot
lrwxrwxrwx   1 root  root       11 2006-10-11 10:43 cdrom -> media/cdrom
drwxr-xr-x   5 root  root     8192 2006-10-16 22:14 dev
drwxr-xr-x 118 root  root     8192 2006-12-23 14:02 etc
-rwxr--rwx   1 peter peter 2091612 2006-11-21 23:53 home
drwxr-xr-x   2 root  root     4096 2006-08-06 02:24 initrd
lrwxrwxrwx   1 root  root       29 2006-10-11 11:16 initrd.img -> boot/initrd.img-2.6.15-27-386
lrwxrwxrwx   1 root  root       29 2006-10-11 10:44 initrd.img.old -> boot/initrd.img-2.6.15-26-386
drwxr-xr-x  19 root  root     4096 2006-10-16 22:14 lib
drwxr-xr-x   2 root  root    49152 2006-10-11 10:43 lost+found
drwxrwxrwx   5 root  root     4096 2006-12-23 13:58 media
drwxr-xr-x   2 root  root     4096 2006-12-23 12:00 mnt
drwxr-xr-x   2 root  root     4096 2006-08-06 02:24 opt
drwxr-xr-x   2 root  root     4096 2006-05-22 16:00 proc
drwxr-xr-x  11 root  root     4096 2006-12-14 20:47 root
drwxr-xr-x   2 root  root     8192 2006-11-22 14:28 sbin
drwxr-xr-x   2 root  root     4096 2006-08-06 02:24 srv
drwxr-xr-x   2 root  root     4096 2006-05-21 20:46 sys
drwxrwxrwt   6 root  root     4096 2006-12-23 14:02 tmp
drwxr-xr-x  10 root  root     4096 2006-12-23 10:15 usr
drwxr-xr-x  14 root  root     4096 2006-08-06 02:31 var
lrwxrwxrwx   1 root  root       26 2006-10-11 11:16 vmlinuz -> boot/vmlinuz-2.6.15-27-386
peter@ubuntu-dell:~$
-------------------------------------------------------------------------------------------------------

And dmsg says:

peter@ubuntu-dell:~$ dmesg /media/usbdisk/
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001ff75000 (usable)
[17179569.184000]  BIOS-e820: 000000001ff75000 - 000000001ff77000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001ff77000 - 000000001ff98000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001ff98000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000fe710
[17179569.184000] On node 0 totalpages: 130933
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126837 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000feb90
[17179569.184000] ACPI: RSDT (v001 DELL    4550    0x00000006 ASL  0x00000061) @ 0x000fd4f6
[17179569.184000] ACPI: FADT (v001 DELL    4550    0x00000006 ASL  0x00000061) @ 0x000fd52e
[17179569.184000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0xfffd0a4e
[17179569.184000] ACPI: MADT (v001 DELL    4550    0x00000006 ASL  0x00000061) @ 0x000fd5a2
[17179569.184000] ACPI: BOOT (v001 DELL    4550    0x00000006 ASL  0x00000061) @ 0x000fd60e
[17179569.184000] ACPI: ASF! (v016 DELL    4550    0x00000006 ASL  0x00000061) @ 0x000fd636
[17179569.184000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 2392.547 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.968000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.972000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.980000] Memory: 508340k/523732k available (1976k kernel code, 14804k reserved, 606k data, 288k init, 0k highmem)
[17179571.980000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.060000] Calibrating delay using timer specific routine.. 4788.95 BogoMIPS (lpj=9577919)
[17179572.060000] Security Framework v1.0.0 initialized
[17179572.060000] SELinux:  Disabled at boot.
[17179572.060000] Mount-cache hash table entries: 512
[17179572.060000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000
[17179572.060000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000
[17179572.060000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179572.060000] CPU: L2 cache: 512K
[17179572.060000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00000400 00000000 00000000
[17179572.060000] mtrr: v2.0 (20020519)
[17179572.060000] CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 07
[17179572.060000] Enabling fast FPU save and restore... done.
[17179572.060000] Enabling unmasked SIMD FPU exception support... done.
[17179572.060000] Checking 'hlt' instruction... OK.
[17179572.076000] checking if image is initramfs... it is
[17179572.640000] Freeing initrd memory: 6617k freed
[17179572.656000] ACPI: Looking for DSDT ... not found!
[17179572.680000] ENABLING IO-APIC IRQs
[17179572.680000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.824000] NET: Registered protocol family 16
[17179572.824000] EISA bus registered
[17179572.824000] ACPI: bus type pci registered
[17179572.836000] PCI: PCI BIOS revision 2.10 entry at 0xfbe6d, last bus=2
[17179572.836000] PCI: Using configuration type 1
[17179572.836000] ACPI: Subsystem revision 20051216
[17179572.864000] ACPI: Interpreter enabled
[17179572.864000] ACPI: Using IOAPIC for interrupt routing
[17179572.872000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.872000] PCI: Probing PCI hardware (bus 00)
[17179572.872000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179572.884000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[17179572.884000] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[17179572.884000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179572.884000] Boot video device is 0000:01:00.0
[17179572.884000] PCI: Transparent bridge - 0000:00:1e.0
[17179572.884000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.920000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179572.940000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[17179572.940000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[17179572.940000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[17179572.944000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[17179572.944000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[17179572.944000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[17179572.944000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[17179572.944000] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)
[17179572.944000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.944000] pnp: PnP ACPI init
[17179572.976000] pnp: PnP ACPI: found 11 devices
[17179572.976000] PnPBIOS: Disabled by ACPI PNP
[17179572.976000] PCI: Using ACPI for IRQ routing
[17179572.976000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.988000] pnp: 00:0a: ioport range 0x800-0x85f could not be reserved
[17179572.988000] pnp: 00:0a: ioport range 0xc00-0xc7f has been reserved
[17179572.988000] pnp: 00:0a: ioport range 0x860-0x8ff could not be reserved
[17179572.988000] PCI: Bridge: 0000:00:01.0
[17179572.988000]   IO window: disabled.
[17179572.988000]   MEM window: fc000000-fdffffff
[17179572.988000]   PREFETCH window: e8000000-f7ffffff
[17179572.988000] PCI: Bridge: 0000:00:1e.0
[17179572.988000]   IO window: e000-efff
[17179572.988000]   MEM window: fe100000-fe2fffff
[17179572.988000]   PREFETCH window: disabled.
[17179572.988000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179572.988000] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[17179572.988000] Simple Boot Flag at 0x7a set to 0x1
[17179572.992000] audit: initializing netlink socket (disabled)
[17179572.992000] audit(1166956980.992:1): initialized
[17179572.992000] VFS: Disk quotas dquot_6.5.1
[17179572.992000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.992000] Initializing Cryptographic API
[17179572.992000] io scheduler noop registered
[17179572.992000] io scheduler anticipatory registered
[17179572.992000] io scheduler deadline registered
[17179572.992000] io scheduler cfq registered
[17179572.992000] isapnp: Scanning for PnP cards...
[17179573.344000] isapnp: No Plug & Play device found
[17179573.360000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[17179573.364000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.364000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.364000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179573.364000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.368000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.368000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 22 (level, low) -> IRQ 169
[17179573.368000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.368000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.368000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.368000] mice: PS/2 mouse device common for all mice
[17179573.368000] EISA: Probing bus 0 at eisa.0
[17179573.368000] EISA: Detected 0 cards.
[17179573.368000] NET: Registered protocol family 2
[17179573.392000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.404000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[17179573.404000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.404000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.404000] TCP: Hash tables configured (established 32768 bind 32768)
[17179573.404000] TCP reno registered
[17179573.404000] TCP bic registered
[17179573.404000] NET: Registered protocol family 1
[17179573.404000] NET: Registered protocol family 8
[17179573.404000] NET: Registered protocol family 20
[17179573.404000] Using IPI Shortcut mode
[17179573.404000] ACPI wakeup devices:
[17179573.404000] VBTN PCI0 USB0 USB1 USB2 PCI1  KBD
[17179573.404000] ACPI: (supports S0 S1 S3 S4 S5)
[17179573.404000] Freeing unused kernel memory: 288k freed
[17179573.452000] vga16fb: initializing
[17179573.452000] vga16fb: mapped to 0xc00a0000
[17179573.600000] Console: switching to colour frame buffer device 80x25
[17179573.600000] fb0: VGA16 VGA frame buffer device
[17179574.672000] Capability LSM initialized
[17179575.372000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179575.372000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179575.372000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 177
[17179575.372000] ICH4: chipset revision 1
[17179575.372000] ICH4: not 100% native mode: will probe irqs later
[17179575.372000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[17179575.372000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[17179575.372000] Probing IDE interface ide0...
[17179575.660000] hda: ST380021A, ATA DISK drive
[17179576.332000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.336000] Probing IDE interface ide1...
[17179576.736000] hdc: SAMSUNG DVD-ROM SD-616T, ATAPI CD/DVD-ROM drive
[17179577.184000] hdd: HL-DT-ST GCE-8481B, ATAPI CD/DVD-ROM drive
[17179577.240000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.248000] hda: max request size: 128KiB
[17179577.264000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179577.264000] hda: cache flushes not supported
[17179577.264000]  hda: hda1 hda2 hda3 hda4 < hda5 >
[17179577.304000] hdc: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[17179577.304000] Uniform CD-ROM driver Revision: 3.20
[17179577.304000] hdd: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.640000] usbcore: registered new driver usbfs
[17179577.640000] usbcore: registered new driver hub
[17179577.640000] USB Universal Host Controller Interface driver v2.3
[17179577.640000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179577.640000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179577.640000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179577.640000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179577.640000] uhci_hcd 0000:00:1d.0: irq 185, io base 0x0000ff80
[17179577.640000] hub 1-0:1.0: USB hub found
[17179577.640000] hub 1-0:1.0: 2 ports detected
[17179577.708000] ieee1394: Initialized config rom entry `ip1394'
[17179577.744000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
[17179577.744000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179577.744000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179577.744000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179577.744000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x0000ff60
[17179577.744000] hub 2-0:1.0: USB hub found
[17179577.744000] hub 2-0:1.0: 2 ports detected
[17179577.848000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 177
[17179577.848000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179577.848000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179577.848000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179577.848000] uhci_hcd 0000:00:1d.2: irq 177, io base 0x0000ff40
[17179577.848000] hub 3-0:1.0: USB hub found
[17179577.848000] hub 3-0:1.0: 2 ports detected
[17179577.952000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 201
[17179577.952000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179577.952000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179577.952000] ehci_hcd 0000:00:1d.7: debug port 1
[17179577.952000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179577.952000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179577.952000] ehci_hcd 0000:00:1d.7: irq 201, io mem 0xfe300000
[17179577.956000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.956000] hub 4-0:1.0: USB hub found
[17179577.956000] hub 4-0:1.0: 6 ports detected
[17179577.984000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179578.060000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179578.060000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 21 (level, low) -> IRQ 209
[17179578.108000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[209]  MMIO=[fe1ff800-fe1fffff]  Max Packet=[2048]
[17179578.240000] Attempting manual resume
[17179578.280000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.284000] kjournald starting.  Commit interval 5 seconds
[17179578.728000] usb 4-2: new high speed USB device using ehci_hcd and address 3
[17179579.284000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[17179579.388000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[005042a124146e3a]
[17179579.728000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17179591.108000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.116000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.256000] Linux agpgart interface v0.101 (c) Dave Jones
[17179591.268000] agpgart: Detected an Intel 845G Chipset.
[17179591.276000] agpgart: AGP aperture is 128M @ 0xe0000000
[17179591.516000] nvidia: module license 'NVIDIA' taints kernel.
[17179591.520000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179591.520000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179591.748000] Real Time Clock Driver v1.12
[17179591.768000] hw_random hardware driver 1.0.0 loaded
[17179591.820000] input: PC Speaker as /class/input/input1
[17179592.320000] SCSI subsystem initialized
[17179592.332000] Initializing USB Mass Storage driver...
[17179592.332000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179592.332000] usb-storage: device found at 3
[17179592.332000] usb-storage: waiting for device to settle before scanning
[17179592.332000] scsi1 : SCSI emulation for USB Mass Storage devices
[17179592.332000] usb-storage: device found at 3
[17179592.332000] usb-storage: waiting for device to settle before scanning
[17179592.332000] usbcore: registered new driver usb-storage
[17179592.332000] USB Mass Storage support registered.
[17179592.424000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179592.540000] Floppy drive(s): fd0 is 1.44M
[17179592.556000] FDC 0 is a post-1991 82077
[17179592.576000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x043D pid 0x0093[17179592.576000] usbcore: registered new driver usblp
[17179592.576000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179592.612000] usbcore: registered new driver hiddev
[17179592.624000] hiddev96: USB HID v1.00 Device [Lexmark Lexmark 5200 Series] on usb-0000:00:1d.1-1
[17179592.624000] usbcore: registered new driver usbhid
[17179592.624000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179592.664000] gameport: EMU10K1 is pci0000:02:02.1/gameport0, io 0xece8, speed 1065kHz
[17179592.768000] parport: PnPBIOS parport detected.
[17179592.772000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[17179592.832000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 18 (level, low) -> IRQ 177
[17179592.832000] Model 1003 Rev 00000000 Serial 10031102
[17179592.860000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[17179592.860000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179592.860000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 217
[17179592.884000] e100: eth0: e100_probe: addr 0xfe1fd000, irq 217, MAC addr 00:07:E9:B1:9E:D9
[17179593.880000] ts: Compaq touchscreen protocol output
[17179594.100000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179595.144000] NET: Registered protocol family 17
[17179595.176000] Intel ISA PCIC probe: not found.
[17179595.344000] lp0: using parport0 (interrupt-driven).
[17179595.404000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179595.404000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179595.404000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179595.464000] Adding 433712k swap on /dev/hda5.  Priority:-1 extents:1 across:433712k
[17179595.608000] EXT3 FS on hda3, internal journal
[17179595.772000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179595.772000] md: bitmap version 4.39
[17179596.284000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179596.660000] cdrom: open failed.
[17179597.096000] cdrom: open failed.
[17179597.096000] cdrom: open failed.
[17179597.336000]   Vendor: Creative  Model: NOMAD MUVO        Rev: 0100
[17179597.336000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[17179597.336000] usb-storage: device scan complete
[17179597.364000]   Vendor: HTS54804  Model: 0M9AT00           Rev: MG2O
[17179597.364000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179597.368000] usb-storage: device scan complete
[17179597.480000] Driver 'sd' needs updating - please use bus_type methods
[17179597.488000] SCSI device sda: 255040 512-byte hdwr sectors (131 MB)
[17179597.492000] sda: Write Protect is off
[17179597.496000] sda: Mode Sense: 03 00 00 00
[17179597.496000] sda: assuming drive cache: write through
[17179597.508000] SCSI device sda: 255040 512-byte hdwr sectors (131 MB)
[17179597.512000] sda: Write Protect is off
[17179597.512000] sda: Mode Sense: 03 00 00 00
[17179597.512000] sda: assuming drive cache: write through
[17179597.512000]  sda: sda1
[17179597.520000] sd 1:0:0:0: Attached scsi removable disk sda
[17179597.520000] SCSI device sdb: 78140159 512-byte hdwr sectors (40008 MB)
[17179597.520000] sdb: assuming drive cache: write through
[17179597.524000] SCSI device sdb: 78140159 512-byte hdwr sectors (40008 MB)
[17179597.524000] sdb: assuming drive cache: write through
[17179597.524000]  sdb:<6>NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179597.780000] NTFS volume version 3.1.
[17179597.904000]  sdb1 sdb2 < sdb5 >
[17179597.940000] sd 0:0:0:0: Attached scsi disk sdb
[17179597.992000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17179597.992000] sd 0:0:0:0: Attached scsi generic sg1 type 0
[17179598.128000] Buffer I/O error on device sdb5, logical block 3020152
[17179598.128000] Buffer I/O error on device sdb5, logical block 3020153
[17179598.128000] Buffer I/O error on device sdb5, logical block 3020154
[17179598.128000] Buffer I/O error on device sdb5, logical block 3020155
[17179598.128000] Buffer I/O error on device sdb5, logical block 3020156
[17179598.128000] Buffer I/O error on device sdb5, logical block 3020152
[17179598.128000] Buffer I/O error on device sdb5, logical block 3020153
[17179598.128000] Buffer I/O error on device sdb5, logical block 3020154
[17179598.128000] Buffer I/O error on device sdb5, logical block 3020155
[17179598.128000] Buffer I/O error on device sdb5, logical block 3020156
[17179598.644000] NET: Registered protocol family 10
[17179598.644000] lo: Disabled Privacy Extensions
[17179598.644000] IPv6 over IPv4 tunneling driver
[17179599.236000] ACPI: Power Button (FF) [PWRF]
[17179599.236000] ACPI: Power Button (CM) [VBTN]
[17179599.352000] ibm_acpi: ec object not found
[17179599.380000] pcc_acpi: loading...
[17179605.564000] ppdev: user-space parallel port driver
[17179608.576000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179608.576000] apm: overridden by ACPI.
[17179609.012000] Bluetooth: Core ver 2.8
[17179609.012000] NET: Registered protocol family 31
[17179609.012000] Bluetooth: HCI device and connection manager initialized
[17179609.012000] Bluetooth: HCI socket layer initialized
[17179609.024000] eth0: no IPv6 routers present
[17179609.048000] Bluetooth: L2CAP ver 2.8
[17179609.048000] Bluetooth: L2CAP socket layer initialized
[17179609.052000] Bluetooth: RFCOMM socket layer initialized
[17179609.052000] Bluetooth: RFCOMM TTY layer initialized
[17179609.052000] Bluetooth: RFCOMM ver 1.7
[17179629.936000] kjournald starting.  Commit interval 5 seconds
[17179629.936000] EXT3 FS on sdb1, internal journal
[17179629.936000] EXT3-fs: mounted filesystem with ordered data mode.
[17179913.584000] ibm_acpi: ec object not found
peter@ubuntu-dell:~$
----------------------------------------------------------------------------------------------------

> **bettlebrox said:**
> 
U said you fsck'd the drive, but did you force a fsck to ensure it checked for bad-blocks and so on?

I don't know how to do that (checking for bad-blocks), but here is the output from fsck:

peter@ubuntu-dell:~$ fsck /media/usbdisk
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
fsck.ext2: Är en katalog vid försök att öppna /media/usbdisk

Superblocket kunde inte läsas eller beskriver inte ett korrekt
ext2-filsystem.  Om enheten är giltig och den verkligen innehåller ett
ext2-filsystem (och inte växlingsutrymme eller ufs eller något annat)
är superblocket trasigt, och du kan försöka köra med ett alternativt
superblock:
    e2fsck -b 8193 <enhet>

peter@ubuntu-dell:~$

This is swedish an says approximately the following:

The superblock was not readable and doesn't describe a correct ext2-filesystem. If the disk really contains a ext2-system, then the superblock is corrupted. You could try an alternative superblock:
    e2fsck -b 8193 <unit>

Now there is something wrong here. Can I use this info to try something?

Thanks for trying to help, Peter.

---

