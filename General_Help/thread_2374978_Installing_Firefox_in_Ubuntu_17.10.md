---
title: "Installing Firefox in Ubuntu 17.10"
date: 2017-10-20
forum: General Help
---

### Post by Hewjr100 on 2017-10-20
In earlier version of Ubuntu I could install Firefox using this tutorial:  [http://libre-software.net/how-to-install-firefox-on-ubuntu-linux-mint/](http://libre-software.net/how-to-install-firefox-on-ubuntu-linux-mint/)  This does not work anymore.  I'm assuming there is a way to install Firefox in the Gnome version but I cannot find it.

Henry

---

### Post by VMC on 2017-10-20
What doesn't work? Did you install it on /opt? I use the Nightly and install it on another partition and just link the firefox to my desktop. Works fine. I'm using xubuntu 17.10
Try running the program from a terminal and see if any error messages appear.

---

### Post by Hewjr100 on 2017-10-20
Yes, using the link above I uncompressed it and moved it to /opt.  Next is to rename Firefox link to old, then sym link to Firefox.  Nothing doing in terminal.  Even tried cd/opt/firefox55/firefox then ran from then ran firefox and all I get is Firefox is not installed.  Removed cd/opt firefox55 and went back to default Firefox.  BTW before you ask I use the name firefox55 because the instructions are for firefox 55 and it makes it faster to use the default examples.  See link above.  This is the same way I did it in Ubuntu 17.04 and earlier and it always worked.

Henry

---

### Post by VMC on 2017-10-21
So using nautilus, you went to "/opt/firefox55" and double-click on the executable file "firefox". And nothing worked?

---

### Post by Hewjr100 on 2017-10-21
Using the command line cd/opt/firefox55,  then sudo firefox enter, said firefox not installed.

Henry

---

### Post by vasa1 on 2017-10-21
Why sudo firefox :???:

---

### Post by &amp;KyT$0P# on 2017-10-21
> **Hewjr100 said:**
>  sudo firefox enter, said firefox not installed.
There's your problem.  Firefox is not located in [FONT=Courier New]$PATH[/FONT], so your shell can't find it.  Try running Firefox like this -
```
/opt/firefox55/firefox
```
or like this -
```
cd /opt/firefox55
./firefox
```

---

### Post by Hewjr100 on 2017-10-21
Will try it later, Cablevision is coming.  Have to deal with it later.

---

