---
title: "Cannot access Qalculate help"
date: 2016-07-04
forum: General Help
---

### Post by &amp;KyT$0P# on 2016-07-04
On Xubuntu 16.04, Qalculate's Help > Contents menu item is grayed out, and pressing the associated keystroke (F1) does nothing.  I just installed qalculate-gtk from the normal Ubuntu repositories through Synaptic.
How to get this menu item enabled and access Qalculate's help documentation?

---

### Post by him610 on 2016-07-04
You can use Synaptic to download the documentation for Qalculate.

---

### Post by &amp;KyT$0P# on 2016-07-04
Thanks but I don't see a documentation package?
*[deleted screenshot; help documentation is part of the qalculate-gtk package]*

---

### Post by QDR06VV9 on 2016-07-04
Here is a online manual :[http://qalculate.sourceforge.net/manual/index.html](http://qalculate.sourceforge.net/manual/index.html)

---

### Post by &amp;KyT$0P# on 2016-07-04
Thank you runrickus that will work in the mean time.

BTW I found a package [libqalculate-doc]("http://packages.ubuntu.com/xenial/libqalculate-doc") but installing it did not help :(

---

### Post by QDR06VV9 on 2016-07-04
Your Welcome...but libqalclate-doc is data needed for more options is all.
And the on-line manual is better in my opinion and the only other entry in the Help Tab was "about[SIZE=2] Qalculate[/SIZE]"  
Kind Regards

---

### Post by &amp;KyT$0P# on 2016-07-04
Now this is interesting - I installed qalculate-gtk in my Lubuntu 14.04 and there the Help menu item works fine.  (It opens in the Gnome help browser.)
No idea what that means for making it work in Xubuntu 16.04 though?

@runrickus: as I was browsing that help site you linked, I got a notice that Qalculate moved to Github: [https://qalculate.github.io/manual/index.html]("https://qalculate.github.io/manual/index.html")

---

### Post by QDR06VV9 on 2016-07-04
> **halogen2 said:**
> Now this is interesting - I installed qalculate-gtk in my Lubuntu 14.04 and there the Help menu item works fine.  (It opens in the Gnome help browser.)
No idea what that means for making it work in 16.04 though?

@runrickus: as I was browsing that help site you linked, _**I got a notice that Qalculate moved to Github**_: [https://qalculate.github.io/manual/index.html](https://qalculate.github.io/manual/index.html)

Yep! so did I.
Just a redirect to the new location.
And yes the help menu is in trusty and i do not have it installed yet in yakkety(16.10)

---

### Post by &amp;KyT$0P# on 2016-07-11
Forgot to post I found a work-around to access the local help.  Running this in a Terminal seems to work
```
yelp /usr/share/gnome/help/qalculate-gtk/C/qalculate-gtk.xml
```

Yeah, the online documentation is easier to browse :p  marking this thread solved

---

