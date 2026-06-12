---
title: "NFS share icon on the desktop"
date: 2007-07-08
forum: General Help
---

### Post by colossus73 on 2007-07-08
Hi,

I successfully automount a shared folder through NFS. I'm wondering how can I have an icon on the desktop as it happens with the others entry in /etc/fstab.

Thank you,

---

### Post by colossus73 on 2007-07-09
No replies? At least someone can show me where to look for? Hald configuration, udev configuration?

I'm using Xubuntu.

Thank you,

---

### Post by peterroots on 2007-07-20
well you have done better than me! I can't get an nfs to mount at all
(using ubuntu server and kubuntu clients)
In kubuntu you should be able to right click the desktop ->create new ->link to device-> NFS then select your device to get an icon on the desk top but I don't know how to do that in ubuntu or xubuntu sorry.

---

### Post by colossus73 on 2007-07-22
It was simple than ever. I double clicked with the right button and choosed Create URL Link. Then I pointed such link to file:///<my mount point> and I gave it an NFS share folder icon, So cool!

---

