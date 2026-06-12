---
title: "Edgy slows down after some upgrades."
date: 2007-01-12
forum: General Help
---

### Post by wormite on 2007-01-12
Hi all, some time ago(probably 3, 4 days ago) There was an automatic upgrade on my Edgy, which included 30-40 items. And suddenly everything in Edgy starts very slowly. Everything is normal until I put in my name and password to log in. After that, Nautilus, gnome-desktop, beryl, firefox, terminal, all start with a long time overhead. Even opening a new web page in firefox tab is gonna take more time. I'm totally lost in this problem. Is there anyone who can tell me where to look at?

My machine:
Dell Latitude D620.

Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)

top - 13:24:14 up 31 min,  4 users,  load average: 0.20, 0.17, 0.16
Tasks: 121 total,   1 running, 120 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.3%us,  0.7%sy,  0.0%ni, 89.1%id,  0.0%wa,  0.0%hi,  1.0%si,  0.0%st
Mem:   1034224k total,   717268k used,   316956k free,    15500k buffers
Swap:  1124508k total,        0k used,  1124508k free,   416980k cached

.xsession-errors give these:
(gnome-panel:5262): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 24
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

Using beryl and NVIDIA-Linux-x86-1.0-9746-pkg1.run which is installed by myself(not the apt-get package provided by edgy)
The time line of what happened:
3 days ago, upgrading 30-40 items, after that, beryl broke so I reinstalled my nvidia driver. Everything worked fine then.
So I undocked my laptop and went home. The problem started. After switching to single screen(when it's docked, it's using dual view) and log in, every program is taking a long time to start.
After trying to solve this for 3 hours and failed, I went back to office and docked laptop again, nothing happened, but after probably 7 or 8 reboots, things became normal again. But "fail to start HAL" error came out every time I log in.
So I searched and found these 2 commands and ran it.
sudo update-rc.d -f dbus remove

sudo update-rc.d dbus defaults 12 
Which obviously changed the priority of dbus process in booting up, and HAL error stopped.

Then I undocked again and went home, everything starts slow again.

Now after rebooting for countless times here in my office with it docked, I'm really frustrated. Thanks to anyone who has read till here, help is really needed here.

---

### Post by wormite on 2007-01-12
PS. By starting slow I mean it takes 10 more seconds for EVERY program to start, even for viewing a new page in firefox.

---

### Post by Envel on 2007-01-16
I have the same problem. It takes a long time to start nautilus, browsing is very slow. Even Rhythmbox is slow!

---

### Post by stocks29 on 2007-01-23
I am experiencing the same problems too.  I especially notice it with nautilus.  When I try to start it it takes about 15 seconds for the window to show up.  If there are already nautilus windows open, they become unresponsive for about 15 seconds.  

I thought it was hdparm and the fact that my drives were spinning down after so many minutes, but I disabled hdparm and still experience the problem.

I am using the 64 bit version of edgy?  Is anyone else?

About everything else starting slow, it may take an extra few seconds for other applications to start (although im not sure), but once they are started they seem to work fine including opening a new firefox tab and or window.

---

### Post by stocks29 on 2007-01-27
Ok, I seem to have resolved my problem.  It apparently was unrelated to any updates.  I went into Services within the Administration menu and disabled autofs.  This caused nautilus open times to decrease from 40+ seconds to about 1 second.  Problem solved....for me anyways......I hope this helps someone else.

---

### Post by dumbbeatnix on 2007-02-02
autofs ??? I don't seem to have that service.  Is this something I should be worried about.

Also having same problems as those posted here.

Cheers
dumbbeatnix:confused:

---

