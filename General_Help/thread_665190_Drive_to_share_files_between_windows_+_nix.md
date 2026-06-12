---
title: "Drive to share files between windows + nix"
date: 2008-01-12
forum: General Help
---

### Post by phillips321 on 2008-01-12
Hi guys,

I have a spare 160Gb drive in my pc that is being used to share files between dual boot win&nix.

The drive is formatted as NTFS, contains files over 5Gb in size and is also used as the installation path for some windows apps.
My main problem is that this drive is getting very very fragmented.

Can FAT32 support file sizes as large as 5Gb+? What would be the best way to share the drive? currently NTFS is working fine other than the fragmentation, and because there are installed programs to this drive they are running very slow.

I've been told to format the drive again and create it using a bigger block size to try to prevent fragmentation, what else can i do?

Thanks in advance guys.

---

### Post by K.Mandla on 2008-01-13
Staff bump.

---

### Post by insane_alien on 2008-01-13
just boot up windows and defragment it from there. 

FAT32 would just make the situation worse even though it would initially offer a small speed advantage.

maybe the ntfs-3g project will come up with an ntfs defragger for linux.

i don't think there is a way to get FAT32 to store files larger than 4GB

---

### Post by r57 on 2008-01-13
Hi there!

U may want to hace drive formatted to ext3 rather to NTFS, then install ext3 drivers to windows to be able read/write the ext3 partitons.

I found ext3 drivers for windows after some googling and all going well so far, but well... I dont use windowz very often so I cannot say how it will work in general use.

Note that with drivers installed windows see and can operate ext3 partitions same way as any other partition type (FAT,NTFS).

---

### Post by insane_alien on 2008-01-13
just a warning if you install the ext3 driver in windows, if your windows install gets a virus that trashes everything it sees it WILL trash your linux install as it will be able to see it.

it is more secure to let linux see windows but not let windows see ubuntu.

a shared partition help increas interchange of files.

---

### Post by atheistkun on 2008-01-13
in windows u can defragment using auslogics
it is fast, free and a good defragmenter

---

