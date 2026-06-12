---
title: "how to switch to sudo user?"
date: 2007-01-21
forum: General Help
---

### Post by bone2006 on 2007-01-21
I've been trying searching for about an hour on how to run konqueror with root privilege and nothing works.

kdesu konqueror does not work and it crashes

The instructions provided by konqueror don't work either " To start Konqueror in super user mode, click on Start menu button, go to Start Menu >System Tools > More System Tools and then click on File Manager Super User Mode."

No such thing as the file manager super user mode and there's no such thing as system tools either.   I haven't done one single thing except install a fresh copy of kubuntu............. kind of disappointing that the help section is wrong and I'm not sure what to do?

---

### Post by norman_ on 2007-01-21
I find it strange you can't start it simply with "sudo konqueror" in the terminal. Works for any apps in my ubuntu (gnome) install.

---

### Post by bone2006 on 2007-01-21
for some reason it complains and the samething with kate.  For gnome I've read your supposed to type in gksudo for graphical applications............. the command doesn't work in kde and haven't been able to find out.

So far the only solution I've found is to reboot and select recovery and while in this mode I'm able to act as root.

---

### Post by norman_ on 2007-01-21
> **bone2006 said:**
> for some reason it complains and the samething with kate.  For gnome I've read your supposed to type in gksudo for graphical applications............. the command doesn't work in kde and haven't been able to find out.

So far the only solution I've found is to reboot and select recovery and while in this mode I'm able to act as root.

I recommend reading this: [http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html)

we need more details. what does it complain about?

---

### Post by bodhi.zazen on 2007-01-21
> **bone2006 said:**
> for some reason it complains and the samething with kate.  For gnome I've read your supposed to type in gksudo for graphical applications............. the command doesn't work in kde and haven't been able to find out.

So far the only solution I've found is to reboot and select recovery and while in this mode I'm able to act as root.

For graphical programs use gksudo

Ex: gksudo kate

---

### Post by TheWizzard on 2007-01-21
> **bodhi.zazen said:**
> For graphical programs use gksudo

Ex: gksudo kate
this is for gtk progs. 
both 
```
sudo konqueror
kdesu konqueror
```
should work. please post the konsole output.

---

### Post by bodhi.zazen on 2007-01-21
> **TheWizzard said:**
> this is for gtk progs. 

Oh, so that's where 'gk' comes from. I had no idea. 

THANKS FOR THE INFO :p

---

### Post by aysiu on 2007-01-21
Please post the output of ```
kdesu konqueror
``` That should work. Do **not** use *sudo* with Konqueror or any graphical application.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) for more details.

---

### Post by TheWizzard on 2007-01-22
> **aysiu said:**
> 
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) for more details.

thanks for the information.

---

### Post by Zill on 2007-01-22
> **bone2006 said:**
> I've been trying searching for about an hour on how to run konqueror with root privilege and nothing works.
kdesu konqueror does not work and it crashes

I have had similar problems with kdesu konqueror and have tried various things to get it working reliably.  It seems to be buggy in Dapper at least.

Suggest you run kdesu konqueror in a terminal window and see what error messages are produced.  I found that commenting-out wacom references in xorg.conf seemed to help (save a copy first!).  See the following links for more info:

[http://kubuntuforums.net/forums/index.php?topic=7964](http://kubuntuforums.net/forums/index.php?topic=7964)
[http://ubuntuforums.org/showthread.php?p=1264009#post1264009](http://ubuntuforums.org/showthread.php?p=1264009#post1264009)

---

### Post by Tilex on 2007-02-15
I've had similar problems, and none of the abovementionned commands works.  Here's my terminal output:
```

Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
kdesu: cannot connect to X server :0.0

```

Any thought?

---

### Post by Zill on 2007-02-16
My problem with kdesu konqueror seems to be resolved with the following...
```
sudo killall kdeinit
```
Then logout and login.

However, this does not seem to be a permanent fix as the problem can re-occur later.  I just run the code again and all is well for a few more days or weeks :confused:

---

