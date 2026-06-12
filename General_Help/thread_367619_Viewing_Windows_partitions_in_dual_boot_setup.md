---
title: "Viewing Windows partitions in dual boot setup"
date: 2007-02-22
forum: General Help
---

### Post by t111 on 2007-02-22
When I was running dapper in dual boot with Vista I could
see the Windows partitions in dapper and could even mount
one small partition that I would use to store MP3 files that I
would play in both operating systems.
When I uninstalled dapper and installed edgy I no longer 
can see any Windows partitions at all, only the one created 
by the Ubuntu install.  Is there anything I can do to be able 
to view the Windows partitions again?

---

### Post by chggr on 2007-02-22
Make a folder in the /media folder:

sudo mkdir /media/WindowsPartition

Use the command mount to mount the partition onto that folder:

mount -t ntfs -o umask=000 /dev/hda1 /media/WindowsPartition

Where hda1 is the partition you want to access.

---

### Post by t111 on 2007-02-22
> **chggr said:**
> Make a folder in the /media folder:

sudo mkdir /media/WindowsPartition

Use the command mount to mount the partition onto that folder:

mount -t ntfs -o umask=000 /dev/hda1 /media/WindowsPartition

Where hda1 is the partition you want to access.


Thanks for that

---

### Post by naxmul on 2007-02-23
well, i was wondering. what does the umask option do?
does it apply the permissions that ubuntu is allowed to have to that partition?

---

### Post by chggr on 2007-02-23
umask changes the permission of the mounted items inside the folder. If you set umask=000, you give the read, write and execute access to all system users. For more info and options for ntfs and other types of partitions, open a console and type in:

man mount

and go to the chapter: "Mount options for ntfs"

The fact is that linux cannot write on a NTFS partition, so the write access will be disabled.

---

### Post by naxmul on 2007-02-23
oh. i didn't know that. learn something new every day. ^_^

thanks for the reply

---

### Post by ofek on 2007-02-23
Linux CAN write on ntfs (its even an option in the new kernels) search "ntfs-3g" in the forums for more info.

---

### Post by chggr on 2007-02-23
> **ofek said:**
> Linux CAN write on ntfs (its even an option in the new kernels) search "ntfs-3g" in the forums for more info.

Ok! It can, but officially NTFS is still not supported. 
When you use ntfs-3g to write on a windows ntfs partition, there exists a possibility that the filesystem will become corrupted. That's why this option on the kernel is not by default on. There is still room for improvement...

---

### Post by ofek on 2007-02-23
Theres always room for improvements but ntfs-3g is stable for day to day use easly.
I use it on my home network daily writing to any of my 5 computers which all have a an ntfs partition on them. This isn't only my experience but what the majority of users are experiencing. I've hadn't have a single memory fault in the past year im using it and although it isn't marked as stable there are enough distros who support it by default and probably fiesty + 1 will do so as well. 
I didnt mean to attack u by any means just I think its time people stop refering to ntfs writing as unstable and dangerous because those days are long gone.

---

