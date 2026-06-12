---
title: "CUPS: Name Unknown, User Withheld, Empty Page_Log"
date: 2013-01-11
forum: General Help
---

### Post by Kirk Schnable on 2013-01-11
I am presently trying to set up proper reporting on my new CUPS server.  My old server is running CUPS 1.4.3.  My new server is running CUPS 1.5.3.

I copied cupsd.conf from my old server to my new server to bring over all of my policies, and I then re-added the printers I wanted on the new server.

My page_log file is completely empty (I need the normal page logging to happen for my reporting).  But the web interface shows the jobs which have existed previously...

When a user prints a document, other than using the test page from the web interface, the username shows as "Withheld" and their job name shows as "Unknown".

[[img]http://binaryimpulse.com/wp-content/uploads/2013/01/CUPS-Server-Shows-Withheld-Unknown-Information-669x600.png[/img]]("http://binaryimpulse.com/wp-content/uploads/2013/01/CUPS-Server-Shows-Withheld-Unknown-Information.png")

I have added **JobPrivateAccess all** and **JobPrivateValues none** to my default policy in cupsd.conf.

Here is my cupsd.conf:
```
#	test---test
#
# Sample configuration file for the CUPS scheduler.  See "man cupsd.conf" for a
# complete description of this file.
#

# Log general information in error_log - change "warn" to "debug"
# for troubleshooting...
LogLevel warn

#Set default encryption - 'Never' = not over SSL, which would need HTTPS
DefaultEncryption Never

# Deactivate CUPS' internal logrotating, as we provide a better one, especially
# LogLevel debug2 gets usable now
MaxLogSize 0

# Administrator user group...
SystemGroup lpadmin

ServerAlias *

# Only listen for connections from the local machine.
Listen server.ip.address.removed:631
Listen /var/run/cups/cups.sock

MaxClients 1024
MaxClientsPerHost 128
ListenBackLog 50

# Show shared printers on the local network.
Browsing On
# BrowseAddress @IF(eth0)
BrowseAddress 10.9.255.255
BrowseOrder allow,deny
BrowseAllow all
BrowseLocalProtocols CUPS dnssd
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
  Allow @LOCAL
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
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
  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI>
    AuthType Default
    Order deny,allow
  </Limit>

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
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
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
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

# Added for Troubleshooting
	JobPrivateAccess all
	JobPrivateValues none
# End of Troubleshooting

</Policy>

#
#
```

Here is my cups-files.conf:
```
#
#
# Sample file/directory/user/group configuration file for the CUPS scheduler.
# See "man cups-files.conf" for a complete description of this file.
#

# List of events that are considered fatal errors for the scheduler...
#FatalErrors config

# Default user and group for filters/backends/helper programs; this cannot be
# any user or group that resolves to ID 0 for security reasons...
#User lp
#Group lp

# Administrator user group, used to match @SYSTEM in cupsd.conf policy rules...
SystemGroup lpadmin


# User that is substituted for unauthenticated (remote) root accesses...
#RemoteRoot remroot

# Do we allow file: device URIs other than to /dev/null?
#FileDevice No

# Permissions for configuration and log files...
#ConfigFilePerm 640
#LogFilePerm 0640

# Location of the file logging all access to the scheduler; may be the name
# "syslog". If not an absolute path, the value of ServerRoot is used as the
# root directory.  Also see the "AccessLogLevel" directive in cupsd.conf.
AccessLog /var/log/cups/access_log

# Location of cache files used by the scheduler...
#CacheDir /var/cache/cups

# Location of data files used by the scheduler...
#DataDir /usr/share/cups

# Location of the static web content served by the scheduler...
#DocumentRoot /usr/share/cups/doc-root

# Location of the file logging all messages produced by the scheduler and any
# helper programs; may be the name "syslog". If not an absolute path, the value
# of ServerRoot is used as the root directory.  Also see the "LogLevel"
# directive in cupsd.conf.
ErrorLog /var/log/cups/error_log

# Location of fonts used by older print filters...
#FontPath /usr/share/cups/fonts

# Location of LPD configuration
#LPDConfigFile 

# Location of the file logging all pages printed by the scheduler and any
# helper programs; may be the name "syslog". If not an absolute path, the value
# of ServerRoot is used as the root directory.  Also see the "PageLogFormat"
# directive in cupsd.conf.
PageLog /var/log/cups/page_log

# Location of the file listing all of the local printers...
#Printcap /var/run/cups/printcap

# Format of the Printcap file...
#PrintcapFormat bsd
#PrintcapFormat plist
#PrintcapFormat solaris

# Location of all spool files...
#RequestRoot /var/spool/cups

# Location of helper programs...
#ServerBin /usr/lib/cups

# SSL/TLS certificate for the scheduler...
#ServerCertificate ssl/server.crt

# SSL/TLS private key for the scheduler...
#ServerKey ssl/server.key

# Location of other configuration files...
#ServerRoot /etc/cups

# Location of Samba configuration file...
#SMBConfigFile 

# Location of scheduler state files...
#StateDir /var/run/cups

# Location of scheduler/helper temporary files. This directory is emptied on
# scheduler startup and cannot be one of the standard (public) temporary
# directory locations for security reasons...
#TempDir /var/spool/cups/tmp

#
#
```

Any ideas why I'm missing so much information?

Thanks,
Kirk

---

### Post by Kirk Schnable on 2013-01-11
Oh!  I realized my mistake with the web interface.

I had placed the **JobPrivateAccess all** and **JobPrivateValues none** in the *authenticated* policy, not the *default* policy.

After copying those directives into my Default policy, I now have the information.

On to why I don't have page logs.....

---

### Post by Kirk Schnable on 2013-01-11
In doing my reading, I found that this could be a problem related to the PPD being used for the printer.

We have been using **	Generic PCL 5e Printer Foomatic/hpijs-pcl5e** for our printers up until now.

I tried copying the old version of this PPD file from my old CUPS server, and I still do not have a page_log when printing to those printers.

I did try a new driver, and when printing to a printer using **HP LaserJet 4050 Series pcl3, hpcups 3.12.2**, I do have a page log.  CUPS also shows page numbers for the job, rather than "Unknown" on the web interface.

It seems like a PPD issue, but copying the old PPD doesn't resolve the issue, and I don't really feel inclined to switch drivers, because we had switched from HP drivers to Generic drivers to resolve some printing hiccups last year.

---

