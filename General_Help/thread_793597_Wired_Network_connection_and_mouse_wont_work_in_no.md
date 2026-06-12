---
title: "Wired Network connection and mouse wont work in normal starup"
date: 2008-05-13
forum: General Help
---

### Post by grimlock838 on 2008-05-13
Wired Network connection and mouse wont work in normal start up. 
They only work by hitting esc @ grub startup screen and when I select Ubuntu generic and selecting x recovery and resume normal start up. 
But If I just startup normal, the Wired Network connection has an x over it and the mouse. doesnt respond, despite it lighting up (optical mouse). What install log do I need to look at to narrow down whatever did this? And why will the mouse work when I run the xrecovery and resume noraml startup??

---

### Post by pointone on 2008-05-13
Very odd. The mouse behaviour could possibly be due to your X.Org configuration. Try running:

```
sudo dpkg-reconfigure xserver-xorg -phigh
``` 

...to regenerate your xorg.conf file.

This wouldn't affect the networking, however. A problem with ACPI might explain both oddities. Try booting with the "noacpi" boot option and see if this solves the problem.

---

