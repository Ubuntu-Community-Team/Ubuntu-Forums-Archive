---
title: "Help with editing menu.lst [Resolved]"
date: 2007-02-18
forum: General Help
---

### Post by Willie G on 2007-02-18
I tried to edit the file menu.lst in the terminal with
the command 'edit /boot/grub/menu.lst' preceded
by sudo, gksudo, sudo nano, etc,etc,etc, and nothing
works.
Can someone please tell me the proper command to 
edit and save the file 'menu.lst' from the terminal?

If I try to edit the file itself for some reason I need
root privileges.

---

### Post by aysiu on 2007-02-18
The proper commands would be ```
gksudo gedit /boot/grub/menu.lst
``` for Ubuntu ```
kdesu kate /boot/grub/menu.lst
``` for Kubuntu or ```
sudo nano -B /boot/grub/menu.lst
``` for either. Read more here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by taurus on 2007-02-18
```
sudo nano -Bw /boot/grub/menu.lst
```
When you are done, press <Ctrl>x, then Y and Return.

---

### Post by aysiu on 2007-02-18
> **taurus said:**
> ```
sudo nano -Bw /boot/grub/menu.lst
```
When you are done, press <Ctrl>x, then Y and Return.
Interesting. What does the *w* option do? I know *-B* makes a backup copy.

---

### Post by taurus on 2007-02-18
In case line that's longer than 80 characters, it won't wrap around to the next line.

---

### Post by aysiu on 2007-02-18
> **taurus said:**
> In case line that's longer than 80 characters, it won't wrap around to the next line.
Cool. Good to know.

---

### Post by Willie G on 2007-02-19
Thanks everyone, I edited menu.lst and now I have 
a good Vista/Ubuntu dual boot.

---

