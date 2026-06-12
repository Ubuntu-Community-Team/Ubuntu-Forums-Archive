---
title: "HELP my external harddrive seems broken"
date: 2007-03-10
forum: General Help
---

### Post by raffytaffy on 2007-03-10
im trying to format my 250gig external to fat32 partition. i tried partition magic on windows and it gave me errors about cylinders ( i know nothing of this) then i try gparted and it generate this error.

Create Primary Partition #1 (ext3, 232.88 GiB) on /dev/sda    ( ERROR ) 
      
   create empty partition    ( ERROR ) 
      
  path: /dev/sda1
start: 63
end: 488392064
size: 232.88 GiB 
  The kernel was unable to re-read the partition table on /dev/sda (Device or resource busy). This means Linux won't know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/sda.

and gpareted is crashing...please help i dont know what to do

edit- ive fixed the problem with a low level foramt to the external then using gparted to create fat32 storage.

---

