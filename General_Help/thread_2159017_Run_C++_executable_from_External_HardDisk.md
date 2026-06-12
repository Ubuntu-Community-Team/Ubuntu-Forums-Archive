---
title: "Run C++ executable from External HardDisk"
date: 2013-07-01
forum: General Help
---

### Post by sajad2006 on 2013-07-01
I am new at linux and trying to run a C code on some large data files placed on my external hard disk. 
I cannot attribute the executable permission to C output file when I copy and compile it on external disk. It works fine if I bring the data file to PC, but due to limited space, I prefer to run it directly from external disk.

I tried some ways found on net, but mostly they only work for bash executables.

Thanks,

---

### Post by Impavidus on 2013-07-01
Is it an ntfs of fat32 drive? In that case it doesn't support linux permissions, so you can't make the file executable. But is there any reason not to keep the executable on your internal Linux drive, whilst keeping the data files on the external drive?

---

### Post by Peptid on 2013-07-01
I've never faced such a problem, but have you tried using 'sudo' or giving permissions with 'chmod' commands?

---

### Post by sajad2006 on 2013-07-01
> **Peptid said:**
> I've never faced such a problem, but have you tried using 'sudo' or giving permissions with 'chmod' commands?

I had tried too change the permission and ownership. didn't help

---

### Post by sajad2006 on 2013-07-01
> **Impavidus said:**
> Is it an ntfs of fat32 drive? In that case it doesn't support linux permissions, so you can't make the file executable. But is there any reason not to keep the executable on your internal Linux drive, whilst keeping the data files on the external drive?

It's NTFS. 
I need to use the executable for parallel calculation. I haven't try this yet, maybe I give it a shot!
Another idea I just had, maybe creating a link instead of actual executable may help. I try this tomorrow at work and then let you know.

Thanks

---

### Post by Vormeph on 2013-07-01
NTFS is supported only by Windows, not Linux. That's probably the reason why you are having trouble. The best way to solve this is by putting the relevant programming files on a USB (or using DropBox) and then transferring them to your Linux machine then. 

I'm curious, why are you running programs from an external hard drive? It's hardly efficient, imo.

---

### Post by mc4man on 2013-07-01
This is a bit of an old story, you could find numerous threads from a couple of years ago or so. 
At that time changes where made to how both vfat & ntfs are mounted, the end result is that both executable binaries & executable text files cannot be run. Has really nothing to do with setting perm on the files after the fact (mounted), you can't,  but how they're default mounted.
Ex. 
*ntfs_defaults[] = { "uid=", "gid=", "dmask=0077", [COLOR="#FF0000"]"fmask=0177"[/COLOR], NULL }
The red prevents any file on ntfs from being run

*vfat_defaults[] = { "uid=", "gid=", "shortname=mixed", "dmask=0077", "utf8=1", [COLOR="#FF0000"]"showexec"[/COLOR], "flush", NULL };
red on vfat the same
There are various workarounds for both, **all** have some downsides.

---

