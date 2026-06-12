---
title: "change name of automatically mounted drive"
date: 2007-09-16
forum: General Help
---

### Post by snark on 2007-09-16
Hi

I have a dual boot system with XP on two separate hard drives. My windows XP hard drive has two partitions on it. A C drive and a D drive.

When I installed Ubuntu it automatically mounted the two partitions and called them "local disk". 

I did not like those names. So I created two directories...

/media/WindowsC
/media/WindowsD

and then I added these two lines in my /etc/fstab file...

/dev/sda1 /media/windowsC ntfs ro,uid=1000,auto 0 0
/dev/sda5 /media/windowsD ntfs ro,uid=1000,auto 0 0

Now here is the problem. The drives mount properly and I can see the files. But the name of one of the mounts is still "Local Disk". In Nautilus under "Places" I have "WindowsC" which is good, and "Local Disk" which is in fact pointing to my Windows D drive. It is as if the drive is being mounted by some other process and called "Local Drive".

So my question is, how do I change the name of the mount from "Local Drive" to "WindowsD" given that I already have it that way in fstab. Where is "local drive" coming from?

Thx.

---

### Post by dcstar on 2007-09-18
> **snark said:**
> Hi

I have a dual boot system with XP on two separate hard drives. My windows XP hard drive has two partitions on it. A C drive and a D drive.

When I installed Ubuntu it automatically mounted the two partitions and called them "local disk". 

I did not like those names. So I created two directories...

/media/WindowsC
/media/WindowsD

and then I added these two lines in my /etc/fstab file...

/dev/sda1 /media/windowsC ntfs ro,uid=1000,auto 0 0
/dev/sda5 /media/windowsD ntfs ro,uid=1000,auto 0 0

Now here is the problem. The drives mount properly and I can see the files. But the name of one of the mounts is still "Local Disk". In Nautilus under "Places" I have "WindowsC" which is good, and "Local Disk" which is in fact pointing to my Windows D drive. It is as if the drive is being mounted by some other process and called "Local Drive".

So my question is, how do I change the name of the mount from "Local Drive" to "WindowsD" given that I already have it that way in fstab. Where is "local drive" coming from?

Thx.

Why not just label the drives in Windows and then they will be mounted using the labels?

---

### Post by snark on 2007-09-19
Hi dcstar

Great idea. I was not aware that that was where the names were coming from. 

Thanks.

---

### Post by dcstar on 2007-09-19
> **snark said:**
> Hi dcstar

Great idea. I was not aware that that was where the names were coming from. 

Thanks.

No worries, it is also something that you can do with USB drives so you always know which filesystem you have mounted (works with EXT3 as well as FAT/NTFS labels) - very handy if you plug different USB drives into your system.

---

