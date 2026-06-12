---
title: "grub error 15 file not found"
date: 2007-08-22
forum: General Help
---

### Post by Naegling23 on 2007-08-22
ok, i know grub has been talked about before, but I cant seem to find a solution to my seemingly simple problem.  I have been fighting with grub for a week or so, and Im very close to having everything fixed.  I recently swapped out the hard drive containing my mbr, and did a grub instal.  Now, grub thinks that my linux kernal is on hd2,0.  When it boots, I get an error 15, file not found.  I can edit the item by hitting e, and changing it to boot from hd0,0.  The only thing is that I want to save this change, so that it tries to boot from hd0,0 everytime, instead of having to manually change it.  So how do I do this?  Is this what chainloader in menu.lst is?

---

### Post by merlinus on 2007-08-22
```

gksudo gedit /boot/grub/menu.lst

```Change the linux stanzas to (hd0,0).

-merlin

---

### Post by Naegling23 on 2007-08-23
you missed a step:

sudo apt-get instal gedit ;-)

thanks though, that was the answer I was looking for

---

### Post by merlinus on 2007-08-23
Glad it worked.  gedit was installed with ubuntu 7.04 for me.

-merlin

---

