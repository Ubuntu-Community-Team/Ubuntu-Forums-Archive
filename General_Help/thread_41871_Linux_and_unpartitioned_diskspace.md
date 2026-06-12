---
title: "Linux and unpartitioned diskspace"
date: 2005-06-15
forum: General Help
---

### Post by omppa on 2005-06-15
:?  Which tool is best way to change unpartitioned diskspace( turn it into ext3) so that i can use it in ubuntu? Maybe some craphical tool or some terminal tool?

 ](*,)  ](*,) And how i can it make happen?

Sami

---

### Post by Knome_fan on 2005-06-15
I haven't tried it myself, but if you are looking for a graphical tool, you could give gparted a try.

Also, qtparted (which uses qt, whearas gparted uses gtk) is a good graphical tool for your purpose.

---

### Post by az on 2005-06-15
man mke2fs


Be careful to not blow away an existing filesystem!

---

### Post by Knome_fan on 2005-06-15
[QUOTE=azz]man mke2fs


Be careful to not blow away an existing filesystem![/QUOTE]

Excuse my ignorance, but shouldn't you first creat a partition with fdisk, or cfdisk befor you format it?

---

### Post by az on 2005-06-15
Yup.  As they say, "my bad"  I thought that it was a case of an unused partition.


Parted can do all that for you. 

sudo parted /dev/dha (if hda is the correct drive)
print #this lists your partitions
mkpartfs
Enter the information as prompted (sensible defaults are usually provided)
and you are good to go....

---

