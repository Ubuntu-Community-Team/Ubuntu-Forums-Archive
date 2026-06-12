---
title: "A problem after changing tty resolution"
date: 2008-05-02
forum: General Help
---

### Post by desper on 2008-05-02
Dear all,

I changed my tty resolution by 

1) adding fbcon & vesafb to /etc/initramfs-tools/modules
2) uncomment the line vesafbin /etc/modprobe.d/blacklist-framebuffer
3) updating initamfs and write vga=791 to grub menu.lst

After these steps and a reboot, I got 1024*768 resolution in terminal. The problem is in X,  there are two small black squares now having their residence at the top of my screen. 

My video card is ati mobility 7000 (m6), ibm lcd panel. it is a ibm x31 laptop

Perhaps I can remove them through undoing above steps likely, but I am wondering whether there is a working around method.  


Thank you all.

desper

---

