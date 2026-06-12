---
title: "Problem with grub"
date: 2007-04-20
forum: General Help
---

### Post by Chillster on 2007-04-20
I have this problem wich i havent had the energy to deal with for a while now.

 Every time i update my kernel and reboot grub points to the wrong partition and i get error 22 from grub. Then i have to edit menu.lst and put the correct info there to make it work. Then the same thing next update.

Not a major problem but its getting a bit annoying, anyone have any ideas ?

---

### Post by ashz on 2007-04-20
I know this will update everything though if i remember right the kernel should do it itself...

sudo update-initramfs -u

u might want to look into that more first though, because that is the bit which updates grub as well!!

---

### Post by chakkaradeep on 2007-04-20
> **Chillster said:**
> 
 Every time i update my kernel and reboot grub points to the wrong partition and i get error 22 from grub. Then i have to edit menu.lst and put the correct info there to make it work. Then the same thing next update.


It would be nice if you tell which version of Ubuntu (dapper,edgy,feisty) and also it would be nice if you paste your /boot/grub/menu.lst here.

Thanks

---

### Post by Chillster on 2007-04-20
oh right well, have had this problem with 6.10 but upgraded to feisty yesterday and got the same problem when i rebooted after upgrade. I will paste my menu.lst when i get home.

---

