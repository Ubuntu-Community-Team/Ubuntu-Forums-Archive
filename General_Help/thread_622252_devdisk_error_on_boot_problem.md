---
title: "dev/disk error on boot problem"
date: 2007-11-24
forum: General Help
---

### Post by AllanP on 2007-11-24
I have re-installed 7.10 again and the same problem persists. I do the install, update the package, make a few minor adjustments and I have the enclosed jpeg error on boot up; which in turn makes me sign in where I have the login window set to automatic login. I've tried as you can see with the included fstab ## out a few lines which I thought may be the problem. All this was ok in 7.
Edit: I just noticed the end of the line sda2 which is swap but, why?
fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=50063f12-e923-46f9-870d-f672218b687d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
## UUID=8d03b1b2-152b-4289-b716-938f2de6d744 /media/mydata   ext3    defaults        0       2
# /dev/sda1
UUID=1201DEF75EAE43A9 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda10
UUID=3619E14036238B54 /media/sda10    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=04ef3e31-14a0-4d83-9948-fbb64483449b /media/sda6     ext3    defaults        0       2
# /dev/sda7
UUID=fb337856-7b1f-411d-929a-f900b7e62af9 /media/sda7     ext3    defaults        0       2
# /dev/sda8
UUID=901159cc-c51c-4c39-a07d-77c39863b881 /media/sda8     ext3    defaults        0       2
# /dev/sda9
UUID=4743-3AF8  /media/sda9     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=70171531-e3a1-41ed-957e-9aa1b2ed0498 /media/sdb1     ext3    defaults        0       2
# /dev/sdb2
UUID=50e23e91-6268-41f1-a8a1-1330d168b178 /media/sdb2     ext3    defaults        0       2
# /dev/sdb3
UUID=4F7F945737B2F9A7 /media/sdb3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=9fa2acbe-e404-4f1b-a340-7de19b78cfa7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
##/dev/sda6   /media/sda6   ext3   defaults   0   1
##/dev/sda7   /media/sda7   ext3   defaults   0   1
## /dev/sda3   /media/mydata   ext3   defaults   0   1

blkid

allan@allan:~$ blkid
/dev/sda1: UUID="1201DEF75EAE43A9" TYPE="ntfs" 
/dev/sda2: TYPE="swap" UUID="9fa2acbe-e404-4f1b-a340-7de19b78cfa7" 
/dev/sda3: LABEL="/media/mydata" UUID="8d03b1b2-152b-4289-b716-938f2de6d744" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="50063f12-e923-46f9-870d-f672218b687d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="04ef3e31-14a0-4d83-9948-fbb64483449b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="fb337856-7b1f-411d-929a-f900b7e62af9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="901159cc-c51c-4c39-a07d-77c39863b881" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="4743-3AF8" TYPE="vfat" 
/dev/sda10: UUID="3619E14036238B54" TYPE="ntfs" 
/dev/sdb1: UUID="70171531-e3a1-41ed-957e-9aa1b2ed0498" SEC_TYPE="ext2" TYPE="ext3" LABEL="/" 
/dev/sdb2: UUID="50e23e91-6268-41f1-a8a1-1330d168b178" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="4F7F945737B2F9A7" LABEL="Disk_2_NTFS" TYPE="ntfs"

---

### Post by AllanP on 2007-11-24
More attempts at solving my problem. I ran /usr/lib/klibc/bin/kinit and got this:

allan@allan:~$ /usr/lib/klibc/bin/kinit
  argc == 5
  argv[0]: "/usr/lib/klibc/bin/kinit"
  argv[1]: "root=UUID=50063f12-e923-46f9-870d-f672218b687d"
  argv[2]: "ro"
  argv[3]: "quiet"
  argv[4]: "splash"
  argc == 3
  argv[0]: "IP-Config"
  argv[1]: "-i"
  argv[2]: "Linux kinit"
IP-Config: no devices to configure
kinit: do_mounts
kinit: name_to_dev_t(UUID=50063f12-e923-46f9-870d-f672218b687d) = dev(0,0)
kinit: root_dev = dev(0,0)
kinit: failed to identify filesystem /dev/root, trying all
kinit: trying to mount /dev/root on /root with type cramfs
kinit: Cannot open root device dev(0,0)
kinit: init not found!

Can't identify my root file system.:confused:

---

### Post by Niniel on 2007-11-27
Are your hds connected to a RAID controller, or some other controller card? Maybe you need special drivers for those.

---

### Post by AllanP on 2007-11-28
No. I have (as you can see by my sig) two 250GB SATA drives which on my ASUS P5K Deluxe MB BIOS are set to IDE compatible. No Raid. All was fine in Ubuntu 7.04 and is fine in Fedora 8. Ubuntu 7.10 it seems has some issues; I think.
This bug issue seems similar: [https://bugs.launchpad.net/ubuntu/+bug/103148](https://bugs.launchpad.net/ubuntu/+bug/103148)
On the bug page it says "in progress"
103148  	 kinit: No resume image   	&#8212;  	Undecided  	In Progress

---

### Post by AllanP on 2007-11-28
I cannot solve the problem but, have discovered where the problem lies. My motherboard's ICH9 controller and or P35 chipset is the root. I disconnected my SATA drives; connected an old IDE drive and installed Ubuntu Gutsy. It all went flawlessly and is running great with none of the errors mentioned in my previous post. Now it isn't all my MB's fault as my Fedora 8 runs fine on the SATA configuration. I do have other issues with this MB and if I could justify the expense I would dump it and purchase a non P35 chipset and ICH9 controller.

---

### Post by Niniel on 2007-11-29
Wow, how did you find that out?

Fedora is pretty cool though, I agree. I had it installed on another machine to play around with, but I lost the root password, so I installed Red Hat over it. Unfortunately, my disk was a trial version of the Enterprise edition that requires registration/activation (now where do we know that from...), but that's a different story. 

Hats off again to your investigative talent.

---

### Post by AllanP on 2007-12-22
This problem is interesting: It doesn't do it every time. Here is the error message from a newer install:
Starting up ...
Loading. ;please wait...
kinit: name_to_dev_t (/dev/disk/by=uuid/abab853877-920f-4dc5-8152-4d57bef41da6) = sdas(8,2)
kinit: trying to resume from /dev/disk/by-ab853877-920f-4dc5-8152-4d57bef41da6
kinit: No resume image, doing normal boot...

Ubuntu 7.10 allan tty1

allan login:

It appears to me that the system when shutting down leaves an image on the swap file to assist in the next boot up. I always know when I shut down if this is going to happen on next boot by the error message when shutting down; which I haven't been quick enough to capture. But I guess accessing the swap file on shut down is the problem.

---

