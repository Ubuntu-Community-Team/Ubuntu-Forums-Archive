---
title: "grub loader"
date: 2007-12-08
forum: General Help
---

### Post by ameba on 2007-12-08
h

---

### Post by rsambuca on 2007-12-08
You can change the timeout line in your menu.lst file.  To do this, use the gedit text editor program, with gksudo for root permission.```
gksudo gedit /boot/grub/menu.lst
```Find the line that says:

> timeout          10

And change the number to whatever you want, in seconds.  ie, 1 or 2 if you want quicker booting.

---

### Post by ameba on 2007-12-08
is

---

### Post by rsambuca on 2007-12-08
The menu.lst is accessed in order to boot the linux kernel.  If you want to hide it, you can change the timeout line to 1, and remove the number sign '#' from in front of the line that says 

#hiddenmenu

Then it will not show the menu, and will only be on it for one second.  I have never tried it, but you can try putting a zero onto the timeout line and see if that works as well.

---

### Post by ameba on 2007-12-08
o

---

### Post by rsambuca on 2007-12-08
I don't see why it wouldn't work.

---

### Post by ameba on 2007-12-08
h

---

### Post by rsambuca on 2007-12-08
REMOVE the number signs.  It should just look like this:

hiddenmenu

---

### Post by PmDematagoda on 2007-12-08
When an # is put in front of an entry it gets commented which means GRUB will not read it, so why are you trying to add another # when it will not make any difference?

Just remove the # in front of the line as stated by rsambuca, then your problem will be fixed.

---

### Post by Herman on 2007-12-08
If you want to see what rsambuca is saying with an illustration, here it is, [Hiding the GRUB menu during bootup]("http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu")

Regards, Herman :)

---

### Post by PmDematagoda on 2007-12-08
> **Herman said:**
> If you want to see what rsambuca is saying with an illustration, here it is, [Hiding the GRUB menu during bootup]("http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu")

Regards, Herman :)

Hey nice guide Herman, it would be really useful, thanks:).

---

### Post by ameba on 2007-12-08
w

---

### Post by rsambuca on 2007-12-08
> **PmDematagoda said:**
> When an # is put in front of an entry it gets commented which means GRUB will not read it, so why are you trying to add another # when it will not make any difference?

Just remove the # in front of the line as stated by rsambuca, then your problem will be fixed.

Again.  Wow.

---

### Post by PmDematagoda on 2007-12-08
For the love of god[-o<, just remove the # in front of the entry for Hiddenmenu. That is all, look at what I said previously, it explains why you should.

EDIT:- Ok, then calmly tell us what you did.

---

### Post by ameba on 2007-12-08
t

---

