---
title: "how to send a font by email"
date: 2013-11-02
forum: General Help
---

### Post by gufghur on 2013-11-02
Hi all,

I've sent some text and a .jpg to a friend so he could put them together professionaly. He now asks me to email him the font since he hasn't got it installed. He tried to explain me how to do this, but since he uses windows, his help is useless. Can anyone of you help me out?

---

### Post by Frogs Hair on 2013-11-02
How is the font packaged or is it ? If it is a font from a web page a link might do and the person could install it  from the site.

---

### Post by drmrgd on 2013-11-02
Have a look at this link for some information about font management in Ubuntu:

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

I've done this before, sharing fonts between Linux and Ubuntu, and it's a simple matter of finding where the font is stored on your system (see the 'Manually' section of that link), and then sending him a copy of that file.  If it's something like a TTF font, then your friend will simply need to install that font on his system by right clicking on it and selecting something like "install font" (don't have a Windows computer close by to get the exact command at the moment).  The hardest part will be finding the font as it could be in one of a few different locations on your system.

---

### Post by Lars Noodén on 2013-11-02
Is it a TrueType font?  If so, those should be in /usr/share/fonts/truetype/ and you can just browse down to the file you need.

---

### Post by gufghur on 2013-11-02
oke, this seems promising ... I'll try it out.

---

### Post by gufghur on 2013-11-02
suddenly I had the luminous idea to type "font" in the dash and what appeared before my very own eyes ...? Yes font manager, and a simple copy to desktop did the trick.

... that is, if this is enough ... it's hard to be a computerneanderthaler in a digital age ...:(

But thanks guys!

---

### Post by Dennis N on 2013-11-02
> **gufghur said:**
> Hi all,

I've sent some text and a .jpg to a friend so he could put them together professionaly. He now asks me to email him the font since he hasn't got it installed. He tried to explain me how to do this, but since he uses windows, his help is useless. Can anyone of you help me out?

Each font is a file that can be copied, pasted, or attached to email like any other file.
They live in **/usr/share/fonts** or **~/.fonts** for the most part.


To send, attach the file to your email message and let the recipient worry about how to install it.

---

