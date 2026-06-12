---
title: "Optimizing the boot process"
date: 2008-04-17
forum: General Help
---

### Post by GordonFreeman on 2008-04-17
Hi,
I want to speed up my boot process, but I don't know where to start. Is there some kind of log file which displays all the processes going on when booting and how long they took?
My system does not take very long to get past the XUbuntu boot logo with the progress bar, but after lunching the gnome display manager and till I can enter my password it takes quite some time, so I wanted to check what it is doing then, because I'm very sure that I didn't take that long in the past.

I'm loading at startup only the gnome libraries, not the KDE libraries.

And I'm using XUbuntu 7.10



Thanks.

---

### Post by Het Irv on 2008-04-17
```
sudo apt-get install bootchart
```

this is a program that gives you a visual graph of what processes are running during boot and for how long.  It will store the charts in /var/log/bootchart

EDIT: something just caught me in your post, you say you are using Xubuntu which installs the XFCE desktop by default.  But then you said that you are running GNOME. Is this right?

---

### Post by psyke83 on 2008-04-17
> **GordonFreeman said:**
> Hi,
I want to speed up my boot process, but I don't know where to start. Is there some kind of log file which displays all the processes going on when booting and how long they took?
My system does not take very long to get past the XUbuntu boot logo with the progress bar, but after lunching the gnome display manager and till I can enter my password it takes quite some time, so I wanted to check what it is doing then, because I'm very sure that I didn't take that long in the past.

I'm loading at startup only the gnome libraries, not the KDE libraries.

And I'm using XUbuntu 7.10



Thanks.

To get you started:

[LIST]
[*]Check your boot time with bootchart: ```
sudo apt-get install bootchart
``` On successive reboots, check, /var/log/bootchart

[*]Reprofile your bootup: [http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

[*]Do a search of the forums for similar posts...
[/LIST]

---

### Post by GordonFreeman on 2008-04-17
> **Het Irv said:**
> ```
sudo apt-get install bootchart
```

this is a program that gives you a visual graph of what processes are running during boot and for how long.  It will store the charts in /var/log/bootchart

EDIT: something just caught me in your post, you say you are using Xubuntu which installs the XFCE desktop by default.  But then you said that you are running GNOME. Is this right?

My Desktop is XFCE yes, but it still uses gdm for the login screen.
And the Gnome libraries are loaded at runtime for the gnome applications, so they're already in memory when starting gnome applications. For example the NetworkManager applet XUbuntu ships with it is the gnome NetworkManager applet.


Ok thank you :-)

---

### Post by Het Irv on 2008-04-17
ahh, okay that makes sence, I haven't used Xubuntu much and that was tripping me up a bit.

---

### Post by GordonFreeman on 2008-04-18
The bootchart says that the boot process takes 22seconds. I think thats a pretty good time, or in other words there won't be much to optimize, right?

---

### Post by SnakeHips on 2008-04-18
[QUOTE=
[LIST]
successive reboots, check, /var/log/bootchart
[/LIST][/QUOTE]

You might want to check this folder after a while (disk space) ,it fills up with bootlogs after a while ;-)

---

### Post by GordonFreeman on 2008-04-18
Yeah, I will do that and if the boot time stays at 22seconds I will remove the bootchart app, or is there a way to disable it?

---

