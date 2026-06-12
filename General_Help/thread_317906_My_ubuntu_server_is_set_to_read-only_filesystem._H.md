---
title: "My ubuntu server is set to read-only filesystem. Help !"
date: 2006-12-13
forum: General Help
---

### Post by Zpeeder on 2006-12-13
Hey, 


My ubuntu server has strangely switcht to a read-only system over night!
When logged in as Sudo I still can't move,copy or wright anywhere on the system. Not even in my Home Folder!

Is there any terminal commands I could use to solve this problem?  

Thank you.

---

### Post by Scorpuk on 2006-12-13
can you show us your fstab file just incase that has been changed to mount the drive as RO?


just a thought. :)

---

### Post by Zpeeder on 2006-12-13
Yes of course.
But how do I retrieve that information? 
I,m still kind of new with linux. ;) 

Thanks

---

### Post by Zpeeder on 2006-12-13
I did a quick search and tried these things:

1 Access the /etc/mtab file for information. 

2 Access /etc/fstab the configure file.

In both cases i got "bash: /etc/mtab: Permission denied" With fstab in the second try instead of mtab.

I was sudo when I did this.

---

### Post by taurus on 2006-12-13
```
cat /etc/fstab
```

---

### Post by sefs on 2006-12-13
I think also that drives turn read only when problems are detected with them that can usually be fixed with running a check disk.

---

### Post by Zpeeder on 2006-12-13
This is what the fstab showed:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0    1
# /dev/sda1
UUID=636b3b37-4ca2-4d14-93ef-662802fd098c /boot           ext3    defaults   0       2
# /dev/sda5
UUID=44ba6f2b-4ae3-4a29-8031-ed8f2ef53c87 none            swap    sw   0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by Xkutzy on 2006-12-13
Sefs is right. This could indicate a problem with the hard disk. I had a similar issue, disk suddenly went read only. Then after rebooting the file system had dropped back to ext2 instead of ext3. You can use the tune2fs to put the journal back on. In my case it turned out to be a hardware fault. I suggest  downloading the disk manufacturers diagnostics and testing the disk.

---

### Post by taurus on 2006-12-13
Is your / partition on /dev/sda2?

---

### Post by Zpeeder on 2006-12-13
Yes the partition is on /dev/sda2.

I've tried to start tune2fs but it won't start, neither will vim or any other program.

More ideas?

---

### Post by taurus on 2006-12-13
Boot with the LiveCD.  Then mount your harddrive and edit /etc/fstab...

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda2 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/etc/fstab
```
Now, place a # in front of this line

```
/dev/mapper/Ubuntu-root /  ext3  defaults,errors=remount-ro 0    1
```
and add a new line just below it...

```
/dev/sda2  /  ext3  defaults,errors=remount-ro  0  1
```
Unmount it and reboot.

```
sudo umount /mnt/ubuntu
```

---

### Post by Zpeeder on 2006-12-13
It worked! 

Thanks, that saved me a lot troubleshooting ;)

---

### Post by taurus on 2006-12-13
Glad to hear it fixed the problem with / partition!

---

