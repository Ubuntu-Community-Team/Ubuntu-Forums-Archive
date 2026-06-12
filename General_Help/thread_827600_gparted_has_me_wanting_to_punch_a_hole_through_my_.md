---
title: "gparted has me wanting to punch a hole through my computer"
date: 2008-06-12
forum: General Help
---

### Post by wripley on 2008-06-12
is there any way to use gparted to format a SECOND hard drive as ntfs?  so far nothing i have tried has worked and the live cd fails because of my 8800 GT, a graphics card that came out almost a year ago but is still mostly unsupported.  what do i have to do to use the gparted desktop app to format the hard drive that NOTHING IS INSTALLED ON?

---

### Post by sdennie on 2008-06-12
What is your exact problem with gparted?  Does it not see the disk?  Will it not let you modify the disk?  If it's already formatted as NTFS and it's being automounted, you'd have to unmount it before you can use gparted on it.

---

### Post by aysiu on 2008-06-12
Error message? Screenshot?

Is it GParted that's failing or your live CD failing?

---

### Post by wripley on 2008-06-12
i can see the drive, and i can set it up to format as any format except NTFS.  there is no error message or anything, it just won't do it.  and now my PSU just burned out so i'm super pissed off.

---

### Post by bluepowder7 on 2008-06-12
one thing i've noticed with my GParted is that sometimes, it only does things if i ask it to do one thing at a time.  so, if i say "erase all partitions, create one large partition, format to jsf" and then click apply, it'll barf 70% of the time.  but if i do "erase all", apply, "create one large", apply, "format to...", apply - then it'll actually succeed at doing what it's supposed to do.

worth a try?

---

### Post by wripley on 2008-06-13
i don't think you guys understand what i meant.  i meant that i can format as any other format if i wanted to, but the NTFS format option is unclickable.  i think i need to install something called ntfsprogs, but i can't find a downloadable/instalable copy of it for hardy (ubuntu studios 8.04)

---

### Post by logos34 on 2008-06-13
try deleting the partition first, then create a new one and see if it will then allow you to choose ntfs format

---

### Post by wripley on 2008-06-13
ok i found ntfsprogs, but when i try to compile it, i get this read out in the terminal

checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.



what do i do?

---

### Post by brallan on 2008-06-13
as far as i know, 8.04 already has ntfs support, but keep in mind that ntfs support is only 99.99% in linux. ntfs was reverse engineered, its a back door and it doesn´t always work. its always better to set up the ntfs filesystem from the people who have the keys to the front door, M$.

bootdisk.com, however, for only US$4 paypal will let you download tools which will do just what you need.

---

### Post by wripley on 2008-06-13
> **brallan said:**
> we are not paid support, please don't act like it.

bootdisk.com, however, for only US$4 paypal will let you download tools which will do just what you need.

... no... but you do claim to be the support forum for ubuntu... go back to bed and let the adults talk.

i ended up trying to do it a different way that doesn't use gparted... and this brallan guy really shouldn't be allowed to represent the community... it is a support forum after all

---

### Post by Oldsoldier2003 on 2008-06-13
> **wripley said:**
> ok i found ntfsprogs, but when i try to compile it, i get this read out in the terminal

checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.



what do i do?

ntfsprogs is in the main repository. ```
sudo apt-get install ntfsprogs
```and when you next run gparted you will be able to perform all actions on a NTFS partition

---

