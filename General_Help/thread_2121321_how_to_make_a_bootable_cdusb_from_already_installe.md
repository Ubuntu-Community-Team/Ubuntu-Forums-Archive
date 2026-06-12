---
title: "how to make a bootable cd/usb from already installed wubi"
date: 2013-03-01
forum: General Help
---

### Post by wolfybreak on 2013-03-01
Hello,

i am a lil bit beginner to the ubuntu and using ubuntu 10.04( my computer cant handle ubuntu 12 i tried :( and btw didnt even used 11 ) and as all first ubuntu users i came accross the that "making you insane!" grub problem i tried to replace files from c:/wubildr with mine existed one but didnt solved the problem i also tried to boot from grub by using commands

grub> insmod ntfs 
grub>set root=(hd0,5)  # its on the d: partion
grub>ls $Boot

etc....

it didnt woked eighter when i try 

grub>loopback loop0 /ubuntu/disks/root.disk  

it gave me "file label not found"  error so in the end i hated myself to not being able to do this stuff and i deceided to 
make a bootable cd or usb drive  from mine already installed wubi so my question is ,is it posible or i really  have to download from internet (i got  less than 100kbps net connection) and apoligize for my bad behaivor or bad language also english is not my main language :(

Thanks.

---

