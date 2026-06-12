---
title: "Printing problems - no go"
date: 2006-11-29
forum: General Help
---

### Post by VSpike on 2006-11-29
I'm having endless trouble with printing.  The bottom line is, I can't get anything to come out of my printers.

I know they are connected OK via USB, because I can cat stuff to /dev/usblp* and the data lights flash on the printers.

When I go to KDE printer setup and try to add a printer via CUPS, the backend selection only offers me "SMB shared" or "Other" - other options are greyed out.

I've tried installing TurboPrint (my Canon i865 is not fully supported by CUPS, but should print something), but that does not seem to be able to print either - it keeps telling the printer is  turned off.

I've tried switching to LPRng but that doesn't work either - it doesn't list the USB ports in the detected local devices, and refuses to send to them.

My other printer is an HP Laserjet 2550 by the way.  When I try to install that (by switching to LPRng, and manually entering /dev/usblp1 as the port) and then select "Postscript Printer", I get a message "Unable to load the requested driver".


I've tried removing and reinstalling CUPS and all related printing packages that I could see, but no joy.

Here is a section from my CUPS error_log after a restart of the daemon.  Does it give any clues?

I've tried googling for some of the messages, but I never seem to hit anything useful.

Please help!

I [29/Nov/2006:14:34:19 +0000] Scheduler shutting down normally.
E [29/Nov/2006:14:34:19 +0000] Unable to save remote.cache - Permission denied
E [29/Nov/2006:14:34:19 +0000] Unable to create job cache file "/var/cache/cups/job.cache" - Permission denied
I [29/Nov/2006:14:34:20 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
I [29/Nov/2006:14:34:20 +0000] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [29/Nov/2006:14:34:20 +0000] Configured for up to 100 clients.
I [29/Nov/2006:14:34:20 +0000] Allowing up to 100 client connections per host.
I [29/Nov/2006:14:34:20 +0000] Using policy "default" as the default!
I [29/Nov/2006:14:34:20 +0000] Full reload is required.
I [29/Nov/2006:14:34:20 +0000] Loaded MIME database from '/etc/cups': 1 types, 0 filters...
W [29/Nov/2006:14:34:20 +0000] add_banner: Banner "confidential" ("/usr/share/cups/banners/confidential") is of an unknown file type - s
kipping!
W [29/Nov/2006:14:34:20 +0000] add_banner: Banner "classified" ("/usr/share/cups/banners/classified") is of an unknown file type - skipp
ing!
W [29/Nov/2006:14:34:20 +0000] add_banner: Banner "standard" ("/usr/share/cups/banners/standard") is of an unknown file type - skipping!
W [29/Nov/2006:14:34:20 +0000] add_banner: Banner "secret" ("/usr/share/cups/banners/secret") is of an unknown file type - skipping!
W [29/Nov/2006:14:34:20 +0000] add_banner: Banner "unclassified" ("/usr/share/cups/banners/unclassified") is of an unknown file type - s
kipping!
W [29/Nov/2006:14:34:20 +0000] add_banner: Banner "topsecret" ("/usr/share/cups/banners/topsecret") is of an unknown file type - skippin
g!
I [29/Nov/2006:14:34:20 +0000] Loading NextJobId from job cache file "/var/cache/cups/job.cache"...
I [29/Nov/2006:14:34:20 +0000] Full reload complete.
I [29/Nov/2006:14:34:20 +0000] Listening to 127.0.0.1:631 on fd 2...
I [29/Nov/2006:14:34:20 +0000] Listening to /var/run/cups/cups.sock on fd 3...
I [29/Nov/2006:14:35:48 +0000] Started "/usr/lib/cups/daemon/cups-deviced" (pid=23202)
E [29/Nov/2006:14:36:11 +0000] CUPS-Add-Modify-Printer: Unauthorized
I [29/Nov/2006:14:36:11 +0000] Saving printers.conf...
I [29/Nov/2006:14:36:11 +0000] Printer "tp0" modified by "root".
I [29/Nov/2006:14:36:11 +0000] Saving printers.conf...
I [29/Nov/2006:14:36:11 +0000] Printer "tp0" modified by "root".
I [29/Nov/2006:14:38:15 +0000] Started "/usr/lib/cups/daemon/cups-deviced" (pid=27103)
I [29/Nov/2006:14:38:18 +0000] Started "/usr/lib/cups/daemon/cups-deviced" (pid=27147)
E [29/Nov/2006:14:39:54 +0000] cupsdAuthorize: Local authentication certificate not found!
I [29/Nov/2006:14:39:54 +0000] Installing config file "/etc/cups/cupsd.conf"...
E [29/Nov/2006:14:39:54 +0000] Unable to save remote.cache - Permission denied
I [29/Nov/2006:14:39:54 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
I [29/Nov/2006:14:39:54 +0000] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [29/Nov/2006:14:39:54 +0000] Configured for up to 100 clients.
I [29/Nov/2006:14:39:54 +0000] Allowing up to 100 client connections per host.
I [29/Nov/2006:14:39:54 +0000] Using policy "default" as the default!
I [29/Nov/2006:14:39:54 +0000] Partial reload complete.
E [29/Nov/2006:14:39:54 +0000] Unable to bind socket for address 127.0.0.1:631 - Permission denied.
I [29/Nov/2006:14:39:54 +0000] Listening to /var/run/cups/cups.sock on fd 2...

---

### Post by needhelpplease on 2007-11-28
I'm having this same problem.  This is what my backend selection looks like:

[IMG]http://img2.freeimagehosting.net/uploads/b73699d81f.png[/IMG]

I tried the foomatic reload drivers thing and it didn't help.  The printer is detected and works fine under Windows.  This came about after doing an upgrade from 7.04 to 7.10.

Any ideas?

---------
[IRS tax help](http://irstaxlawyers.us/)

---

### Post by jbeiter on 2007-12-01
same here, I switched from redhat (printers worked fine with cups) to Ubuntu 7.10 and printing doesn't work at all. 

Annoyingly, it detected that I have a printer on the par port and even detected what make and model it is. Print jobs and tests do nothing.

Man I hate cups. It's a perpetually brittle app.

---

### Post by jbeiter on 2007-12-01
deleted - off topic

---

