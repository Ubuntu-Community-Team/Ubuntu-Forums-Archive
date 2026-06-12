---
title: "Cups printer error using Printer HP LaserJet 4350"
date: 2008-01-25
forum: General Help
---

### Post by sirisian on 2008-01-25
I set up a Cups and pykota printing system, but now I'm getting an error.

I should first say that I uninstalled app armor. An employee at another division of our department said it caused problems when he set up his system.

In /var/log/cups/error_log
Only error I'm getting:
> E [25/Jan/2008:13:07:59 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory

Did I not install something?

I've been googling but haven't found anything that would work with a LaserJet 4350 printer.

This is my cupsd.conf file:

> 
# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
Listen *:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
  Allow from all
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
  Allow from all
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
  Allow from all
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

#
# Printcap: the name of the printcap file.  Default is /etc/printcap.
# Leave blank to disable printcap file generation.
#

Printcap /var/run/cups/printcap

//random comments after this point


If you need any other information I'll supply it. I am completely lost.

---

### Post by nemilar on 2008-01-25
You should check ou t this page on LinuxPrinting.org: 
[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4350]("http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4350")

You can use their PPD file if you want, or you can install hpijs which works great with HP printers, too.  That site has instructions on how to do both.

Hope this helps!

---

### Post by sirisian on 2008-01-25
> **nemilar said:**
> You should check ou t this page on LinuxPrinting.org: 
[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4350]("http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4350")

You can use their PPD file if you want, or you can install hpijs which works great with HP printers, too.  That site has instructions on how to do both.

Hope this helps!It's not a driver issue. I think it's for something else in cups maybe.

[http://ubuntuforums.org/showthread.php?t=581948](http://ubuntuforums.org/showthread.php?t=581948)

That has my same problem, but doesn't work more me. I figure this is just an overall Gutsy bug.

---

