---
title: "Help with &quot;fixmbr&quot; and &quot;fixboot&quot; commands.."
date: 2008-01-19
forum: General Help
---

### Post by Pablocm on 2008-01-19
Hi everyone. I'm trying to restore the default windows MBR using the recovery console, My plan is to restore the default Windows boot loader and then erase the linux partitions.

Ok, so I boot up the Recovery console and type "fixmbr". The problem is that it says this (not exact text, I'm translating it from spanish):

```
 
***WARNING***
This computer appears to have a non-standard or invalid MBR *[SIZE="1"]("Registro de inicio principal", i'm not sure if that's an MBR in english)[/SIZE]*.
FIXMBR may damage your partition tables if you continue.
This may cause that all partitions in your hard drive to be inaccessible.
If you don't have problems to obtain access to your drive, do not continue.
Are you sure you want to write a new MBR? __ (y/n)

```

A pretty intimidating message I must add :-s. So I googled up this problem and it seems to erase all partition data and messed up things :(... So what do I do?

By the way, I only have one 40 GB HD drive, and it looks like this: (c+p from Gparted)

/dev/hda1   fat32   6.9 GiB           (my data drive)
/dev/hda2   ntfs    26.9 GiB  boot   (my windows partition)
/dev/hda3   ext3   3.11 GiB           (my old ubuntu partition)
/dev/hda4   linux-swap   287.9 MiB

Thanks in advance.

---

### Post by torgrot on 2008-01-19
You would answer yes, and it will wipe out Grub and replace it with Windows boot loader which if I read you correctly is what you want to do.

torgrot

---

### Post by kellemes on 2008-01-19
MS likes scaring people.. so it's all fine..
It will only "fix" (for lack of a better word) the bootloader, no partitions will be deleted or something..

---

### Post by Pablocm on 2008-01-19
One last question... is this a normal message that appears to everyone using "fixmbr", or it appears only to some unlucky people?

---

### Post by ajgreeny on 2008-01-19
Everyone gets it!

---

### Post by kellemes on 2008-01-19
> **ajgreeny said:**
> Everyone gets it!


Indeed.

---

