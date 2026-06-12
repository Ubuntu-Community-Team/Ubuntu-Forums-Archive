---
title: "[SOLVED] Help w/ choice &amp;amp; install of lightweight window manager for headless remote a"
date: 2007-02-25
forum: General Help
---

### Post by flamacue on 2007-02-25
[SIZE="2"]Goal:[/SIZE]

To setup my **headless Ubuntu server** to **run a few apps** (namely Azureus & Mozilla Thunderbird) **automatically on boot**, and have those apps accessible remotely (via VNC).  I am trying to minimize system resources used in the process.


[SIZE="2"]Current situation:[/SIZE]

I am running **Ubuntu *Server* 6.10** (so no local GUI!), on an AMD64 system.  I have **successfully installed [FONT="Courier New"]vnc4server[/FONT]**.  I can ssh into the server as a normal user, and execute [FONT="Courier New"]vncserver[/FONT].  Having done that, I can access display #1 remotely using VNC.  At present it is using [_[COLOR="Blue"]twm[/COLOR]_]("http://en.wikipedia.org/wiki/Twm") as its window manager, and it comes up with one xterm.  (I notice that this comes from the last two lines of [FONT="Courier New"]~/.vnc/xstartup[/FONT].)


[SIZE="2"]What I need:[/SIZE]

[LIST]Input on choice of a **lightweight window manager**.  (I don't want to run a full desktop environment, i.e. no Gnome/KDE.)  I just want to be able to resize/minimize/maximize windows, switch between tasks (so a taskbar would be handy), and launch apps from it.[/LIST]
[LIST]Help setting up said window manager to run on display #1 (instead of twm), such that it is accessible remotely via VNC.[/LIST]
[LIST]Help **automating the startup** (at boot time) of the VNC server with said window manager, and apps of my choice.[/LIST]


[SIZE="2"]Additional details (or "Motivation and 'Story Time'"):[/SIZE]

I had a machine set up as a raid box running gentoo.  It had two software RAID-1 arrays which I setup using [[COLOR="Blue"]_evms_[/COLOR]]("http://en.wikipedia.org/wiki/Enterprise_Volume_Management_System"), and samba shares for access from my Windows boxen.  Eventually...I broke the OS.  (Updated a bunch of stuff at once, copied new config files over top of old ones blindly.  Recovery plan failed.)  Fortunately, booting with the [_[COLOR="Blue"]System Rescue CD[/COLOR]_]("http://sysresccd.org") allowed me to see that all my data (and evms metadata) was still intact.  Gentoo had been high maintenance, so I decided to try Ubuntu.  (And I am pleased with that decision!)

I also decided to upgrade the hardware before doing so, as I wanted Wake On LAN, and the ability to add SATA devices later, so I bought a Gigabyte GA-K8NE motherboard, AMD Sempron 64 2800+, and 1 GB DDR-400 RAM.  (Upgraded from an old Athlon board with a Duron ~900MHz - 1GHz CPU, & single data rate SDRAM.)  The (PATA) disks in the RAID arrays remain connected to a PCI controller card.  I'm pleased with my new setup so far.

So with my new hardware in place, I installed Ubuntu Server, set it to automount my RAID arrays at boot, and setup some samba shares.  (Getting Wake On LAN to work took some time to figure out, due to some bad assumptions and an old driver (forcedeth).  I intend to post a HOW-TO later.)

I bought the hardware I did because it was featureful at a fair price, and had relatively modest power requirements.  However, the irony of the situation is that it is now significantly more powerful than my regular desktop machine...which runs Windows 2000 Pro...and which stays on 24x7 for a couple reasons:
[LIST]Downloading emails from a pop server with Thunderbird.  Select messages are forwarded based on filter rules, for near-realtime alerts sent to my SMS phone, and[/LIST]
[LIST]Seeding torrents with Azureus.[/LIST]

My windows box has become rather sluggish and bloated, and it uses more power (electricity) than my raid box (ubuntu server)....such is my primary motivation for migrating these apps, so I can turn off my Windows machine.

---

### Post by yabbadabbadont on 2007-02-25
Fluxbox meets your listed requirements.

---

### Post by flamacue on 2007-02-26
New problem:  Firefox will not run from within fluxbox, openbox, or icewm.  (It still works fine on twm, though.)

Per your suggestion, and some additional research, I installed fluxbox, openbox, and icewm, to try them out.  I added one at a time to [FONT="Courier New"]~/.vnc/xstartup[/FONT] (commenting out all others), and restarted the vncserver with
[FONT="Courier New"][FONT="Fixedsys"]vncserver -kill :1; vncserver -localhost[/FONT][/FONT]
(using -localhost b/c I'm ssh tunnelling).

I cannot run Firefox from any of them.  From fluxbox, openbox, or icewm, whether I type [FONT="Fixedsys"]firefox &[/FONT] in the xterm window, or launch it by right-click and choosing it from the window manager's menu, I get the following error:

[FONT="Courier New"]The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 1936 error_code 1 request_code 146 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

[1]+  Exit 1                  firefox
flamacue@raid:~$[/FONT]

and it crashes immediately.


Firefox was to be a test app for me as I try out window managers; I would like to be able to run it occasionally from the virtual desktop.  How can I fix this?

Note:  I had installed [FONT="Courier New"]firefox[/FONT] v2.0.0.1+0d using aptitude, prior to installing the new window managers.

Thanks in advance to anyone who can help.

---

### Post by flamacue on 2007-08-17
It's been a while since I posted these.  I think I was running Edgy server at the time.  Running Feisty server (converted to Xubuntu) at the moment, and I'm not having the same issues, or taking quite the same approach.

i.e.  This thread is now obsolete (which is why I marked it "solved").  :)

---

