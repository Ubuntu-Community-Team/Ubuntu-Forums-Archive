---
title: "Inquiry about Ubuntu Server"
date: 2006-12-30
forum: General Help
---

### Post by shoregeek on 2006-12-30
Hi All,
I am not new to the IT or Technology world, however, Linux is not something I have worked with on a professional level.   Mostly tinkering with the included *nix in OSX Tiger. 

I have been reading a lot about Ubuntu and look forward to playing with the desktop version, especially as an alternative to Windows.  However, I have some questions about the server edition.

I am looking to setup a server for my small business - we are in need of LDAP, WebDAV, File Server (NAS?), and some web page serving (limited access).

The LDAP and WebDAV are to replace our .Mac account - which helps us share our contacts and calendars, as .Mac is unreliable.

I would also like the ability to run a limited access project management PHP package for contractors use (posting jobs, bidding, tracking, etc.).

Is this possible with Ubuntu Server?  Also, I seem to be happier with some sort of GUI setup - can I setup a server with GUI vs. all command line?  I will learn my command lines as necessary, but there is something to be said about a decent GUI.  :D 

Sorry to be so long winded, but this is something I have been looking at doing for a long time - and something has to be done soon.  I want to be as thorough as I can before jumping in.

Thanks!

-Eric

---

### Post by Arisna on 2006-12-30
I know that a GNU/Linux machine would be very suitable for running a file server (through NFS or SMB, usually), a web server (Apache), and PHP services.  I'm not sure about LDAP or WebDAV--I didn't see anything suitable with a quick browse through the official Ubuntu software repositories.  I could be missing something, or software for these last two things might be available through other sources.

---

### Post by shoregeek on 2006-12-30
After some reading it would appear "LAMP" is what I need to install.  Still trying to figure that all out. :)

---

### Post by koenn on 2006-12-30
next to LAMP you may allso need Samba (Windows style File server).
For LDAP you could look into OpenLDAP - you may find it in the ubuntu repositories eg
[http://packages.ubuntu.com/edgy/net/slapd](http://packages.ubuntu.com/edgy/net/slapd)

---

