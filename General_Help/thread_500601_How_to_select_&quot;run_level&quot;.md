---
title: "How to select &quot;run level&quot;?"
date: 2007-07-14
forum: General Help
---

### Post by Nergar on 2007-07-14
I found this text in a book i'm reading

[I]When Linux starts up, it enters into what is referred to as a run level or system state. Typically, a system set to start at run level 5 boots to a graphical login prompt. A system set to run level 3 boots to a text prompt. The run level is set by the initdefault line in the /etc/inittab file. Change the number on the initdefault line as you please between 3 and 5. 
Don’t use any other number unless you know what you are doing. Never use 0 or 6, since those numbers are used to shutdown and reboot the system, respectively.[/I]

but theres no /etc/inittab file, so where or what do i need to change so ubuntu boots to a text login?

---

### Post by apoth on 2007-07-14
It looks like the old init system has been replaced by one called upstart, which has its configuration in /etc/event.d

I don't know how the new system works but that should give you something more to google.

---

### Post by Nergar on 2007-07-14
there seems to be a lack of information on upstart. Thnx anyway

---

### Post by mlissner on 2007-09-11
If it isn't already too late, try: [this]("http://ubuntuforums.org/showthread.php?t=466108&highlight=run+level")

---

### Post by ArdentLonging on 2007-09-12
When I wanted to change run level, I just edited /etc/event.d/rc-default.  If you want run level to be 3, rewrite the last telinit x to telinit 3 and reboot.  Then you can start as run level 3.

If you want to change the behavior of the run level, please apt-get "sysv-rc-conf" which sets the behavior of each run level.  If you want run level 3 without gdm and X, just sysv-rc-conf as root and uncheck gdm and X.

---

