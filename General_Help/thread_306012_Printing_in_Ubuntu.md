---
title: "Printing in Ubuntu"
date: 2006-11-24
forum: General Help
---

### Post by madsurfer on 2006-11-24
Hi
I have a problem printing in Ubuntu. I have a usb printer connected to a Ubuntu machine, which when I printed to from another Ubuntu machine worked well. I also have several win xp machines which I wanted to get printing. I have tried to get the windows machines printing using samba and cups, but could not get printing to work on the windows machines getting permission denied errors. While fiddling about trying to get my printer working on the windows machine, my cups system stopped working. Now every time I try to access it I get the error "the CUPs server could not be contacted"

I restored my cupsd.conf file but to no avail. Here below is my cupsd.conf file

DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.1.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

What have I done to the systems to cause this error. Any help would be much appreciated.

Adrian

---

### Post by madsurfer on 2006-11-24
Further to this problem if a do a lpstat -v on my ok system I get :-

adrianr@md11:~$ lpinfo -v
network socket
network beh
network bluetooth
direct hp:/no_device_found
network http
network ipp
network lpd
network smb

but if I do the same on one of my other systems I get:

adrianr@spitfire:~$ lpinfo -v
lpinfo: Unable to connect to server: Connection refused

Is this a permissions problem? and if it is where do I change things to fix it?

Adrian

---

### Post by madsurfer on 2006-11-24
Hi

This problem has really got me stuck, have even tried to uninstall and reinstall cups to no avail. If I don't fix it I may have to go back to windows!!!
Please please please can anyone help

Adrian

---

### Post by David Corrales on 2006-11-24
I changed my samba authentication level from user to share and it works. I still get the "permission denied errors" from windows but it still prints fine.

---

### Post by madsurfer on 2006-11-24
Thanks for the info, glad to see that someone is looking at my question!! Will try this out when the printing is solved, at the moment I cant get past "the CUPS server could not be contacted" problem, any ideas out there?!
Adrian

---

### Post by David Corrales on 2006-11-26
Here's my default edgy cups config file:
```

#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
Listen 631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
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

#
#

```

---

### Post by juseal on 2007-01-26
I followed this thread and it started working for me.
[http://ubuntuforums.org/showthread.p...ould+contacted](http://ubuntuforums.org/showthread.p...ould+contacted)

A condensed version is:

Remove cups

sudo apt-get remove cupsys cupsys-client

Purge cups

sudo apt-get remove --purge cupsys cupsys-client

Re-install cups

sudo apt-get install cupsys cupsys-client

I hope that helps

---

