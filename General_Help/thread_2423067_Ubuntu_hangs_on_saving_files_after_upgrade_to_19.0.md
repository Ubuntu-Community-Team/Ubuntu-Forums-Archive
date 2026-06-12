---
title: "Ubuntu hangs on saving files after upgrade to 19.04"
date: 2019-07-17
forum: General Help
---

### Post by punknroll on 2019-07-17
Hi,

after upgrading to 19.04 my system ist getting slow and slower the longer the machine is running. Especially saving files takes longer and longer and the whole system freezes when I store a file. I saw that memory consumption of gnome shell increases. How can I debug what's wrong here? I created a new account and everything works fast there.

Any hints?

Thanks in advance.

---

### Post by dino99 on 2019-07-17
Are you using a swap file or partition ? is it activated and working ? what errors is logged ? (journalctl -b)
Have you cleaned your system after dist-upgrade ? (use gtkorphan and bleachbit as root (carefully select scripts) )

---

### Post by punknroll on 2019-07-18
Thanks for the quick reply. I cleaned the system using gtkorphan and bleachbit as root. But no luck.

I am using a swap partition:

swapon -s
filename				Typ		size	used	priority
/dev/dm-1                              	partition	16723964	0	-2

When I delete a file from the desktop it takes a 12 seconds while the desktop freezes then the desktop refreshes.

journalctl -b only shows:
Jul 18 15:43:37 punknroll-desktop dbus-daemon[4503]: [session uid=1000 pid=4503] Activating service name='org.gnome.Nautilus' requested by ':1.25' (uid=1000 pid=4860 comm
Jul 18 15:43:37 punknroll-desktop dbus-daemon[4503]: [session uid=1000 pid=4503] Successfully activated service 'org.gnome.Nautilus'
Jul 18 15:43:37 punknroll-desktop org.gnome.Nautilus[4503]: Initializing nautilus-image-converter extension

It doesn't look like an error to me.

Any hints?

---

### Post by punknroll on 2019-07-22
I switched to gnome desktop environent and used gnome tweak tool to play around with the settings. I also deleted a lot of files on my desktop. The freezing was gone. Now even if i switch back to "Ubuntu" as desktop environment the freezing is gone. 

So for me the problem is resolved now.

---

