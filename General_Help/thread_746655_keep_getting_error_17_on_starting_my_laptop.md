---
title: "keep getting error 17 on starting my laptop"
date: 2008-04-05
forum: General Help
---

### Post by ironzee on 2008-04-05
Hi i was trying out Ubuntu 7.10 & ended up installing it on my laptop. When installing i didnt change any options given to me other then the time, contry & keyboard settings.

Enjoyed it for a few day, now i have decided to install it to my desktop & get my vista back on my Laptop I am a Laptop Dj / producer & photograpger i use this laptop for various things for which i need vista back. 

upon reinstalling the vista back i kept getting error that no partition was avilable.done some googling around & found out about formating hd with Gparted, Done that made the hd into fat32 so that my laptops recovery disc can read it & it did.

It installed restored the manufactures settings back to the laptop meaing all the softwares that came pre-installed & vista are restored.

now heres a new problem which is making me crazy when i restart the laptop it says  

 GURB Loading stage1.5 

GURB Loading, please wait...
Error 17

i done some more googling & found out that i can actually format the whole drive with all data with  boot`n`nuke but it didnt work it said theres errors in sectors.

Please help i need to get back to vista so i can do my gigs.

---

### Post by twright on 2008-04-05
with gparted delete all but the recovery partition make an ntfs partition, right click on it select 'manage flags' and tick 'boot', vista should now be able to install

---

### Post by ironzee on 2008-04-06
Thanks !! I will try this

---

### Post by ironzee on 2008-04-06
YES! YES!! It worked thanks a million twright.

---

