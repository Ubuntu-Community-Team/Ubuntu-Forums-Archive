---
title: "Can't boot Dapper after failed MS Windows install"
date: 2007-05-23
forum: General Help
---

### Post by wanton on 2007-05-23
Hi all,

System is as follows:

hda ubuntu Dapper ext3
hdb MS Windows fat32
HDC storage fat32

After a failed attempt at reinstalling MS Windows on hdb, I can no longer get Dapper to boot. The system wanted to do a fsck so I let it. It found many problems with inode 8 which I let it fix. No wwhen booting I get:

Kernel 2.6.15-27-386
uncompressing linux ok ... booting kernel

various lines then:

Mount: Mounting /dev/hda1 on /root failed: invalid argument
mounting /root/dev on /dev.static/dev failed no such file or directory
mounting /sys on /root/sys failed : no such file or dir
mounting /proc on /root/proc failed: no such file or dir
Target file system doesn't have /sbin/init

then I get BusyBox and the following:
/bin/sh: can't access tty job control turned off.

I cannot mount the drive from the live cd. Mount gives the following:

ubuntu@ubuntu:~$ sudo mkdir /mnt/cdrive
ubuntu@ubuntu:~$ mount /dev/hda1 /mnt/cdrive
mount: only root can do that
ubuntu@ubuntu:~$ sudo mount /dev/hda1 /mnt/cdrive
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Although maybe my mount command needs some extra arguments?

Any suggestions, or is my dapper dead and I should just cut my losses (there is some data in /home I'd really like to keep/resurrect if possible)

---

### Post by SteveHillier on 2007-05-23
Windows zaps the GRUB boot loader.  Even if you have a complete windows load you lose any Linux installations you have got.
That is why if you are making a dual boot system you MUST install Linux second.
ps.  I did have fun recently when I had a machine with Win XP, Win VIsta and Ubuntu loaded on it.
Steve

---

### Post by wanton on 2007-05-23
Hmmm.....are you sure? I do *not* have the two OS's on the same drive they are on *separate* drives. Grub is still there, I still have all my boot options in the Grub menu.  I figured Windows 98 should not have been able to even see hda to do any damage to it. (And certainly when scandisk was run it only saw hdb and hdc which were the only two fat32 formatted drives)

Anyway, i am not interested (well not primarily) with why it happened, just with whether my Dapper install is basically "gone to <insert name of deity here>" or whether (and how) I can save my /home data which foolishly is on the same partition as the rest of the Dapper install.

---

### Post by SteveHillier on 2007-05-25
Can anyone ever be sure inthis game!!
I had a machine with Win XP installed.  I then loaded Ubuntu (Dapper) on the same disk dual boot.  Worked fine.  Dapper partitioner even did some clever stuff in finding space for itself - but then what did we expect.
Let a few months go by and WIn Vista appears.  As I spend my time supplying computers, Vista was important for me to test.  So I thought I would get clever.  Put in a fresh HD.  Install Vista to that disk leaving HD0 in place.  Reboot machine.  Boot options - Vista or older version of Windows.  Dapper disappeared without trace.
Sorry if this does not help.  Why is it that Linux has to be cognicent of WIndows but Windows does not believe Linux exists?
Steve

---

### Post by rillip on 2007-05-25
Yes, the mount command here is incorrect.

Here is a correct one:

sudo mount -t filesystemtype /device /location

So for me, mount -t ext3 /dev/sda1 /mnt/storage

Mounts my extra sda drive to my storage directory.

Hope that helps!

---

