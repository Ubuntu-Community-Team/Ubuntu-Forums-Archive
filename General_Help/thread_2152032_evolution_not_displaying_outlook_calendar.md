---
title: "evolution not displaying outlook calendar"
date: 2013-06-06
forum: General Help
---

### Post by gleedadswell on 2013-06-06
First of all I'm embarrassed to admit that my workplace uses an Outlook 2003 server...

I'm running Evolution 3.2.3 under Ubuntu 12.04.  I've installed the packages 

evolution
evolution-exchange

and have successfully got it to link to our Outlook server.  So I can read and send e-mail and the global address book works.  But when I go to the calendar it displays no events.  It gives the error:

Error loading calendar
No backend factory for 'exchange' of 'VEVENT'

Looking around elsewhere on the web I don't see much about this.  There is a post from someone using BSD a few years ago reporting the same thing:

[http://forums.freebsd.org/showthread.php?t=15515](http://forums.freebsd.org/showthread.php?t=15515)

They apparently found a fix for ubuntu involving adding a line to [COLOR=#000000][FONT=monospace]/etc/ld.conf.d/samba.conf[/FONT][/COLOR] but that file doesn't seem to exist under 12.04, so no luck there.

Another post I found elsewhere talked about the e-calendar-factory.  I've found mine; it is in

/usr/lib/evolution/e-calendar-factory

Could there be a configuration file that is supposed to point evolution at this file and somehow is failing?

Any suggestions would be much appreciated.

---

