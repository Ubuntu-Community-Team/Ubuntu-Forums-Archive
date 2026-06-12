---
title: "proftpd problem"
date: 2006-10-21
forum: General Help
---

### Post by mitjab on 2006-10-21
i upgrade proftpd and now i have problem with ipv6, no one can connect to ftp. Why i can not use ipv4?

this is proftpd.log

Oct 21 12:51:20 server proftpd[8721] mitjab.homelinux.net: error setting IPV6_V6ONLY: Protocol not available
Oct 21 12:51:20 server proftpd[8721] mitjab.homelinux.net: ProFTPD 1.3.0 (stable) (built Sun Oct 15 11:31:30 UTC 2006) standalone mode STARTUP
Oct 21 12:51:53 server proftpd[8721] mitjab.homelinux.net: ProFTPD killed (signal 15)
Oct 21 12:51:53 server proftpd[8721] mitjab.homelinux.net: ProFTPD 1.3.0 standalone mode SHUTDOWN
Oct 21 12:51:55 server proftpd[8747] mitjab.homelinux.net: error setting IPV6_V6ONLY: Protocol not available
Oct 21 12:51:55 server proftpd[8747] mitjab.homelinux.net: ProFTPD 1.3.0 (stable) (built Sun Oct 15 11:31:30 UTC 2006) standalone mode STARTUP
Oct 21 12:51:57 server proftpd[8749] mitjab.homelinux.net (BSN-95-232-143.dial-up.dsl.siol.net[::ffff:193.95.232.143]): error setting IPV6_V6ONLY: Protocol not available
Oct 21 12:51:57 server proftpd[8749] mitjab.homelinux.net (BSN-95-232-143.dial-up.dsl.siol.net[::ffff:193.95.232.143]): FTP session opened.
Oct 21 12:51:59 server proftpd[8749] mitjab.homelinux.net (BSN-95-232-143.dial-up.dsl.siol.net[::ffff:193.95.232.143]): USER mitjab: Login successful.
Oct 21 12:52:00 server proftpd[8749] mitjab.homelinux.net (BSN-95-232-143.dial-up.dsl.siol.net[::ffff:193.95.232.143]): error setting IPV6_V6ONLY: Protocol not available
Oct 21 12:52:00 server proftpd[8749] mitjab.homelinux.net (BSN-95-232-143.dial-up.dsl.siol.net[::ffff:193.95.232.143]): error setting IPV6_V6ONLY: Protocol not available

what to do?

thx

---

### Post by taurus on 2006-10-21
Maybe you want to comment out by placing a # in front of the lines with IPV6 in /etc/hosts!!!  Otherwise, install gproftpd and use it to configure your proftpd...

---

### Post by mitjab on 2006-10-21
i try to comment this in hosts file but it is the same.
I can not use gproftpd becouse i do not have KDE or GNOME.

---

### Post by taurus on 2006-10-21
After modifying your /etc/hosts, did you reboot!

Are you running the server version right now?

---

### Post by mitjab on 2006-10-21
yes i reboot the system and yes i am running the server version of ubuntu.

---

### Post by mitjab on 2006-10-22
the problem must be somewhere else but do not know where?

---

### Post by ash211 on 2007-01-08
I'm having the same problem with a current edgy system.  Did you ever get proftpd working, mitjab?

---

### Post by rotorboy on 2007-01-17
Same problem as mitjab.
error setting IPV6_ONLY: Protocol not available

I also commented out the IPv6 lines in /etc/hosts... no joy.](*,) 

Could this be router related?

---

### Post by rootchick on 2007-01-19
I'm having this same problem...it seems that edgy is using proftpd 1.3.0, compiled with ipv6 enabled, and there's no way to turn it off as far as I can tell.  However, 1.3.1 was released on 12/12/06 with a configuration option to disable it.  Here's what I found about it:

[http://www.proftpd.org/docs/RELEASE_NOTES-1.3.1rc1](http://www.proftpd.org/docs/RELEASE_NOTES-1.3.1rc1)

Looks like the ubuntu package needs to be updated.  Or maybe you can grab the source package and compile it without ipv6 enabled?  Maybe I'll try it.

---

### Post by rootchick on 2007-01-19
Well, it's not as bad as I thought.  I added this line to /etc/hosts, just under my original localhost (127.0.0.1) line:

::1             localhost.localdomain   localhost  

That sets localhost for ipv6.  It seems to work, at least when I started proftpd it didn't fail.

---

### Post by ash211 on 2007-01-19
Ubuntu generally doesn't add new packages until they can be synced with Debian, since that saves both parties time and effort.  Debian doesn't have 1.3.1 in the repositories yet, see [http://packages.debian.org/stable/net/proftpd](http://packages.debian.org/stable/net/proftpd)

We'll have to wait for Debian to package the latest proftpd until Ubuntu can sync it.  To speed up the process, see what it takes to file a package request in Debian.  I'd be interested to know how it's done.

---

