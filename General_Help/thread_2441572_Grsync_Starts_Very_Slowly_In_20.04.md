---
title: "Grsync Starts Very Slowly In 20.04"
date: 2020-04-24
forum: General Help
---

### Post by linux4me on 2020-04-24
I just did a clean install of Ubuntu 20.04 on two machines, and in both cases, Grsync takes a *very* long time to start. I tried it with both a fresh grsync.ini file and my existing one, and it made no difference.

To give you an idea of how slow Grysnc's startup really is, here's the start time of LibreOffice Writer as shown by the time command:
```

time libreoffice --writer

real	0m2.771s
user	0m1.130s
sys	0m0.108s

```

and here's the start time of Grsync:
```

time grsync

real	0m37.736s
user	0m0.210s
sys	0m0.016s

```

So LibreOffice starts in only 2.771 seconds, and it takes Grsync 37.736 seconds to start!

When starting from the command line, Grsync does throw an error about the "canberra-gtk-module" not being installed, so I installed libcanberra-gtk-module, which prevents the error, but does nothing for the slow startup.

Has anyone had the same issue? Any suggestions on how to further troubleshoot this?

---

### Post by mcellius on 2020-04-24
I haven't used grsync in some time so I don't know when the slowness started, but I checked and had the same result as you: it takes over 30 seconds to open.  I installed it from Ubuntu Software, and it's not a Snap (which was blamed for a couple apps that started slowly), so I don't know what's going on.  However, it's pretty old and I don't think it's had further development in some time.

---

### Post by linux4me on 2020-04-26
Thanks for checking it out. I'm glad to hear it's not just me, at least.

I was running 18.04 prior to this, and used Grsync regularly without the slow startup, so I think this particular issue is new in 20.04; however, [ssh-askpass was broken]("https://bugs.launchpad.net/ubuntu/+source/grsync/+bug/1789012") then and remains so in 20.04.

I hope development isn't dead, though judging by what I see on Launchpad, it may be.

---

### Post by rbmorse on 2020-04-26
Grsync hasn't been updated for awhile.  In the meantime, a couple of new versions of GTK have been released. 

You might need to install:

```
appmenu-gtk2-module
```

or possibly that and 

```
libcanberra-gtk-module
```

as well.  Don't forget to reboot after installation.  If they don't help you can back them out again.

---

### Post by linux4me on 2020-04-29
I saw the error message about libcanberra-gtk-module when I started Grsync from Terminal, so I already had that installed, and it made no difference other than preventing the error.

I tried installing appmenu-gtk2-module as you suggested, rebooted, and that fixed the issue. Here's the start time of Grsync with appmenu-gtk2-module installed:
```

time grsync

real	0m8.669s
user	0m0.110s
sys	0m0.022s

```
Much better! Thanks @rbmorse.

---

