---
title: "gnome-cups-manager does not start"
date: 2006-10-11
forum: General Help
---

### Post by Flavian on 2006-10-11
Hi guys!
It is really weird, I got a little problem with gnome-cups-manager, it won't start. When I start it it loads and in the taskbar it says: "Starting gnome-cups-manager" and then nothing... it just disappears and that's it :(

I have to kill it to start it over again.
And when I want to print something an error message comes after a LONG period of time "The CUPS server could not be contacted" ... :(

[edit]
If I start it over the console I get the following Error Message:
> 
florian@octavius:~$ sudo gnome-cups-manager

** (gnome-printer-view:6864): WARNING **: IPP request failed with status 1280

** (gnome-printer-view:6864): WARNING **: IPP request failed with status 1280
- using device default
- using device default

And again an erro notification:
"The CUPS server could not be contacted"

---

### Post by gosh on 2006-10-11
Have you tried managing cups through your browser?
> [http://localhost:631](http://localhost:631)

---

### Post by Flavian on 2006-10-11
Does not work either :(
It just does not load the page...

---

### Post by Flavian on 2006-10-11
Maybe someone can help me with a little bit more information.
The error log puts out the following for my last print request!

> 
I [11/Oct/2006:22:12:57 +0200] Listening to :::631 (IPv6)
I [11/Oct/2006:22:12:57 +0200] Listening to 0.0.0.0:631 (IPv4)
E [11/Oct/2006:22:12:57 +0200] Unable to include config file "/etc/cups/cupsd-browsing.conf" - No such file or directory
W [11/Oct/2006:22:12:57 +0200] "AuthClass User" is deprecated; consider using "Require valid-user" on line 21.
W [11/Oct/2006:22:12:57 +0200] "AuthClass System" is deprecated; consider using "Require @SYSTEM" on line 26.
I [11/Oct/2006:22:12:57 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
W [11/Oct/2006:22:12:57 +0200] Repairing ownership of "/var/run/cups"
E [11/Oct/2006:22:12:57 +0200] Creating missing directory "/var/run/cups/certs"
W [11/Oct/2006:22:12:57 +0200] Repairing ownership of "/var/run/cups/certs"
W [11/Oct/2006:22:12:57 +0200] Repairing access permissions of "/var/run/cups/certs"
I [11/Oct/2006:22:12:57 +0200] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [11/Oct/2006:22:12:57 +0200] Configured for up to 100 clients.
I [11/Oct/2006:22:12:57 +0200] Allowing up to 100 client connections per host.
I [11/Oct/2006:22:12:57 +0200] Creating CUPS default administrative policy:
I [11/Oct/2006:22:12:57 +0200] <Policy default>
I [11/Oct/2006:22:12:57 +0200] <Limit Send-Document Send-URI Cancel-Job Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Authenticate-Job>
I [11/Oct/2006:22:12:57 +0200] Order Deny,Allow
I [11/Oct/2006:22:12:57 +0200] Require user @OWNER @SYSTEM
I [11/Oct/2006:22:12:57 +0200] </Limit>
I [11/Oct/2006:22:12:57 +0200] <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
I [11/Oct/2006:22:12:57 +0200] Order Deny,Allow
I [11/Oct/2006:22:12:57 +0200] AuthType Basic
I [11/Oct/2006:22:12:57 +0200] Require user @SYSTEM
I [11/Oct/2006:22:12:57 +0200] </Limit>
I [11/Oct/2006:22:12:57 +0200] <Limit All>
I [11/Oct/2006:22:12:57 +0200] Order Deny,Allow
I [11/Oct/2006:22:12:57 +0200] </Limit>
I [11/Oct/2006:22:12:57 +0200] </Policy>
I [11/Oct/2006:22:12:57 +0200] Full reload is required.
I [11/Oct/2006:22:12:57 +0200] Loaded MIME database from '/etc/cups': 34 types, 39 filters...
I [11/Oct/2006:22:12:58 +0200] Loading job cache file "/var/cache/cups/job.cache"...
I [11/Oct/2006:22:12:58 +0200] Full reload complete.
I [11/Oct/2006:22:12:58 +0200] Listening to :::631 on fd 0...
I [11/Oct/2006:22:12:58 +0200] Listening to 0.0.0.0:631 on fd 2...



I think it's also worth to mention that printing already worked before!! AND that it just does not work anymore, just out of the blue...

---

### Post by gosh on 2006-10-12
To enable cups browsing follow this wiki: [https://help.ubuntu.com/community/HOWTO-enable-cups-browsing](https://help.ubuntu.com/community/HOWTO-enable-cups-browsing)

---

### Post by Flavian on 2006-10-12
Seems like when I post something that it always happens 2 minutes after posting that I figure it out... :D
Anyways it works now :)
What I did was completely removing all the packages of cups and the related drivers plus gnome-cups-manager... reinstalled them and now it works! I can print *yeah*! Thanks for any help though!

---

### Post by maximilian35 on 2006-11-24
I also have a problem with 'cups-server'. I remove all the components related with cups and reinstall them. Now my printer Z 602 is working. Thanks for your post. Helps very much:)

---

