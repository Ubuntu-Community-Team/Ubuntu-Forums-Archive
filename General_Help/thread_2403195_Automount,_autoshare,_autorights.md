---
title: "Automount, autoshare, autorights"
date: 2018-10-08
forum: General Help
---

### Post by troneleck on 2018-10-08
Hello,

i need a fileserver that automount's all drives (DVD, HDD, USB,...), makes a samba share for them and grants 777 automatically.

Wat option do i have to build this?

---

### Post by sp40140 on 2018-10-08
Please be more specific. 
for Automount: you can add entry in /etc/fstab file.
for Samba share: you configure the smb.conf file with the folders you want to share.
Both of these have excellent documents (and examples available in this forum and/or other sites). However, if you have any specific questions, post it and the group will help.
So, are you stuck at any point?

---

### Post by troneleck on 2018-10-09
With automount, i mean plug in a usb hdd (no fstab enty) and it is automaticlly mounted.
After the drive is mouned, i want it automatically as a sambashare with 777 rights.

I want a NAS where everyone can plug in drives and everyone in the network see them as share and they can change, copy, move, delete, execute files, without setting up anything by hand.

---

