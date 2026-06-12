---
title: "cannot create files on external usb"
date: 2013-02-03
forum: General Help
---

### Post by qwertyjjj on 2013-02-03
I just formatted my exterla usb to ext2 but once done I cannot create any files/folders or copy anything onto the drive?
Is this a permissions problem?
I tried chmod to 777 but that doesn't work.
jason@spain ~ $ sudo blkid
/dev/sdb1: UUID="c78c7fe0-6def-48d7-ab7a-78c371e55a27" TYPE="ext4" 
/dev/sdc1: UUID="10a56044-4866-482f-88da-358e0eb9acaf" TYPE="ext2" LABEL="USB" 


I use it on different computers and it worked before without having to change permissions.

---

### Post by TheFu on 2013-02-03
Are there any errors displayed?
What do the log files in /var/log/* show?  Use **grep **to find warnings and errors.

---

### Post by rnerwein on 2013-02-03
> **qwertyjjj said:**
> I just formatted my exterla usb to ext2 but once done I cannot create any files/folders or copy anything onto the drive?
Is this a permissions problem?
I tried chmod to 777 but that doesn't work.
jason@spain ~ $ sudo blkid
/dev/sdb1: UUID="c78c7fe0-6def-48d7-ab7a-78c371e55a27" TYPE="ext4" 
/dev/sdc1: UUID="10a56044-4866-482f-88da-358e0eb9acaf" TYPE="ext2" LABEL="USB" 


I use it on different computers and it worked before without having to change permissions.
hi
please post the output of your "mount" command to see how it is mounted.
for "blkid" it's some times better to call blkid with -c /dev/null to really get the truth.
and what is the error message when you try to some thing to your USB.
cheers

---

### Post by ibjsb4 on 2013-02-03
For using a flash drive for just storage (ext2 or 4 or both) I just format the ext and do not use an UUID.  It will come up in nautilus this way.

---

