---
title: "Printer Driver CUPS - User/Password not accepted"
date: 2015-07-20
forum: General Help
---

### Post by angel mike on 2015-07-20
I have a Brother Printer HL-3150CDW and have successfully installed the LPR and CUPSwrapper drivers (have  checked that these are installed). I then went to install the printer and modify the connection to Network mode but I am asked for  User/Password by CUPS. I enter these but they are not recognized.

---

### Post by wyliecoyoteuk on 2015-07-20
You need to be a member of the lpadmin group if I remember correctly.

---

### Post by angel mike on 2015-07-20
Hi Wyliecoyoteuk

Thanks very much for that useful lead. I went into the official ubuntu documentation site for CUPS and found how to install the CUPS package then used the link
[http://localhost:631/printers](http://localhost:631/printers) to modify the printer from local to network and lo and behold the printer now works ! 

Thanks again for the prompt post.
Regards Mike

---

### Post by kurt18947 on 2015-07-20
I suspect it matters which 'flavor' of Ubuntu you're using but for Ubuntu-gnome & Xubuntu I install a package from the repository called " system-config-printer-(common, gnome, udev) as part of my initial install. This adds a number of administrative shortcuts, one of which is connection type & address.

---

