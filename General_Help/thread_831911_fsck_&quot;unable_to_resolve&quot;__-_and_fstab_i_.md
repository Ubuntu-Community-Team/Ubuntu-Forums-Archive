---
title: "fsck &quot;unable to resolve&quot;  - and fstab i OK - what's wrong?"
date: 2008-06-17
forum: General Help
---

### Post by Andre-D on 2008-06-17
Strange problem, after much googling, I must ask:

why do I get:

```
~$ fsck
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: [COLOR="Red"]Unable to resolve[/COLOR] 'UUID=9e7d65ff-f9b5-465a-81b2-906ed8fa8a8c'

```

when my stab is:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=9e7d65ff-f9b5-465a-81b2-906ed8fa8a8c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=789ec2a0-e5f3-413d-a447-c5dc5675d3cf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```



and 

```
~$ sudo blkid
/dev/sda1: UUID="24800BFE800BD568" TYPE="ntfs" 
/dev/sda2: UUID="6A4895C848959403" LABEL="Storage" TYPE="ntfs" 
/dev/sda5: UUID="9e7d65ff-f9b5-465a-81b2-906ed8fa8a8c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="789ec2a0-e5f3-413d-a447-c5dc5675d3cf" 

```


Please help.

---

### Post by chrisccoulson on 2008-06-17
What is the output of:
```
sudo vol_id /dev/sda5
```

---

### Post by Andre-D on 2008-06-17
```
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=9e7d65ff-f9b5-465a-81b2-906ed8fa8a8c
ID_FS_UUID_ENC=9e7d65ff-f9b5-465a-81b2-906ed8fa8a8c
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
```

thanks for trying to help

BTW: this is the main partition where I am running OS from right now.. so it's working.

---

### Post by plucky on 2008-06-17
> ~$ fsck
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=9e7d65ff-f9b5-465a-81b2-906ed8fa8a8c'


I am assuming you get this problem when you are booting.

Does it stop the boot process?

How far into the boot process does it get?

Do you <CTRL D> to continue? 

Open a terminal and post output of ```
cat /boot/grub/menu.lst
```

---

### Post by bufsabre666 on 2008-06-17
if its a permanent drive in the computer ((looks like a drive on the primary sata channel)) then this will prolly work 


back it up first

```
sudo cp /etc/fstab /etc/fstab.0
```


open a text editor
```
sudo gedit /etc/fstab
```

and replace it with this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
/dev/sda5/    /           ext3    defaults,relatime,errors=remount-ro 0       1
# /dev/sda6
/dev/sda6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

reboot
```
sudo shutdown -r now
```

give that a twirl

---

### Post by rbprogrammer on 2008-06-17
I get the same error:
```

$ fsck
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=d267541c-af6c-486f-a0dc-27db50d1081a'

```
I think it might be because fsck cannot check a mounted filesystem correctly.  The UUID (both mine and Andre-D's) is the root partition.  Since you can't unmount that while logged in, I don't see a way to fsck that partition without just slaving the drive on another computer.

Andre-D, is there any other problems with the drive?  Why do you want to fsck?  One would usually fsck on an unmounted partition, for example, for me to check my flash drive I would do:
```

$ sudo fsck /dev/sdd1

```

---

### Post by rbprogrammer on 2008-06-17
> **Andre-D said:**
> 
Strange problem, after much googling, I must ask:

why do I get:

```
~$ fsck
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: [COLOR="Red"]Unable to resolve[/COLOR] 'UUID=9e7d65ff-f9b5-465a-81b2-906ed8fa8a8c'

```
...
...
...
BTW: this is the main partition where I am running OS from right now.. so it's working.

Upon further examination, I suspect it is just an error in the fsck program.  As I said in my previous post, people usually specifically say what partition they want to fsck.  So if you call the fsck command without any parameters, the program must be doing something by default that causes that.  I get the same thing and there is nothing wrong with my system.

Hope that helps.

---

### Post by Andre-D on 2008-06-17
rbprogrammer: "is there any other problems with the drive? Why do you want to fsck?"

I am trying to do it because I (successfully) enlarged the partition using Acronis Partition tool.
no, it seems to be healthy, and during boot, it just skips the test.

And YES, i've been trying to start it without any parameters.
(I kind of hoped to make it offer to check upon next boot)

plucky: some of your questions are answered, and grub does have proper UUID's

so the conclusion is that everything is OK (?)
Thanks to all.

---

