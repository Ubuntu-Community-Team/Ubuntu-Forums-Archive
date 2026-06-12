---
title: "Cannot Redirect X Window over SSH"
date: 2014-04-05
forum: General Help
---

### Post by rmccarri on 2014-04-05
Hi Everyone,
I'm running Ubuntu 12.04 64 bit on my work desktop. I have an older OpenSUSU 10.3 computer that runs one of the instruments that I oversee. Typically, I would ssh into my Ubuntu computer with the following type of login:

```
ssh -X user@host
```

and then launch applications from the command line over SSH and have the X windows display for the application divert to the OpenSUSE machine. This worked for years, but recently, I've been getting the error:

```
Gtk-WARNING **: cannot open display:
```

I've checked my sshd_config file on the Ubuntu box and X forwarding is enabled. Has anyone else run into the issue that X forwarding has stopped working?
Thanks in advance for any help.

---

### Post by HermanAB on 2014-04-05
When this happens to me, I log out and log in again to restart Xorg and following that it works again.  There may be a better way to fix it.

---

### Post by rmccarri on 2014-04-05
Thanks for the suggestion! Ounce tried restarting everything, but it's been persisting for a few months.

---

### Post by HermanAB on 2014-04-06
See these:
[http://www.linuxquestions.org/questions/debian-26/gtk-warning-**-cannot-open-display-0-0-a-807450/](http://www.linuxquestions.org/questions/debian-26/gtk-warning-**-cannot-open-display-0-0-a-807450/)
[http://forums.opensuse.org/showthread.php/453089-Using-gedit-as-root-quot-Gtk-WARNING-**-cannot-open-display-quot](http://forums.opensuse.org/showthread.php/453089-Using-gedit-as-root-quot-Gtk-WARNING-**-cannot-open-display-quot)

---

