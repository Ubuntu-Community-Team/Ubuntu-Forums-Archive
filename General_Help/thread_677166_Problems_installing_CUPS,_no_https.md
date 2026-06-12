---
title: "Problems installing CUPS, no https"
date: 2008-01-24
forum: General Help
---

### Post by XP-FREAK on 2008-01-24
Hi,

my Server is running on debian and has no X installed. I hope this makes no sense if I post this problem here or in a debian forum.

I installed HPLIP, CUPSYS and so on and changed the cups configuragtion so that I can access the CUPS configuration page from outside, because without X it isn't very comfortable although links, lynx and so on don't like that config page.

I can see that my printer is found, can choose the right ppd file but then, the page redirects me to

[https://blackbox:631/admin](https://blackbox:631/admin)

what does not load :(

My configuration looks like this:

```

[...]
Listen localhost:631
Listen 192.168.1.120:631
Listen /var/run/cups/cups.sock
[...]
DefaultAuthType Basic
[...]
# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow 192.168.1.*
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Encryption Required
  Order allow,deny
  Allow localhost
  Allow 192.168.1.*
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
  Allow 192.168.1.*
</Location>
[...]

```

Does anyone know this problem? Can somebody help me?

---

### Post by UltraMathMan on 2008-01-25
Here's the cupsd.conf file from my working headless server: ```
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel info

# Administrator user group...
SystemGroup lpadmin sys root

# Only listen for connections from the local machine.
Listen 631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow @LOCAL
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow @LOCAL
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow @LOCAL
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

-Hope this helps :)

---

