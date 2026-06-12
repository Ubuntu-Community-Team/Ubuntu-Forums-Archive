---
title: "Upstart Documentation?"
date: 2006-11-21
forum: General Help
---

### Post by dibl on 2006-11-21
Kind Readers,

Anyone know where I can find any documentation on upstart?  For example... when one issues a stop <job> command, what signal is sent to the process by upstart?  One might expect to find that sort of detail in the man page for stop.  Where can I find documentation on the language for event scripts?  One might expect to find a man page for event.d.  If no such man pages exist, I'm willing to contribute to them, but I need access to the information to do so?  Yes, yes, I know... RTS (read the source)... is that all there is?

-- David

---

### Post by keybuk on 2006-11-23
> **dibl said:**
> Kind Readers,

Anyone know where I can find any documentation on upstart?  For example... when one issues a stop <job> command, what signal is sent to the process by upstart?  One might expect to find that sort of detail in the man page for stop.  Where can I find documentation on the language for event scripts?  One might expect to find a man page for event.d.  If no such man pages exist, I'm willing to contribute to them, but I need access to the information to do so?  Yes, yes, I know... RTS (read the source)... is that all there is?

-- David

Documentation is kinda deliberately missing from edgy, because we knew that a lot of it would change for feisty and we didn't want people relying on it not changing.

To answer your questions, the TERM signal is sent to a process followed by the KILL signal if the process doesn't die within a certain amount of time.

The language for the event scripts is documented at [http://upstart.ubuntu.com/doc/getting-started.html](http://upstart.ubuntu.com/doc/getting-started.html)  I can forewarn you that "start script" and "stop script" are being renamed, and that "on EVENT" will mean something else entirely.

For feisty, we'll be shipping far richer documentation.  If you'd like to help out with that, join us on Freenode #upstart

---

### Post by jthompson on 2006-12-08
Well lets say I need to add an init script for something that doesn't necessarily have an ubuntu package or debian package.  Or maybe I want to take an init script written for debain and make it work on Edgy...

Can I poor through /etc/init.d/skeleton?

Does that still work?

Can I use update.rc-d foobar defaults still?

Do Bum, and things like that still show you what is slated to start on bootup, etc?

---

