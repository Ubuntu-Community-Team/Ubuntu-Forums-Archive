---
title: "Can't get mount to appear in Computer"
date: 2008-04-22
forum: General Help
---

### Post by ninestories on 2008-04-22
One of my SATA drives has ceased to appear in the Computer (computer:///) window as a drive.  I've mounted the drive from /drv/sdb1/ to /mnt/drv/ but don't know how to get it to show up under the 'Computer' window.  All other drives (hard disks, CD-ROMs, USB drives) display correctly.

Thanks in advance.

--j.

---

### Post by Het Irv on 2008-04-22
Try remounting your drives
```
sudo mount -a
```

If that doesn't work please post your fstab file
```
 gedit /etc/fstab 
```

---

### Post by ninestories on 2008-04-22
Thank you for your suggestion.  Re-mounting the drives did not work.  There are two SATA disks -- the primary is a Vista system drive, and the secondary has Ubuntu installed via Wubi -- in the fstab file below you can see "host" which is the second drive I want to appear.

The first drive is 'sda3' (which shows up properly under its drive name) and the second 'sdb1'

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by Het Irv on 2008-04-22
I haven't used Wubi yet, so educate me.
How does Wubi install Ubuntu, into a seperate partition or a File in Windows?

---

### Post by ninestories on 2008-04-22
As a file in Windows.

Wubi installed to its own directory on a Windows NTFS drive and does not require a separate partition.  The reference from fstab to "/host/ubuntu/disks/root.disk" is simply to the directory hosting the entire Ubuntu filesystem as a single file (root.disk is a 13.0GB file in my case).

In fact, /host/ ***is*** the mounted drive itself, but does not appear in the 'Computer' listing.

---

### Post by Het Irv on 2008-04-22
So how would you boot into Ubuntu using Wubi?  Does the line in Grub just point to that file or do you have to goto Windows first?

Thanks for your patience while I wrap my brain around whats going on, I am still working on your problem.

---

### Post by ninestories on 2008-04-22
Booting is still managed by Windows Boot Manager, with an option to boot to either Vista or Ubuntu.  Selecting Ubuntu kicks you over to GRUB4DOS, which then boots Ubuntu using the following (excerpted from /boot/grub/menu.lst:

```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=E21A05E31A05B597 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
```

If it helps to explain, GRUB also uses (the contents of /boot/grub/device.map)

```
(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

Thank you again for your patience and understanding.

---

### Post by Het Irv on 2008-04-22
Thanks for the explanation.  Let me make sure I have this right.  You have two OS's on one partition and with some code magic you can boot to one or the other without having to boot to one and open a VM.  So technically you are already mounted to the physical drive.  What you want is a way to get to the Windows files to appear in "Computer:///", correct?

---

### Post by chrisccoulson on 2008-04-22
Have you tried mounting the drive under /media instead of /mnt?

---

### Post by ninestories on 2008-04-22
Chris:
Mounting to /media instead of /mnt doesn't work either.

Het Irv: 
You are correct.  I am already mounted to the drive and can browse its files through /mnt/drivename/ or /media/drivename/ in Chris' example, I just want it to show up under computer:///

---

### Post by Het Irv on 2008-04-22
I have a drive that is set up similarly and I was trying a few things, but I kept getting an error saying "operation not supported by backend"  This might mean that it is not possible, but you can put a shortcut to the file in the list on the left-hand side.

Browse to the file you want to link to and drag-and-drop to the sidebar.  This will give you a link to the file like the links to Documents and Pictures and whatnot.  It will also show the link when you use "Save-As" and "Open" so it might be a bit more convenient. 

*Still looking for a way to put it in Computer:///*

---

### Post by ninestories on 2008-04-22
I've also just tried adding the device directly to fstab to see if I can get it to show up after rebooting.  I added

```
/drv/sdb1 /media/drivename ntfs-3g defaults,locale=en_US.utf8 0 0
```

which made the system unable to boot (presumably since that drive is also the parent of the root) until the GRUB file was changed to the following

```
/host /media/drivename ntfs-3g defaults,locale=en_US.utf8 0 0
```

Which brought the system to boot but neither mounted nor made available the additional volume.  In the meantime I can suffice with a shortcut, but I'm disappointed that this is turning up as tricky as all that when I'm sure it's something simple.  In fact, when I installed Ubuntu I did not have this problem -- it was only after installing the updates that the problem ensued.  Go figure.

Again, thank you for your continued help and support.  I look forward to any future solutions. :)

--j.

---

