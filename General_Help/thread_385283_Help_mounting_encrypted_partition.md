---
title: "Help mounting encrypted partition"
date: 2007-03-15
forum: General Help
---

### Post by ray007 on 2007-03-15
Using the encrypted filesystem howto I have made a luks-partition which I last accessed about 3 weeks ago.
Now when I tried to mount the partition again, cryptsetup tells me it's not a luks-partition.
How can I find out what's going wrong so I can get to my data again.

Ah, yes, I'm using a regularly updated edgy-system.

Many thanks in advance
Ray

---

### Post by larrybrazos on 2007-03-15
> **ray007 said:**
> Using the encrypted filesystem howto I have made a luks-partition which I last accessed about 3 weeks ago.
Now when I tried to mount the partition again, cryptsetup tells me it's not a luks-partition.
How can I find out what's going wrong so I can get to my data again.

Ah, yes, I'm using a regularly updated edgy-system.

Many thanks in advance
Ray
sudo fdisk -l

what type of format does it say the drive is?

---

### Post by ray007 on 2007-03-15
fdisk -l says
/dev/hda8           13638       19138    44186751    b  W95 FAT32

but that can't be right, and

mount -t vfat /dev/hda8 /mnt
gives
mount: wrong fs type, bad option, bad superblock on /dev/hda8,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and dmesg | tail says

[17194608.876000] FAT: invalid media value (0xd5)
[17194608.876000] VFS: Can't find a valid FAT filesystem on dev hda8.

--
Thanks for helping
Ray

---

### Post by ray007 on 2007-03-18
No more ideas what's going wrong and what I can do to recover my data?

I could really use some help here, please!

---

### Post by larrybrazos on 2007-03-18
sorry bro.  i am not very solid with hard drive stuff, i just knew fdisk -l might give some clues . . .

anyone else got an idea about this?

---

