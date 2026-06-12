---
title: "Successful dual boot with Windows, but how do I make Windows default"
date: 2008-04-29
forum: General Help
---

### Post by mistergoomba on 2008-04-29
So, I successfully have my dual boot set up, and I'm glad to say that it was really easy!

I am running Hardy on my work laptop and need to run Windows at work (Linux at home). My question is, at the boot screen, there is a 10 second timer that will choose Ubuntu from the top of my list. How do I get Windows to this top position?

Thanks in advance.

---

### Post by btmiller on 2008-04-29
Look in your /boot/grub/menu.lst file for the line that looks like "default  0". You can change the default to any of the entries in the menu.lst. Remember that the numbering of entries in the file starts from 0, so if your Windows installation is the second entry, you would set the default to be 1.

---

### Post by mistergoomba on 2008-05-01
perfect, thanks!

---

### Post by MVF on 2009-06-04
> **btmiller said:**
> Look in your /boot/grub/menu.lst file for the line that looks like "default  0". You can change the default to any of the entries in the menu.lst. Remember that the numbering of entries in the file starts from 0, so if your Windows installation is the second entry, you would set the default to be 1.
Thank you for the dlear information. But when I put "/boot/grub/menu.lst" in the command line, I get a "permission denied" message.

---

### Post by Chronon on 2009-06-04
What do you mean by "put in the command line", exactly?

---

### Post by t4ggs on 2009-06-04
> **MVF said:**
> Thank you for the dlear information. But when I put "/boot/grub/menu.lst" in the command line, I get a "permission denied" message.

do the following: sudo gedit /boot/grub/menu.lst

it seems to me that u r trying to edit menu.lst without administrator rights...thats what the sudo command is for
after u enter it, it will ask u for the password, then just edit menu.lst and save...it should work

---

### Post by nebileix on 2009-06-04
> **MVF said:**
> Thank you for the dlear information. But when I put "/boot/grub/menu.lst" in the command line, I get a "permission denied" message.

```
$ sudo gedit /boot/grub/menu.lst
```

Try these if u haven't.

---

