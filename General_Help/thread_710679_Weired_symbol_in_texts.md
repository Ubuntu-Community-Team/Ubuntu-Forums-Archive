---
title: "Weired symbol in texts"
date: 2008-02-28
forum: General Help
---

### Post by StOoZ on 2008-02-28
sometimes I ran into this weired symbol, never in firefox,or in the ubuntu itself, but only on texts (chm) and when chatting in IRC, I woder how to solve this:
[IMG]http://img81.imageshack.us/img81/25/fontsoi0.jpg[/IMG]


thanks alot.

---

### Post by pointone on 2008-02-29
It's an unrecognized character. Not sure how you could fix it, though. Installing additional fonts (msttcorefonts) or using a different encoding many work.

---

### Post by StOoZ on 2008-03-01
how do I changed the econding???

I remember installing (msttcorefonts) , so I already have it.

---

### Post by y-lee on 2008-03-01
I have the same problem with certain programs but i ignored it. 

Anyway I think to change character encoding 

```
dpkg-reconfigure locales
```

But for the program you appear to be using that may not work. From the[ xChm web site]("http://xchm.sourceforge.net/faq.html")

> **Q:** How can I get xCHM with Uncode support? My chm documents are displayed all messy (I get squares for characters no matter what font face I choose).

**A: **This is not about xCHM, but about wxWidgets. You need to compile wxWidgets with Unicode support, and then re-configure and build xCHM. You can instruct wxGTK that you want it to use Unicode by issuing:

```
./configure --enable-gtk2 --enable-unicode
```

in the root wxGTK source directory.

If you received xCHM as part of a Linux or BSD distribution, you might try to ask your distribution maintainers to provide a Unicode-able xCHM package instead of the one you have

---

### Post by Michael Schmidt on 2008-06-24
I have downloaded xchm for Hardy and got the same weird characters when I viewed a .chm file.  From this thread and other discussions on the web, this appears to be because it is not Unicode enabled.  The advise is to ask the distribution maintainers to provide a Unicode-enabled version of xchm.  So, would the Ubuntu folks do this?

I continued to struggle with the problem today and came across a review of Linux .chm viewers.  The author recommended KchmViewer (available via Synaptic Package Manager).  Problem solved!  It has a very slick GUI and, most importantly, there is an option to select language - and Unicode is one of the choices.  My problem-child .chm file cleaned right up.

---

