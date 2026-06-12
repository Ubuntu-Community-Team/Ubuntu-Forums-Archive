---
title: "[SOLVED] System monitor won't launch"
date: 2008-02-20
forum: General Help
---

### Post by Arathon on 2008-02-20
When launched from the GUI, the computer thinks for a few seconds, then nothing happens.  When launched from the terminal, it immediately writes

peter@rebel64-ubuntu:~$ gnome-system-monitor

** (gnome-system-monitor:5673): WARNING **: SELinux was found but is not enabled.

terminate called after throwing an instance of 'Glib::FileError'
Aborted (core dumped)


I couldn't find anything about this anywhere else, but given that I have an error message, I'd think someone would have an idea of what I could do.  This system is not a heavily-modified one, so I'm not sure why I'm having a problem like this.......

---

### Post by happyhamster on 2008-02-20
If you installed custom themes/icons, perhaps your problem is related to:
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/180087](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/180087)

---

### Post by Arathon on 2008-02-20
> **happyhamster said:**
> If you installed custom themes/icons, perhaps your problem is related to:
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/180087](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/180087)

I didn't install anything, but in the process of trying to get Firefox 3 Beta 3 installed, I apparently deleted the system icons for Firefox and had to get some new icons.  I think I'll try deleting those and reinstalling Firefox 2 (hopefully that will restore the old Firefox icons).  If that screws up my Firefox 3 install, though, I'm gonna be mad.  =P

---

### Post by Arathon on 2008-02-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+s...or/+bug/180087](https://bugs.launchpad.net/ubuntu/+s...or/+bug/180087) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Yup, that worked.  I guess it didn't like having to use my Firefox icon.  That seems a little fishy, if you ask me, but I guess it's no big deal since everything still seems to work in my FF3 install.

How do I mark this as solved?  =P

---

