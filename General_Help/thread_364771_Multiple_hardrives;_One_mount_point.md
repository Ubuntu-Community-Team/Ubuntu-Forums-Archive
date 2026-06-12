---
title: "Multiple hardrives; One mount point ?"
date: 2007-02-18
forum: General Help
---

### Post by PsYcHo_SiB on 2007-02-18
Hi,

I have the latest version of ubuntu installed on one of my server. I have about 7 hard disks in the server, totaling about 1,4TB.

 I would like to know if it is possible via software to create only one volume totaling 1,4 TB ? Could I mount let's say the 7 hdd at one mount point ?

Thanks,

- SiB -

---

### Post by solar george on 2007-02-18
Logical volume manager?

Software RAID??

I'll try and find a howto.

'cause I don't know!

---

### Post by PsYcHo_SiB on 2007-02-18
Okay, I googled software Raid and found out some howto. I would like to know if my hard disk must be formated ? I can't format those disks because I have about 600gb of data on it. Is software Raid able to create one huge drive without formating ?

- SiB -

---

### Post by solar george on 2007-02-18
LVM - there is an explanation [here]("http://tldp.org/HOWTO/LVM-HOWTO/index.html")

Software raid - similar for raid [here]("http://tldp.org/HOWTO/Software-RAID-HOWTO.html#toc1")

There may be some newer ubuntu specific info somewhere - try the wiki



and as a last resort google it.

---

### Post by solar george on 2007-02-18
> I would like to know if my hard disk must be formated ?
Yes it must for sofware raid.

You might be able to get around this with LVM.

If you collect all the data on a few drives - there must be at least 600gb of storage available on the freed disks. Set-up the free disks as an LVM group and put a filesystem on it. Copy all of the data across from the old drives onto the LVM drive. Grow the LVM to take up all available space. Resize the file system to make full use of the LVM.

If you are going to do this you should get all the information that you are likely to need together first. Do more research of your own - all that I know about LVM is from experimenting on computers where it didn't matter if I made a terrible mistake.

And always backup,

or else..................

---

