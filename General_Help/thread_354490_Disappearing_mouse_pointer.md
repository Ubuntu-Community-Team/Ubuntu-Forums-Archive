---
title: "Disappearing mouse pointer"
date: 2007-02-06
forum: General Help
---

### Post by juicemansam on 2007-02-06
OK, up until a few updates ago, possibly within the last two weeks, I've noticed my mouse pointer disappearing. This mostly happens when using Firefox 1.5.0.9 and Thunderbird 1.5.0.9. The actual symptom is the mouse pointer disappearing inside the application window(s), and re-appearing when the pointer is in the task bar/panels, or viceversa, disappearing in the panels and appearing in the application. It also randomly appears and disappears within the browser window, depending on the object being hovered over, which is also random. Does anybody know what's going on, or has had this same problem? I don't remember this happening with xubuntu, which I've been using for more than 6 months, up until 2-3 weeks after updating/upgrading to edubuntu (both dapper versions).

My OS is the standard Dapper-based Edubuntu AMD64 version, with Dapper-based Xubuntu AMD64 version left-over files. The hardware is an PentiumD 805, 1GB DDR2 533, ECS C19A (with latest bios), Samsung SyncMaster 941bw, and an Optorite Laser mouse.

My suspicions lie on X, Gnome, or Nvidia's 8774 driver (driver's between that version and 9746, seem broken for my needs. The only suspicious log entry that I can find is the SetGrabKeysState - enabled/disabled messages, but they might be unrelated. The reasons that I suspect X or Gnome is because I remember reading about root window layers, which if my little understanding of X and Gnome is in the least bit correct, the mouse pointer is being drawn on a layers that's failing?

---

### Post by juicemansam on 2007-02-11
OK, yesterday I started using the XFCE session (again) rather than the GNOME session, and I'm not getting any of the symptoms of the disappearing pointer.

---

### Post by Talon2 on 2007-02-13
I see the same issue on my main box here.  I have an ATI Radeon 9600 card using the x.org driver so I can't blame it on the nVidia driver.  I'm running Edubuntu 6.10.

This is terribly annoying.  I've found other similar reports but no solution.

I may load Xbuntu to see if maybe this is related to Gnome.

---

