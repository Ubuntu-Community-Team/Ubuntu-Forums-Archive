---
title: "CUPS server can not be contacted"
date: 2007-04-15
forum: General Help
---

### Post by braddcadd on 2007-04-15
I have read a lot of cups thread and my problem seems to fall through the cracks.  

System-->Administration-->Printing    give the following error  "Cups server can not be contacted"

lpq from terminal gives:
```

lpq: Unable to connect to server

```

cups doesn't start correctly from the terminal (notice there is no [ok] on the right):
```

sudo /etc/init.d/cupsys start
 * Starting Common Unix Printing System: cupsd 

```

here is my error log (i've recently purged so the log may be light):
```

cat /var/log/cups/error_log
E [15/Apr/2007:07:36:50 -0400] Unknown directive RunAsUser on line 8.
E [15/Apr/2007:07:36:50 -0400] Filter "foomatic-rip" for printer "LaserJet-4" not available: No such file or director

```

here is apt info on cups:
```
apt-cache show cupsys
Package: cupsys
Priority: optional
Section: net
Installed-Size: 9460
Maintainer: Debian CUPS Maintainers <pkg-cups-devel@lists.alioth.debian.org>
Architecture: i386
Version: 1.2.0-0ubuntu5
Replaces: cupsys-pstoraster
Depends: libc6 (>= 2.3.4-1), libcupsimage2 (>= 1.1.19final-1), libcupsys2 (>= 1.1.99.rc2), libgnutls12 (>= 1.2.5), libldap2 (>= 2.1.17-1), libpam0g (>= 0.76), libpaper1, libslp1, zlib1g (>= 1:1.2.1), adduser (>= 3.12), debconf (>= 1.2.9) | debconf-2.0, patch, poppler-utils | xpdf-utils, perl-modules, procps, gs-esp, lsb-base (>= 3)
Recommends: cupsys-client, smbclient (>= 3.0.9), foomatic-filters
Suggests: cupsys-bsd, cupsys-driver-gutenprint | cupsys-driver-gimpprint, foomatic-filters-ppds, xpdf-korean | xpdf-japanese | xpdf-chinese-traditional | xpdf-chinese-simplified, cups-pdf, hplip
Conflicts: cupsys-pstoraster (<< 2)
Filename: pool/main/c/cupsys/cupsys_1.2.0-0ubuntu5_i386.deb
Size: 2161748
MD5sum: 61cdc1e5b56dc6901faaf5d40a2d0680
Description: Common UNIX Printing System(tm) - server
 The Common UNIX Printing System (or CUPS(tm)) is a printing system and
 general replacement for lpd and the like.  It supports the Internet
 Printing Protocol (IPP), and has its own filtering driver model for
 handling various document types.
 .
 This package provides the CUPS scheduler/daemon and related files.
 .
 The terms "Common UNIX Printing System" and "CUPS" are trademarks of
 Easy Software Products (www.easysw.com), and refer to the original
 source packages from which these packages are made.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, kubuntu-desktop, edubuntu-desktop, xubuntu-desktop

```


here is my cupsd.conf file:
```

cat cupsd.conf
#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

RunAsUser No

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
# Listen localhost:631
# Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
# The 'Browsing' setting is configured in /etc/cups/cups.d/browse.conf
# so that changing it does not require to change this file.
# Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an adminstrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

# Include files in /etc/cups/conf.d
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf

```

I wish I could give more details on the problem but I have no idea what's going on with this one.  Any help would be appreciated.  Thanks.

---

### Post by Adramelech on 2007-04-15
Juat what i might try in your situation:

E [15/Apr/2007:07:36:50 -0400] Filter "foomatic-rip" for printer "LaserJet-4" not available: No such file or directory

Seems like you installed a printer and the CUPS is not able to find the driver? try unsintalling the driver and starting CUPS.

Or try to locate the file.

updatedb
locate foomatic-rip

---

### Post by braddcadd on 2007-04-15
I removed that printer from the printers.conf file.  Still can;t get cups to start correctly.  Should I do something else to ensure I've removed the driver for the LJ4?

---

### Post by braddcadd on 2007-04-15
here is some more information from the error log:
```

E [15/Apr/2007:13:54:29 -0400] Unknown directive RunAsUser on line 8.
E [15/Apr/2007:13:58:13 -0400] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [15/Apr/2007:13:58:23 -0400] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [15/Apr/2007:14:00:03 -0400] Unknown directive RunAsUser on line 8.
E [15/Apr/2007:14:00:17 -0400] Unknown directive RunAsUser on line 8.

```

---

### Post by pointone on 2007-04-15
Comment the RunAsUser line in your cupsd.conf file.

---

### Post by braddcadd on 2007-04-15
No dice there either.  I tried commenting it, changing it to yes, changing it to no,...

Maybe the erros in the log are not the root cause of my problem (cups won't start...)?

I'm trying to use the web interface to cups now but I don't have/know my username password for cups...

---

### Post by UltraMathMan on 2007-04-16
First open a terminal and do ```
sudo adduser cupsys shadow
``` then you will be able to log into the web interface with your username and password. Second uncomment both the Listen directives in cupsd.conf, keep RunAsUser commented (I think that command is outdated). Make sure you have foomatic-db, foomatic-db-engine, foomatic-db-gutenprint, foomatic-db-hpijs, foomatic-filters, foomatic-filters-ppd installed. Then try adding the printer again. If that doesn't work change "LogLevel warning" to "LogLevel debug" in cupsd.conf to get more info. Hope this helps :)

---

### Post by koenie53 on 2007-04-16
braddcadd I have the same problem in edgy and so far nobody replied with info on how to solve this problem so far. I tried everything but no luck
There is one thing I want too ask you.........how do you get the screenprints of the files you send. 
I can only take a screenshou but that does not look good......can you indicate how this is dine please!!!!!
Before I forget.....if you get this solved can you email me at [email]gertkoen@telkomsa.net[/email]

---

### Post by braddcadd on 2007-04-16
Thanks for the replies.  Still no change for me.  Although, I've abondoned the old LJ4 printer, so I don't need to install it.  I just need the cups server running again.  At this point I don;t theink the old LJ4 printer is causing the problem.

As before (I copy the terminal with a mouse and the edit->copy pulldown menu in the terminal).  Here is the debug level information.  Maybe it will help us solve the problem:
```

E [16/Apr/2007:17:26:04 -0400] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [16/Apr/2007:17:26:15 -0400] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [16/Apr/2007:17:26:32 -0400] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
I [16/Apr/2007:17:28:24 -0400] Listening to 127.0.0.1:631 (IPv4)
I [16/Apr/2007:17:28:24 -0400] Listening to /var/run/cups/cups.sock (Domain)
I [16/Apr/2007:17:28:24 -0400] Listening to :::631 (IPv6)
I [16/Apr/2007:17:28:24 -0400] Listening to 0.0.0.0:631 (IPv4)
I [16/Apr/2007:17:28:24 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [16/Apr/2007:17:28:24 -0400] Cleaning out old temporary files in "/var/spool/cups/tmp"...
D [16/Apr/2007:17:28:24 -0400] Removed temporary file "/var/spool/cups/tmp/4623e9e19d276"...
D [16/Apr/2007:17:28:24 -0400] Removed temporary file "/var/spool/cups/tmp/4623e9ec5802b"...
D [16/Apr/2007:17:28:24 -0400] Removed temporary file "/var/spool/cups/tmp/4623e9f750000"...
D [16/Apr/2007:17:28:24 -0400] Removed temporary file "/var/spool/cups/tmp/4623ea08d25f5"...
I [16/Apr/2007:17:28:24 -0400] Configured for up to 100 clients.
I [16/Apr/2007:17:28:24 -0400] Allowing up to 100 client connections per host.
I [16/Apr/2007:17:28:24 -0400] Using policy "default" as the default!
I [16/Apr/2007:17:28:24 -0400] Full reload is required.
I [16/Apr/2007:17:28:24 -0400] Loaded MIME database from '/etc/cups': 34 types, 39 filters...
D [16/Apr/2007:17:28:24 -0400] Loading printer postscript-color-printer-rev3b...
I [16/Apr/2007:17:28:24 -0400] Loading job cache file "/var/cache/cups/job.cache"...
D [16/Apr/2007:17:28:24 -0400] Loading job 65 from cache...
D [16/Apr/2007:17:28:24 -0400] Loading job 70 from cache...
I [16/Apr/2007:17:28:24 -0400] Full reload complete.
I [16/Apr/2007:17:28:24 -0400] Listening to 127.0.0.1:631 on fd 0...
I [16/Apr/2007:17:28:24 -0400] Listening to /var/run/cups/cups.sock on fd 2...
I [16/Apr/2007:17:28:24 -0400] Listening to :::631 on fd 3...
E [16/Apr/2007:17:28:24 -0400] Unable to bind socket for address 0.0.0.0:631 - Address already in use.
D [16/Apr/2007:17:28:25 -0400] cupsdNetIFUpdate: "lo" = localhost...
D [16/Apr/2007:17:28:25 -0400] cupsdNetIFUpdate: "wlan0" = 192.168.1.103...
D [16/Apr/2007:17:28:25 -0400] cupsdNetIFUpdate: "lo" = localhost...
D [16/Apr/2007:17:28:25 -0400] cupsdNetIFUpdate: "wlan0" = fe80::216:b6ff:fea5:35e2%wlan0...
I [16/Apr/2007:17:28:28 -0400] Scheduler shutting down normally.
I [16/Apr/2007:17:28:28 -0400] Saving remote.cache...
I [16/Apr/2007:17:28:32 -0400] Listening to 127.0.0.1:631 (IPv4)

```

---

### Post by UltraMathMan on 2007-04-16
Ok, I didn't notice you're using an older version of cups, recomment the Listen directives in cupsd.conf, make sure they are in ports.conf - are you running Ubuntu 6.06? Second, did you add cupsys to the shadow group (see about post)? I googled the **pam_authenticate() returned 7**, and it seems that it stems from not doing this. Also remember that after making changes to any cups config files you need to reload cups with ```
sudo /etc/init.d/cupsys restart
``` Keep me posted.

---

### Post by braddcadd on 2007-04-16
UltraMathMan, thanks for the help!

Port 631 is the only line in my ports.conf file.

Yeah, I am using Dapper (i'm afraid of edgy :) ).  I did the shadow trick but it did not allow me to login to the web-interface with my regular passord/login.

If it helps, I;ve also had trouble with hplip.  I installed it from a downloaded tarball and from the repositories.  I think the conflict between the two caused a problem.  Cups quit sometime during this mishap.

Is there any other diagnostic info I can provide?

---

### Post by UltraMathMan on 2007-04-16
When you try to log into the web interface, do you get any error messages? Do you even get the web interface up at all? It should let you see non-admin stuff without a password. You might try adding ```
 DefaultEncrytion Never
``` to cupsd.conf under DefaultAuthType Basic if you get a **426 - Upgrade Required**. Not at my computer at the moment to check this further, but adding cupsys to shadow should let it read the password file, and let you into the web interface at *localhost:631*...strange.

---

### Post by braddcadd on 2007-04-16
I see the non-admin stuff, but it keeps asking for my passowrd, over and over...

---

### Post by UltraMathMan on 2007-04-16
hmmm, ok make sure you are a member of the lpadmn group with ```
sudo adduser *yourusername* lpadmin
``` (you could also do add cupsys to shadow again to make sure it did go through) if you're already a member (you probably are). Next try adding *shadow* to the groups in cupsd.conf like ```
# Administrator user group...
SystemGroup lpadmin shadow
``` (restart cups). As a last resort you could temporarily disable system authentication (so that it doesn't ask you for a password) by commenting the following in cupsd.conf ```
  # All administration operations require an administrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    #AuthType Basic
    #Require user @SYSTEM
    Order deny,allow
  </Limit>
``` then restart cupsys ```
sudo /etc/init.d/cupsys restart
``` just make sure to uncomment it when you're done making changes in the web interface.

---

### Post by braddcadd on 2007-04-16
OK, something changed.  But now the admin section of the web-interface won;t load.  The start page loads.  Also still can;t start cups.  This is getting crazy...

---

### Post by UltraMathMan on 2007-04-16
I know what you mean, honestly I expected things to be fixed after adding cupsys to shadow. That's all it ever took for me, 6.06 or 6.10. Please post the end of the error_log again so I can see what happened. Where did you stop in my previous post (ie. what did you change). And when you say you can't start cups, do you mean sudo /etc/init.d/cupsys restart fails somehow?

---

### Post by braddcadd on 2007-04-16
I was already a user in lpadmin and in shadow.  I did comment out the login requirement from the conf file.  

Actually sudo /etc/cups/cupsys restart says OK, but a plain start says nothing (it never successfully starts).  I can stop it (just in case) and start does not yeild the un-acheiveable [ok].

Thanks fro you continued help (i am sort of a newbie).  Below is more debug info:
```

D [16/Apr/2007:21:45:11 -0400] cupsdSendError: 7 code=401 (Unauthorized)
D [16/Apr/2007:21:45:11 -0400] cupsdCloseClient: 7
D [16/Apr/2007:21:45:19 -0400] cupsdAcceptClient: 7 from localhost:631 (IPv4)
D [16/Apr/2007:21:45:19 -0400] cupsdReadClient: 7 POST /admin HTTP/1.1
D [16/Apr/2007:21:45:19 -0400] cupsdReadClient: 7 Browser asked for language "en-us.utf-8"...
D [16/Apr/2007:21:45:20 -0400] cupsdAuthorize: username="braddcadd"
D [16/Apr/2007:21:45:20 -0400] CGI /usr/lib/cups/cgi-bin/admin.cgi started - PID = 12167
I [16/Apr/2007:21:45:20 -0400] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=12167)
D [16/Apr/2007:21:45:20 -0400] cupsdSendCommand: 7 file=10
D [16/Apr/2007:21:45:20 -0400] [CGI] admin.cgi started...
D [16/Apr/2007:21:45:21 -0400] [CGI] http=0x8075ab0
D [16/Apr/2007:21:45:21 -0400] [CGI] op="config-server"...
D [16/Apr/2007:21:45:21 -0400] cupsdAcceptClient: 9 from localhost (Domain)
D [16/Apr/2007:21:45:21 -0400] cupsdReadClient: 9 PUT /admin/conf/cupsd.conf HTTP/1.1
D [16/Apr/2007:21:45:21 -0400] cupsdAuthorize: No authentication data provided.
D [16/Apr/2007:21:45:21 -0400] cupsdSendError: 9 code=401 (Unauthorized)
D [16/Apr/2007:21:45:21 -0400] cupsdCloseClient: 9
D [16/Apr/2007:21:45:21 -0400] cupsdAcceptClient: 9 from localhost (Domain)
D [16/Apr/2007:21:45:21 -0400] cupsdReadClient: 9 PUT /admin/conf/cupsd.conf HTTP/1.1
D [16/Apr/2007:21:45:21 -0400] cupsdAuthorize: username="braddcadd"
I [16/Apr/2007:21:45:21 -0400] Installing config file "/etc/cups/cupsd.conf"...
D [16/Apr/2007:21:45:21 -0400] cupsdSendError: 9 code=201 (Created)
D [16/Apr/2007:21:45:21 -0400] cupsdCloseClient: 9
D [16/Apr/2007:21:45:21 -0400] [CGI] cgiCopyTemplateLang(tmpl="header.tmpl")
D [16/Apr/2007:21:45:21 -0400] [CGI] locale="en_us"...
D [16/Apr/2007:21:45:21 -0400] [CGI] Template file is "/usr/share/cups/templates/header.tmpl"...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting at file position 0...
D [16/Apr/2007:21:45:21 -0400] [CGI] "{title}" at 205...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting "{refresh_page?" at 374, result=1...
D [16/Apr/2007:21:45:21 -0400] [CGI] Output first part...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting at file position 374...
D [16/Apr/2007:21:45:21 -0400] [CGI] "{refresh_page}" at 424...
D [16/Apr/2007:21:45:21 -0400] [CGI] Returning at file position 427 on character ':'...
D [16/Apr/2007:21:45:21 -0400] [CGI] Skip second part...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting at file position 427...
D [16/Apr/2007:21:45:21 -0400] [CGI] Returning at file position 428 on character '}'...
D [16/Apr/2007:21:45:21 -0400] [CGI] Finished "{refresh_page?", out=0xb7e770e0...
D [16/Apr/2007:21:45:21 -0400] [CGI] "{title}" at 671...
D [16/Apr/2007:21:45:21 -0400] [CGI] "{title}" at 952...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting "{SECTION=admin" at 1411, result=1...
D [16/Apr/2007:21:45:21 -0400] [CGI] Output first part...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting at file position 1411...
D [16/Apr/2007:21:45:21 -0400] [CGI] Returning at file position 1412 on character ':'...
D [16/Apr/2007:21:45:21 -0400] [CGI] Skip second part...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting at file position 1412...
D [16/Apr/2007:21:45:21 -0400] [CGI] Returning at file position 1415 on character '}'...
D [16/Apr/2007:21:45:21 -0400] PID 12167 (/usr/lib/cups/cgi-bin/admin.cgi) exited with no errors.
D [16/Apr/2007:21:45:21 -0400] [CGI] Finished "{SECTION=admin", out=0xb7e770e0...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting "{SECTION=classes" at 1678, result=0...
D [16/Apr/2007:21:45:21 -0400] [CGI] Skip first part...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting at file position 1678...
D [16/Apr/2007:21:45:21 -0400] [CGI] Returning at file position 1679 on character ':'...
D [16/Apr/2007:21:45:21 -0400] [CGI] Output second part...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting at file position 1679...
D [16/Apr/2007:21:45:21 -0400] [CGI] Returning at file position 1682 on character '}'...
D [16/Apr/2007:21:45:21 -0400] [CGI] Finished "{SECTION=classes", out=0xb7e770e0...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting "{SECTION=help" at 1938, result=0...
D [16/Apr/2007:21:45:21 -0400] [CGI] Skip first part...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting at file position 1938...
D [16/Apr/2007:21:45:21 -0400] [CGI] Returning at file position 1939 on character ':'...
D [16/Apr/2007:21:45:21 -0400] [CGI] Output second part...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting at file position 1939...
D [16/Apr/2007:21:45:21 -0400] [CGI] Returning at file position 1942 on character '}'...
D [16/Apr/2007:21:45:21 -0400] [CGI] Finished "{SECTION=help", out=0xb7e770e0...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting "{SECTION=jobs" at 2206, result=0...
D [16/Apr/2007:21:45:21 -0400] [CGI] Skip first part...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting at file position 2206...
D [16/Apr/2007:21:45:21 -0400] [CGI] Returning at file position 2207 on character ':'...
D [16/Apr/2007:21:45:21 -0400] [CGI] Output second part...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting at file position 2207...
D [16/Apr/2007:21:45:21 -0400] [CGI] Returning at file position 2210 on character '}'...
D [16/Apr/2007:21:45:21 -0400] [CGI] Finished "{SECTION=jobs", out=0xb7e770e0...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting "{SECTION=printers" at 2464, result=0...
D [16/Apr/2007:21:45:21 -0400] [CGI] Skip first part...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting at file position 2464...
D [16/Apr/2007:21:45:21 -0400] [CGI] Returning at file position 2465 on character ':'...
D [16/Apr/2007:21:45:21 -0400] [CGI] Output second part...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting at file position 2465...
D [16/Apr/2007:21:45:21 -0400] [CGI] Returning at file position 2468 on character '}'...
D [16/Apr/2007:21:45:21 -0400] [CGI] Finished "{SECTION=printers", out=0xb7e770e0...
D [16/Apr/2007:21:45:21 -0400] [CGI] Returning at file position 2830 on EOF...
D [16/Apr/2007:21:45:21 -0400] [CGI] cgiCopyTemplateLang(tmpl="restart.tmpl")
D [16/Apr/2007:21:45:21 -0400] [CGI] locale="en_us"...
D [16/Apr/2007:21:45:21 -0400] [CGI] Template file is "/usr/share/cups/templates/restart.tmpl"...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting at file position 0...
D [16/Apr/2007:21:45:21 -0400] [CGI] Returning at file position 52 on EOF...
D [16/Apr/2007:21:45:21 -0400] [CGI] cgiCopyTemplateLang(tmpl="trailer.tmpl")
D [16/Apr/2007:21:45:21 -0400] [CGI] locale="en_us"...
D [16/Apr/2007:21:45:21 -0400] [CGI] Template file is "/usr/share/cups/templates/trailer.tmpl"...
D [16/Apr/2007:21:45:21 -0400] [CGI] Starting at file position 0...
D [16/Apr/2007:21:45:21 -0400] cupsdCloseClient: 7
I [16/Apr/2007:21:45:21 -0400] Saving remote.cache...

```

---

### Post by UltraMathMan on 2007-04-16
I'm glad to help however I can :)

There are no errors in your error_log file, (lines that begin with E), and based on what I've seen so far (I make no claims of being a expert) I'm beginning to suspect something might be wrong with cups itself (something non-config related), if that's the case you could try reinstalling it and see what happens. Before that however try removing "Allow localhost" from ```
# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>
``` as it is redundant with Allow @LOCAL. This *shouldn't* be what's breaking things, but you never know...

Additonally I'm curious about whether cups was ever working, ie. did this just happen or has it always been like this? If it hasn't always been like this, approximately when did it happen and what was going on at the time?

EDIT: Also, do you still have the printer that was causing problems installed, or any printers installed?

---

### Post by braddcadd on 2007-04-17
I've tried un-installing and installing many different ways and many different times.  

The only printer I have installed is a pdf printer (postscript).

If it helps here are some error lines from today's log:
```

E [17/Apr/2007:17:12:35 -0400] Unable to bind socket for address :::631 - Address already in use.
E [17/Apr/2007:17:12:35 -0400] Unable to bind socket for address 0.0.0.0:631 - Address already in use.

```

Cups dies about the time I tried to install hplip.  I did so by two methods.  First I installed it from a tarball that i got off the hplip website, then I realized Ubuntu had it in the repository (so I installed it too).  The confilct between the two has kept my scanner from working.  I have recently gotten the scanner/cups to work well on another Unbuntu machine.

I was fighting with hplip and Officeject 5610 when all this occured.  See my thread for that problem, [http://ubuntuforums.org/showthread.php?t=329452](http://ubuntuforums.org/showthread.php?t=329452) .

Thanks again.

---

### Post by UltraMathMan on 2007-04-18
First, those errors indicate something is use port 631 from two places, make sure you don't have Listen 631 uncommented in both cupsd.conf and /etc/cups/ports.conf. I'm going to load up a 6.06 live cd and install hplip to see if it causes some sort of conflict, I'll get back to you after that. Hopefully we'll get this sorted out soon :)

---

### Post by braddcadd on 2007-04-18
Hey Thanks!

browse.conf had the line "Browsing on"

ports.conf had the line "Port 631"

So I commented them both out.

The conflict was actually caused by two versions of hplip.  I did the manual install first [http://hplip.sourceforge.net/install/manual/distros/ubuntu.html](http://hplip.sourceforge.net/install/manual/distros/ubuntu.html)

Then I did apt-get install hplip.  I read that conflict can be a problem in a man page somewhere (I think).

Here are the packages I have that start with hp*:
(I must have hplip (repository version) uninstalled now)
```

hpijs                                           install
hplip                                           deinstall
hplip-data                                      install
hplip-ppds                                      install
hpoj                                            deinstall

```

---

### Post by UltraMathMan on 2007-04-18
If there is a conflict between the two installed versions of hplip, you'll also need to uninstall hplip-data and hplip-ppds, as these were probably installed along with hplip. See if your version of apt-get has the auto remove function```
sudo apt-get remove --auto-remove hplip
``` This will remove all packages that were installed along with hplip (except those still being used). If it doesn't have auto remove, try removing hplip-data and hplip-ppds normally. You'll probably need to uncomment Port 631 to print eventually (or add another address, I'll need to look it up). 

Removing the manually installed package (if you wanted to do so) would be more difficult probably as the guide you posted instructs you to use "make install". For future reference, when installing from source using "checkinstall -D" is a better option as it creates a .deb file and installs that, making removal much easier.

So try removing those files and see what happens.

Also, when you try to do ```
sudo /etc/init.d/cupsys start
``` do you do ```
sudo /etc/init.d/cupsys stop
``` first? Not sure if this is necessary in older versions of CUPS, but it might be causing problems if you try to start the service without stopping it.

---

### Post by braddcadd on 2007-04-21
ok, back to the good fight!

I did remove those packages but it didn't change anything for me.  Here is and [E] from my error log if it helps:
```

E [21/Apr/2007:15:38:38 -0400] Creating missing directory "/var/run/cups/certs"

```

Is there an alternative to cups? (or is there more stuff to try)

---

### Post by UltraMathMan on 2007-04-21
There are alternatives to CUPS (such as LPRng) but if I recall they conflict with CUPS which is a dependency for GNOME, so trying to install it causes some problems as, at least aptitude tries to remove CUPS which breaks GNOME first. Could you note the end of the error log now, then do ```
sudo /etc/init.d/cupsys stop
``` then ```
sudo /etc/init.d/cupsys start
``` and post the output and the difference in the error log (the stuff that's after the place you noted before).

---

### Post by braddcadd on 2007-04-21
hey your fast...

OK, I cleared the error_log first.  So before is blank.

after:
```

I [21/Apr/2007:17:29:32 -0400] Scheduler shutting down normally.
I [21/Apr/2007:17:29:32 -0400] Saving remote.cache...
I [21/Apr/2007:17:29:37 -0400] Listening to :::631 (IPv6)
I [21/Apr/2007:17:29:37 -0400] Listening to 0.0.0.0:631 (IPv4)
I [21/Apr/2007:17:29:37 -0400] Listening to /var/run/cups/cups.sock (Domain)
I [21/Apr/2007:17:29:37 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [21/Apr/2007:17:29:37 -0400] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [21/Apr/2007:17:29:37 -0400] Configured for up to 100 clients.
I [21/Apr/2007:17:29:37 -0400] Allowing up to 100 client connections per host.
I [21/Apr/2007:17:29:37 -0400] Using policy "default" as the default!
I [21/Apr/2007:17:29:37 -0400] Full reload is required.
I [21/Apr/2007:17:29:37 -0400] Loaded MIME database from '/etc/cups': 34 types, 39 filters...
D [21/Apr/2007:17:29:37 -0400] Loading printer postscript-color-printer-rev3b...
I [21/Apr/2007:17:29:37 -0400] Loading job cache file "/var/cache/cups/job.cache"...
D [21/Apr/2007:17:29:37 -0400] Loading job 65 from cache...
D [21/Apr/2007:17:29:37 -0400] Loading job 70 from cache...
I [21/Apr/2007:17:29:37 -0400] Full reload complete.
I [21/Apr/2007:17:29:37 -0400] Listening to :::631 on fd 0...
I [21/Apr/2007:17:29:37 -0400] Listening to 0.0.0.0:631 on fd 2...
I [21/Apr/2007:17:29:37 -0400] Listening to /var/run/cups/cups.sock on fd 3...

```

---

### Post by UltraMathMan on 2007-04-21
Instant email subscription + gmail notifier :)

 Everything looks normal, do you have a printer you can try to add?

---

### Post by braddcadd on 2007-04-21
When I go to System->Administration->Printing it says Cups server un-available.

---

### Post by UltraMathMan on 2007-04-21
Alright, at this point I'd try reinstalling CUPS with ```
sudo apt-get install --reinstall cupsys
```

---

### Post by braddcadd on 2007-04-21
I hate to keep bringing bad news, but no changes on my end.  At this point I may just either live with it or start collecting my data/settings and do a fresh install soon.

Can you think of anything else that I should try?  I am willing if you are!

(btw - what kind of math are you into?)

---

### Post by UltraMathMan on 2007-04-21
I'm sorry to say it but I'm about out of ideas at this point, and with the release of 7.04, a fresh install/upgrade may not be a bad idea (I know I'll be upgrading after my exams).

As a undergrad I don't have a fixed particular interest in a specific part of math yet, but I'm currently taking courses in Combinatorics, Discrete Math, Complex Variables, and Unique and Nonunique Factorization. Fun stuff all of it. :)

---

### Post by braddcadd on 2007-04-21
Thanks for all your help.  Good luck with school.

I'm sure a fresh install will work as I have done so recently with my desktop.

---

### Post by UltraMathMan on 2007-04-21
Thanks, sorry I wasn't able to get things working again for you.

---

### Post by be4truth on 2007-05-03
I assume you want to contact the cups server on your own machine. I had the same problem.
1)    /etc/inid/cupsys stop
2)    apt-get --purge cupsys
3)    apt-get install cupsys

That's removed all the bad stuff and gave me a clean start.

---

### Post by braddcadd on 2007-06-12
I've tried restarting, un-installing, and removing both versions of hplip.  I've also tried re-installing.  All to no avail.  I've now upgraded from dapper, though edgy, to feisty.  I still suffer from the same CUPS problem.

take a look at this (not sure what to do with it):
```

gnome-cups-manager
GTK Accessibility Module initialized
Bonobo accessibility support initialized

** (gnome-printer-view:11352): WARNING **: IPP request failed with status 1280

** (gnome-printer-view:11352): WARNING **: IPP request failed with status 1280

```

Can anyone help?

---

### Post by John CCC on 2007-07-06
> **be4truth said:**
> I assume you want to contact the cups server on your own machine. I had the same problem.
1)    /etc/inid/cupsys stop
2)    apt-get --purge cupsys
3)    apt-get install cupsys

That's removed all the bad stuff and gave me a clean start.

I'm getting the same error message.. Just hoping it is not as persistent of a problem.

Anyway, I'd certainly like to try the above solution, but I'm a noobee and I'm unfortunately getting tripped up at the first line. The result is as follows: > john@niamh:~$ /etc/inid/cupsys stop
bash: /etc/inid/cupsys: No such file or directory

Is my command wrong?

---

### Post by braddcadd on 2007-07-14
```

/etc/init.d/cupsys stop

```

---

### Post by braddcadd on 2007-07-22
Well, I finally got lucky on this one.  I did a fresh install on another computer, then copied the "/etc/cups" directory over from that computer.  With an un-foo'd copy of "/etc/cups" directory everything works fine now.

I hop this helps someone else!

---

