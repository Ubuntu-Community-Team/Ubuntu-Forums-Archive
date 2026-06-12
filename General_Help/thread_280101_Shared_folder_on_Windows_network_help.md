---
title: "Shared folder on Windows network help"
date: 2006-10-18
forum: General Help
---

### Post by cptjaben on 2006-10-18
I'm on my families home network, which consists of my computer(running ubuntu)and 3 other computer with windows on them. I've managed to share a folder on the windows network, but when I try to access it, It asks for a username and password which I do not have, I never was asked to set a username and password nor can I find where to do it. In addition, my root login does not work. How do I set a username and password for this shared folder so that i can access it or how do I make it so that the folder does not need a username and password? Thanks

---

### Post by elpuerco on 2006-10-19
A complete stab in the dark here, but when you create the share on Windows does it not ask you for the user names of those allowed to connect?

---

### Post by Iowan on 2006-10-19
> **cptjaben said:**
> how do I make it so that the folder does not need a username and password? Thanks
One option (not necessarily the best - or even good) is to change (or set) **security=share** in the **/etc/samba/smb.conf** file. Then you'll need to restart Samba.

---

### Post by cptjaben on 2006-10-19
Thanks for the help, would anyone happen to know the command the restart Samba?

---

### Post by beerorkid on 2006-10-19
> **cptjaben said:**
> Thanks for the help, would anyone happen to know the command the restart Samba?

sudo /etc/init.d/samba restart

---

### Post by cptjaben on 2006-10-19
thanks for the help everyone

---

