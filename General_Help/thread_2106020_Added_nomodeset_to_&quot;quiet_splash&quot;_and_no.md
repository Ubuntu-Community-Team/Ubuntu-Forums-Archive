---
title: "Added nomodeset to &quot;quiet splash&quot; and now GUI won't start..."
date: 2013-01-17
forum: General Help
---

### Post by buffalo05 on 2013-01-17
Apologies if this is answered somewhere, but I've had no luck finding it if it was.

Anyways, I was having brightness control issues on my HP G7, and tried adding nomodeset to the grub. On reboot, I'm taken to the tty1 login and cannot get to the GUI/desktop. I've tried "startx," "alt+F7," and "install desktop."

Is there a simple way I can edit the grub and undo nomodeset from the "quiet splash" without the text editor?

Thanks for the help.

---

### Post by dabl on 2013-01-17
Well, "simple" is kinda in the eye of the beholder ....

Do you have the nano package installed?

```
sudo apt-cache policy nano
```

If no, install it.  If yes, then what you need to do is change to the directory /etc/defaults and then run

```
sudo nano grub
```

and VERY CAREFULLY cursor down to the line that begins like this:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ..."

and delete your unfortunate addition by backspacing from the right end of the line.

Then you must run 

```
sudo update-grub
``` to change the /boot/grub/grub.cfg file, which changes the menu.

Then ```
sudo shutdown now -r
``` and when it comes back up, the grub menu should not have the nomodeset option and you should get your GUI login same as before.

---

### Post by ibjsb4 on 2013-01-17
To do it on the fly from your grub menu.
Hold down the shift at boot to make grub appear, then hit "e" on the line you normally boot. This will allow you to edit grub. Use the cursor keys go to the line you need to edit.

---

### Post by buffalo05 on 2013-01-17
Thanks for the response. 

Tried this out, and I'm getting an empty grub file. Appreciate your help.

---

### Post by buffalo05 on 2013-01-17
NM, mea culpa. Just needed to "nano /etc/default/grub"

Now, I need to figure out how to exit the grub file :P, heh heh. Thanks for the support, gentlement.


*****
Update:

Alright, fixed! Thanks again!

---

### Post by haqking on 2013-01-17
> **buffalo05 said:**
> NM, mea culpa. Just needed to "nano /etc/default/grub"

Now, I need to figure out how to exit the grub file :P, heh heh. Thanks for the support, gentlement.

ctrl + x

then Y to save

---

### Post by steeldriver on 2013-01-17
*nm - too slow*

---

