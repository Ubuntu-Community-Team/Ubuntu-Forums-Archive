---
title: "create partitions via bash"
date: 2008-02-13
forum: General Help
---

### Post by bibawa on 2008-02-13
Hello,

for a school project I need to create a remastered Ubuntu cd for the installation of Thinstation. Now I need to create from a bash script the partitions on the harddisk.

What is the best way to do this ? I think Fdisk and than a grubinstall, but I cannot send inputs to fdisk via bash.

Any ideas?


kind regards,

---

### Post by lloyd_b on 2008-02-13
> **bibawa said:**
> Hello,

for a school project I need to create a remastered Ubuntu cd for the installation of Thinstation. Now I need to create from a bash script the partitions on the harddisk.

What is the best way to do this ? I think Fdisk and than a grubinstall, but I cannot send inputs to fdisk via bash.

Any ideas?


kind regards,

What exactly do you mean "I cannot send inputs to fdisk via bash"?  Are you saying that you've tried feeding it with a redirected input file, such as
```
fdisk /dev/hda1 < inputs.txt
```
and it didn't work?  (It *should*, but then I've never tried it...)

At any rate, if fdisk won't accept such inputs, try "sfdisk" instead.  "man sfdisk" in a terminal window for more info on sfdisk.

Lloyd B.

---

