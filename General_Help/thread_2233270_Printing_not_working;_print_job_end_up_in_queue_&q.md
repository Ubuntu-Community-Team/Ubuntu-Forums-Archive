---
title: "Printing not working; print job end up in queue &quot;processing&quot; – CUPS problem?"
date: 2014-07-07
forum: General Help
---

### Post by Z80A on 2014-07-07
In the past I haven't had to much problems with printing from Ubuntu - maybe I don't print enough. But having revived a Windows XP based system recently (nice little Atom desktop system now performing really well with Lubuntu 14.04), I have (well the user of the system has) plenty of problems with printing. 

The printer (an older HP895Cxi) is connect to the parallel printer port, and even though printing did works out the box, after installing/detecting the printer automatically (no HP-LIB installed), it now fails mostly (Ubuntu and Wine applications). When printing the job pops up correctly in the printing queue, but consistently end up with status "Processing". Other print job are then stuck.

 When accessing CUPS ([http://localhost:631](http://localhost:631)), the printer is defined like this:

```
 Description:    HEWLETT-PACKARD DESKJET 895C
 Location:    EL1600
 Driver:    HP DeskJet 895C - CUPS+Gutenprint v5.2.10-pre2 (color, 2-sided printing)
 Connection:    parallel:/dev/lp0
 Defaults:    job-sheets=none, none media=iso_a4_210x297mm sides=one-sided
```

The configuration file looks like this:

```
#
#
# Sample configuration file for the CUPS scheduler.  See "man cupsd.conf" for a
# complete description of this file.
#

# Log general information in error_log - change "warn" to "debug"
# for troubleshooting...
LogLevel warn

# Deactivate CUPS' internal logrotating, as we provide a better one, especially
# LogLevel debug2 gets usable now
MaxLogSize 0

# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseLocalProtocols dnssd

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Web interface setting...
WebInterface Yes

# Restrict access to the server...
<Location />
  Order allow,deny
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    Order deny,allow
  </Limit>

   <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job  Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription  Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job  Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job  CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
   <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer  CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default  CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
   <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer  Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs  Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer  Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs  CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
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

# Set the authenticated printer/job policies...
<Policy authenticated>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Default
    Order deny,allow
  </Limit>

   <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job  Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription  Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job  Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job  CUPS-Get-Document>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
   <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer  Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs  Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer  Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs  CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    AuthType Default
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

The Error Log has some entries that could maybe indicate some problems:

```
 W [08/Jun/2014:09:49:06 +0200] CreateProfile failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
 W [08/Jun/2014:09:49:06 +0200] CreateProfile failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
 W [08/Jun/2014:09:49:06 +0200] CreateDevice failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
 E [08/Jun/2014:13:49:41 +0200] [Job 15] Stopping unresponsive job.
 E [08/Jun/2014:16:46:29 +0200] [Job 16] Stopping unresponsive job.
 E [08/Jun/2014:16:52:04 +0200] [cups-deviced] PID 28499 (dnssd) stopped with status 1!
 E [08/Jun/2014:17:03:12 +0200] [Job 18] Stopping unresponsive job.
 E [08/Jun/2014:17:25:49 +0200] [Job 21] Stopping unresponsive job.
 W [08/Jun/2014:18:29:16 +0200] CreateProfile failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
 W [08/Jun/2014:18:29:16 +0200] CreateProfile failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
 W [08/Jun/2014:18:29:16 +0200] CreateDevice failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
```

Any ideas?

---

