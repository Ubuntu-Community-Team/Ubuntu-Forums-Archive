---
title: "boot problem of windows 7 after deleting ubuntu from partition 'D' not properly"
date: 2016-07-11
forum: General Help
---

### Post by zeeshan_khan on 2016-07-11
Hello ,


I  just delete the partition of the Ubuntu in my D drive from dual OS systems. my Window 7 OS  is install in C drive. . when i start my laptop. it display rescue mode  and says grub problem. 

I run these commands


sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair

and get the following URL after running the boot-repair

http:// paste2.org/8V83CLJM

kindly guide me what I have to do in order to start my windows 7 which is in c partition and then I will make setting through disk manage. 

thanx alot in advance. 

sincerely

zeeshan

---

### Post by westie457 on 2016-07-11
Hi the link you posted does not work. Could you try again please.

---

### Post by grahammechanical on 2016-07-11
You need to re-install the Windows boot loader. A Windows repair/rescue disk should let you do that. Also Boot Repair has an Advanced option called Repair Windows boot files. See the last image in this wiki page.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards.

---

