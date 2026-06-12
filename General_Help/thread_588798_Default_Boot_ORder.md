---
title: "Default Boot ORder"
date: 2007-10-23
forum: General Help
---

### Post by LinuxNewb092 on 2007-10-23
How do I make WIndows be the default boot instead of Ubuntu?

---

### Post by Denn1s on 2007-10-23
linux uses GRUB as a boot loader, as sudo you have to edit the configuration file wich is /boot/grub/menu.lst 
here you can change the line that says 
default		0
to something like
default		3 
or wichever line your other OS is

---

### Post by LinuxNewb092 on 2007-10-23
Ok, well Im new to Linux, how do you edit this file?

---

### Post by gargo2000 on 2007-10-24
To edit your Grub Menu List use the following code:

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by basacis on 2007-11-13
Thanks this is exactly what I have been looking for. I had the right idea but I was not using sudo and I could not figgure out how to edit the file with VI.

---

