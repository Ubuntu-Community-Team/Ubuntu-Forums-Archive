---
title: "Bad hard disk?"
date: 2005-09-14
forum: General Help
---

### Post by usacomp2k3 on 2005-09-14
First off, I'm sorry if this is in the wrong forum/subforum. 
I'm a linux n00b, as this box was my first taste of linux. I installed 5.04 on it, and had no problems. I got apache and mysql and all that working, (using lampp) no problem. After a little bit of work, I got a ventrilo server working. I then was in the middle of trying to get a no-ip service running when this happened. This is a dedicated computer for hosting a website, including a phpbb forum and a gallery, image gallery (go figure).
The machine is an old Dell celeron 400 with 128mb RAM. The drive is a Maxtor 6.5gb. The 'net connection is 6mbit/384kbps cable.
The last think I did before the crash, was change the port that ssh runs over, and then went to restart the computer for that to take effect (been a windows user all my life, don't know if that's necessary of linux). After that, the computer never booted right.
It goes through, up to the grub section, no problem. Then it starts giving errors. Let me see if I can type alot of them up for you:
```

root  (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
  [Linux-bzImage, setup 0x1600, size=0x120b06]
initrd  /boot/initrd.img-2.6.10-5-386
  [Linux-initrd @ 0x3a7d000, 0x433000 bytes
savedefault
boot
Uncompressing Linux... Ok, booting the kernel
...something about an audit
... (I missed alot of this)
/loadmodules: 7: cannot create /dev/null: Read only file system
...(it then repeats that for 8, 9, 10...up to at least 30)
...(I might have missed something in here, it went by way too quick)
ERROR: Module pdc202xx_old does not exist in /proc/modules
ERROR: Module piix does not exist in /proc/modules
ERROR: Module rz1000 does not exist in /proc/modules
ERROR: Module sc1200 does not exist in /proc/modules
ERROR: Module serverworks does not exist in /proc/modules
ERROR: Module siimage does not exist in /proc/modules
ERROR: Module sis5513 does not exist in /proc/modules
ERROR: Module slc90e66 does not exist in /proc/modules
ERROR: Module triflex does not exist in /proc/modules
ERROR: Module trm290 does not exist in /proc/modules
ERROR: Module via82cxxx does not exist in /proc/modules
/sbin/init: 395: cannot create /dev/null: read-only file system
/sbin/init: 422: cannot create /dev/null: read-only file system
/sbin/init: 422: cannot create /dev/null: read-only file system
/sbin/init: 422: cannot create /dev/null: read-only file system
/sbin/init: 422: cannot create /dev/null: read-only file system
/sbin/init: 422: cannot create /dev/null: read-only file system
/sbin/init: 422: cannot create /dev/null: read-only file system
/sbin/init: 422: cannot create /dev/null: read-only file system
/sbin/init: 422: cannot create /dev/null: read-only file system
pivot_root: No such file or directory
/sbin/init: 428: cannot create /dev/null: read-only file system
/sbin/init: 420: cannot open dev/console: No such file
Kernel panic - not syncing: attempted to kill init!

``` 
So yeah, any ideas?
I'd rather not have to just completely rebuild, but I'd rather do that then have to do too much work to patch it :P
If there's any more tests I can run, I'd be happy to. I do know that it's not the ram, as I did run memtest, and it does the same thing with just one of the 64mb chips.

---

### Post by KenLazlo on 2005-09-14
the message read-only filesystem occures sometimes when the filesystem of the partition is damaged. 

first of all, I would boot ubuntu live cd and check the filesystem:

fsck /dev/hda1

---

### Post by usacomp2k3 on 2005-09-14
```

ubuntu@ubuntu:~$ sudo fsck /dev/hda1
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/: clean, 93922/750720 files, 794059/1500061 blocks

``` 

That doesn't really sound too helpful  :smile:

---

### Post by mlomker on 2005-09-14
What is the output of:

```

mount
sudo fdisk -l

```

---

### Post by usacomp2k3 on 2005-09-14
```

ubuntu@ubuntu:~$ mount
/dev/mapper/casper-snapshot on  / type (rw,noatime)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /lib/modules/2.6.12-8-386/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,modev)
tmpfs on /dev type tmpfs (rw, size=10M,mode=0755)
ubunut@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device        Boot       Start             End          Blocks        Id         System
/dev/hda1     *           1                   747         6000246     83         Linux
/dev/hda2                  748               784          297202+      5         extended
/dev/hda5                  748               784          287171      82         Linux swap / Solaris


```

---

### Post by usacomp2k3 on 2005-09-14
Well, I was able to boot using the Live CD, and was able to mount the hard disk, and all the data appears to be there. (One gets much satisfaction from figuring out how to do that on an alien OS  ;-) )
So it seems like it's just the partition that's messed up. I'll probably go ahead and reinstall on a 2nd HDD I have laying around and basically just build it from scratch.

EDIT: is there anyway I can read a boot log off the broken drive if I mount it either under the live CD or under the new hdd install?

---

### Post by mlomker on 2005-09-15
[QUOTE=usacomp2k3]EDIT: is there anyway I can read a boot log off the broken drive if I mount it either under the live CD or under the new hdd install?[/QUOTE]

You mean the stuff that scrolls across the screen?  I don't think so but that'd sure be nice.  I should research a way to do that.

You can access the contents of what is normally output by dmesg, though.  That is stored in the /var/log/kernel.log file.

---

### Post by mlomker on 2005-09-15
[QUOTE=usacomp2k3]```

ubuntu@ubuntu:~$ mount
/dev/mapper/casper-snapshot on  / type (rw,noatime)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /lib/modules/2.6.12-8-386/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,modev)
tmpfs on /dev type tmpfs (rw, size=10M,mode=0755)

```[/QUOTE]

I'm left to assume that you ran the command while on a boot CD or something, because hda1 isn't mounted there.  I was curious if it'd show up as (rw) or not.

---

### Post by usacomp2k3 on 2005-09-15
[QUOTE=mlomker]I'm left to assume that you ran the command while on a boot CD or something, because hda1 isn't mounted there.  I was curious if it'd show up as (rw) or not.[/QUOTE]
Yeah, Breezy Badger Live CD. Let me see what it says for that when I mount the drive.
```

ubuntu@ubuntu: /mnt/temp$ mount
...
/dev/hda1 on /mnt/temp type ext3 (rw)

``` 
There wasn't anything but networking in the kern.log, so yeah. And the dmesg in /mnt/temp/var/log didn't have anything abnormal, so I don't know *shrug*

---

### Post by mlomker on 2005-09-16
I think you need to reinstall.  I'd recommend adding a journal to your drives (that's default in the new Breezy version) or using reiser partitions instead.  Ext3 partitions can withstand more abuse than drives without a journal.

Boot up to a Knoppix or another linux CD (and then do a Ctrl-Alt-F2 to get to another screen).

You can reformat to reiser before your new install with **mkreiserfs /dev/hd?**, or you can upgrade to ext3 before or after with **tune2fs -j /dev/hda?**.

If you aren't sure about the partition number then **fdisk -l** will get you a list.

---

### Post by sneax on 2005-09-16
Just a small note irrelevant to your harddisk problem:
You want to install a no-ip service (I assume for updating a dynamic ip), just to make sure: if you have 'modern' router it's possible this router already has such a client, you would just have to login to the router, enter the information and the router keeps your ip updated with the service.

Just a notice in case you don't know, it's very easy and I use it too - much better and less hassle then all those stupid clientdaemons ;) Your router might not support all of them but mine supports dyndns.org which is excellent.

---

### Post by usacomp2k3 on 2005-09-16
Yeah, I went ahead and installed 5.10 on another HDD that I have. I'm just going to go with that. I believe it is in the ext3 mode (heard bad things about reiser that I'm not 100% comfortable with it, since I don't know what's going on anyway :P)
And re: the dynamic IP.
Yeah, the router I have at home does that, but since I don't live at home (@ college), I'm not 100% sure that the server is going to stay there, so I'm just going to install it locally so that the IP will follow the server, which is what I need it to do.

Thanks for your help guys.
-usacomp2k3
(typed in the first install of linux on my laptop (woohoo for Breezy Badger) )

---

