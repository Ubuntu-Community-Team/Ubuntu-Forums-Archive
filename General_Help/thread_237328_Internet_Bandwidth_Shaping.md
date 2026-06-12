---
title: "Internet Bandwidth Shaping"
date: 2006-08-16
forum: General Help
---

### Post by PacShady on 2006-08-16
Hey all

Here's another program I need to find an alternative for converting from Windows to Linux - NetLimiter.

NetLimiter is an all-purpose bandwidth shaping utility. Not only can it shape a computer's entire network connection, but it's ALSO good for limiting specific programs traffic, blocking traffic altogther, and one can also set up time conditions on limits imposed on programs, for instance, one program can be shaped between the hours of 8am-8pm at 8KB/s, and outside of these times shaping is removed. This kind of setup is really awesome for instance setting up a download program to download at full speed during night, but during the day traffic for that specific program is slowed to allow other programs such as web browsers etc. to use the free bandwidth.

Unfortunately, my searching so far has only brought up QoS shapers, which work on a priority system which I've found to be quite ineffective for what I need, rather than a fixed limiting system like NetLimiter. Also, I've not found one program at all so far that has a graphical frontend (well I am still used to Windows, and most text-based terminal programs are too complicated for me right now with limited understanding), and I've not found one program either that has time conditions that are able to be set, so one must make changes manually whenever shaping is required (which defeats the purpose of what I need it for). Finally, many of the shapers I've found are for large networks, and shape entire connections to workstations rather than specific programs.

So, is there any solution to this on Linux? I think a great number of home users would benefit from such a program as this, but so far I've had no luck in finding one.

'Shady

---

### Post by PacShady on 2006-08-25
*bump*

---

### Post by cypresstwist on 2007-10-02
Use "trickle".

---

### Post by tab80 on 2008-01-08
Maybe you should try mastershaper
[http://www.mastershaper.org/index.php/Main_Page](http://www.mastershaper.org/index.php/Main_Page)

or firestarter (I'm not sure of the traffic shaping feature)
[http://www.fs-security.com/](http://www.fs-security.com/)

---

### Post by njparton on 2008-01-08
Squid?

---

