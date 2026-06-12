---
title: "Finally got the ubuntu boxed network, it flys!!"
date: 2007-10-12
forum: General Help
---

### Post by ade234uk on 2007-10-12
Really pleased. Finally managed to get the Ubuntu box networked so I can place my files in a secure place. 

After about 30 minutes of scratching I decided to map the drive in Windows to 192.168.1.xx/share which is the ubuntu box, then suddenly I was asked for a username and password.
I entered my standard username and password for Ubuntu and up came the folder. Excellent.

Just wondering if mapping the drive is the correct thing to do, as I can not access it through the network in Windows.

---

### Post by the_nite_owl on 2007-10-12
You may find that the mapped drive is read only.
You might want to setup Samba to share out drive/folders so that Windows clients will be able to read/write them and see them on the network.

---

### Post by ade234uk on 2007-10-12
The drive does read and write.
I dragged a file off the shared folder and put it back on. I also created a file on the shared folder and dragged it on to the windows desktop.

I got no permission errors, so I presume everything is working?

---

