---
title: "Dell inspiron 1525 desktop effects"
date: 2008-06-16
forum: General Help
---

### Post by fatherdaly on 2008-06-16
Ok so this is a laptop bought directly from Dell with ubuntu preinstalled, and when I try and enable Desktop effects I get this screen:

[[IMG]http://img233.imageshack.us/img233/146/screenshotep7.th.png[/IMG]](http://img233.imageshack.us/my.php?image=screenshotep7.png)

It just says it can't do it... is this because the graphics processor simply cannot handle it?

Or can I do something about it?

The graphics card is called an: "Integrated Intel® Graphic Media Accelerator X3100"

---

### Post by karasuman on 2008-06-16
I had this exact same problem.  (I have the same computer from Dell.  Mine's green!)  It vanished completely when I upgraded to Hardy.  

The only new problem upgrading gave me was that my sound control stopped working, but it didn't take me long to fix that.  You just need to install a program called alsamixer and edit the maximum volume setting in there by opening the terminal, typing alsamixer, and using your mouse.  :)

---

### Post by prshah on 2008-06-16
> **fatherdaly said:**
> when I try and enable Desktop effects 
It just says it can't do it... 

Or can I do something about it?




Open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here. ```

compiz --replace

```

---

### Post by fatherdaly on 2008-06-16
ok here's what it said:

```
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by prshah on 2008-06-16
> **fatherdaly said:**
> 
```
Checking for Xgl: not present. 

```

Open a terminal (Applications-Accessories-Terminal), then give the following command ```

sudo apt-get install xserver-xgl

```

Then, close, logout, and restart X with Ctrl_Alt_BkSpace. Login and try to enable desktop effects the GUI way, and if it fails, the terminal way. If it still doesn't work, post back with messages/output.

---

### Post by fatherdaly on 2008-06-16
thanks, it worked.

---

### Post by prshah on 2008-06-16
> **fatherdaly said:**
> thanks, it worked.

OK! Please mark the thread solved; click on "Thread Tools" _near_ the top right hand side of the page, then select "Mark Thread as Solved".

---

