---
title: "Several problems due dependecies and System failed"
date: 2015-09-20
forum: General Help
---

### Post by dan91av on 2015-09-20
Hi,
thank you for who will read this and will help me.
The story is quite long but I'll resume briefly. I wanted do cancel Python 2.7 version to keep only the newest one, without knowing about dependencies problem. So when I did this, my system started to have problems (due to errors I couldn't 'apt-get install' nothing, then my wifi connections stopped to work) till I shutted down the computer. Now when I start Ubuntu (14.04) it stops at the initial phase of loading (the one with the ubuntu logo): it stucks. If I go to ctrl-alt-f2 mode I am limited (I have no internet connection). So I'd like to reinstall ubuntu through usb, but when I go to ' /media ' it seems not finding my usb drive. How can I change my boot order without it? Or which would be the better solution?
I'm really confused and impressed about the problem with python dependencies but I didn't know it, so I really thank who will help me.

---

### Post by ian-weisser on 2015-09-20
Your 14.04 system NEEDS Python2.7. Several important elements of your system depend upon it; their migration to Python3 was not yet complete when 14.04 was released.
Yes, that means your 14.04 must have BOTH Py2.7 and Py3 installed.

I do not understand the problem you are encountering trying to reinstall.
You don't mount the install media - you boot from it.

---

### Post by dan91av on 2015-09-20
The problem now is that my Ubuntu doesn't work anymore: when I turn on my pc ubuntu is stucked in the initial phase, and I can only use the verbal mode forcing (ctrl-alt-f2). In this verbal mode I have no more internet connection.
How can I boot from it?(usb)

---

### Post by ian-weisser on 2015-09-20
> **dan91av said:**
> How can I boot from it?(usb)

The same way you booted from it when you installed Ubuntu.

Poweroff system.
Insert USB
Poweron system
Look carefully for BIOS/EFI boot menu key (F12 or such)
Change BIOS/EFI to boot from USB instead of HDD

---

### Post by dan91av on 2015-09-20
Thank you. Now I'm in the ' Try Ubuntu without installing' mode and I would like to retrieve and copy data on usb before new installation. I am searching on community, if you can give some hints I'll be pleasured.
Thank you again

---

### Post by ian-weisser on 2015-09-20
Copy data onto a different USB? (easier)
Or copy data onto a different partiton of the install USB? (harder)

---

### Post by dan91av on 2015-09-20
Yes, I am copying onto a different usb, the unique problem was changing permissions to files, but seems solved. Hope that with next installation will finish this story.
Really thank you.

---

