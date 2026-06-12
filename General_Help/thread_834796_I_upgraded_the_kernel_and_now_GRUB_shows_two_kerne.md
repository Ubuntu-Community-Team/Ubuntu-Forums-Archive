---
title: "I upgraded the kernel and now GRUB shows two kernel versions.. how to fix?"
date: 2008-06-19
forum: General Help
---

### Post by Redrazor39 on 2008-06-19
Is there an easy and safe way to delete the older kernel or at least hide it? It's so annoying to have so much crap in GRUB when I only have two OSs.

---

### Post by raul_ on 2008-06-19
you can edit /boot/grub/menu.lst

and comment the lines of the old kernels.

Backup first

---

### Post by Redrazor39 on 2008-06-19
When you say comment, you mean put a # at the beginning of the line, right?

and how could I back this up?

---

### Post by fooman on 2008-06-19
correct about comment being a # in front of the line.

and to back up the file *before* you edit it....run this in a terminal:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```

---

### Post by Butthead on 2008-06-19
Just cut them out with a text editor.

Even easier is just use whatever flavor of package manager you happen to have (Adept, Synaptic?) to delete the old kernels (and their corresponding crap), and a new Grub menu will automagically be rebuilt for you (with the old kernels gone from it).

---

### Post by Redrazor39 on 2008-06-19
I am using kubuntu (first day using it and really trying to figure it out) so I have Adept.

So, if I just search in Adept for that kernel number, will it appear and I can uncheck it or is the old kernel (version 2.6.24-16) deleted another way in Adept?

---

### Post by raul_ on 2008-06-20
Uncheck it

---

### Post by drs305 on 2008-06-20
If you are looking for a safe method to edit menu.lst and limit the number of kernels displayed on boot install and use StartUp-Manager. It's gui based app to edit menu.lst without editing it yourself and possibly messing it up.

Here's how to use it:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by pPrdrm on 2008-06-20
By editing the /boot/grub/menu.lst you will only remove the grub entry of that kernel version. But if you want to uninstall the old kernel also, then you should uninstall it via Synaptic. That way you will remove the kernel and the entry of it at Grub menu clearing some MB on your hard drive.

---

### Post by Redrazor39 on 2008-06-20
Thanks for all the help, everyone! I uninstalled kubuntu because I totally screwed up my installation, but I'm gonna give it another go. This time, I'll be more careful about how I install the new KDE.

Then, I'll do a full upgrade. If this happens again, I'll try your methods and try to post about how that goes.

---

