---
title: "mounting more then one LVM drive on live CD with the same name."
date: 2013-02-09
forum: General Help
---

### Post by ulao on 2013-02-09
So I have two drives in my system 

one) sda with a partition for swap and a partition for my EXT4 LVM that contains my data. The drive will not boot.

two)made decadent to the above with a clean install and it boots. 

My goal is to copy my data from one to two. I have booted to the live CD and ran installed lvm2. When I run sudo vgchange -ay it shows both drives the exact same name. If I look in /dev there is only one entry so I can only boot one drive. How in the heck can I get to the second?

---

### Post by ulao on 2013-02-09
I scratched the idea and tried Clonezilla, took a bit of work but that got it.

---

