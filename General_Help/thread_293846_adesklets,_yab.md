---
title: "adesklets, yab"
date: 2006-11-05
forum: General Help
---

### Post by wynutter on 2006-11-05
Heya,

I've been trying to get the yab adesklet to work on my computer. I have downloaded the relevant things and installed them. I have tested YAB and it comes up happily on my desktop. I tell it to register and then try to restart adesklets and it does nothing. I call

adesklets -i

and it gives me the following error:


Traceback (most recent call last):
  File "/usr/bin/adesklets_installer", line 631, in ?
    if globals()['%sGUI' % ui](): break
KeyError: 'TkGUI'



Help?

Austin

---

### Post by Don_DiZzLe on 2006-11-15
I also get this same error, do i need to install python-tk ?

---

### Post by Kandinsky on 2006-11-22
Yes,

you need python-tk for this

---

