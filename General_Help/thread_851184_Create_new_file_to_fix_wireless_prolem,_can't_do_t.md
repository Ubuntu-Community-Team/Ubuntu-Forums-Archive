---
title: "Create new file to fix wireless prolem, can't do that"
date: 2008-07-06
forum: General Help
---

### Post by Parkbench on 2008-07-06
I'm trying to get my wireless card working, and I'm doing what is described on this page: [http://linuxexpert.wordpress.com/2008/04/28/fix-intel-wireless-driver-on-hardy/](http://linuxexpert.wordpress.com/2008/04/28/fix-intel-wireless-driver-on-hardy/)

but when it comes to the part that says: create a file named iwl3945 in /etc/modprobe.d

How do I create a file in there? It doesn't give me an option to do so, and when I try to move a new file in there it says cannot move: permission denied.

I'm a complete noob, so please go easy on me if this is a retarded question.

---

### Post by tech0007 on 2008-07-06
alt-f2 then type 'gksu gedit', it will prompt you for your userpassword. OR
open terminal, 'sudo nano /etc/modprobe.d/iwl3945'
type what you need in there. save it by pressing ctrl-O ,[enter], ctrl-X.

---

### Post by Parkbench on 2008-07-06
Thank you, that did it.

---

