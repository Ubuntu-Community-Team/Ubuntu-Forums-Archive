---
title: "Grub Help"
date: 2006-08-15
forum: General Help
---

### Post by Alien56 on 2006-08-15
I am using Ubuntu and Fedora Core 5 with grub as my boot manager. I have Windows XP and Fedora in the grub.conf file and I need to know how to add Ubuntu. Does anyone know how?

---

### Post by Tomosaur on 2006-08-15
Try running 'sudo update-grub' in the terminal.

---

### Post by Alien56 on 2006-08-15
Should I be at root@localhost?, or in some other directory becasue I tried it at root@localhost and it didn't work. Also if it has to be in another directory how do I switch to another directory?

---

### Post by kaens on 2006-08-16
if you're root, then you don't need the sudo. You should avoid being root though.

---

### Post by Alien56 on 2006-08-16
Unfortuantely that did not work. The terminal didn't recognize that as a command. I don't know if I made it clear or not but I'm trying to get Ubuntu to work in grub, but I'm only able to access Fedora right now.

---

### Post by Tomosaur on 2006-08-16
Ah I see. I think the grub setup should be the same. If you have a file called menu.lst in /boot/grub, you will need to add a few lines to get Ubuntu showing up, but the lines you need to add will depend on your hard drive configuration, and the kernel you're using.

---

### Post by tommcd on 2006-08-16
See this for comprehensive grub help:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Scroll down to "operating system entries". You will have to add ubuntu with your current kernel to menu.lst. Follow the format shown. This should allow you to boot ubuntu.
Hope this helps.

---

### Post by Alien56 on 2006-08-16
If I have ubuntu 2.6.15-23-386, installed on my only hard disk and "/" being on partition 2 and "/home" on partition 3 how would I setup grub?

---

