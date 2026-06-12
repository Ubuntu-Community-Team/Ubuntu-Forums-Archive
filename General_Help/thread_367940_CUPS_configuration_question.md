---
title: "CUPS configuration question"
date: 2007-02-22
forum: General Help
---

### Post by uzd4ce on 2007-02-22
I'm trying to access a printer that is installed on my desktop from my wireless laptop.  When i try to print, it says it cannot access the server, and will try again in 30 seconds.

I figure I did something wrong in my cupsd.conf file that doesn't allow the remote access.

Can someone take a look and see if anything jumps out as being the problem?

Thanks.

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
Listen localhost:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress 192.168.1.255

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
 Order allow,deny
 Allow localhost
 Allow @LOCAL
Allow 192.168.0.*
Allow from 192.168.0.*
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
 <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job
Purge-Jobs Set-Job-Attributes Create-Job-Subscription
Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job
Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
   Require user @OWNER @SYSTEM
   Order deny,allow
 </Limit>

 # All administration operations require an adminstrator to authenticate...
 <Limit Pause-Printer Resume-Printer Set-Printer-Attributes
Enable-Printer Disable-Printer Pause-Printer-After-Current-Job
Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer
Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer
Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer
CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs
CUPS-Set-Default>
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
#added by Bill based on web CUPS tutorial
ServerName 192.168.0.100

---

### Post by UltraMathMan on 2007-02-24
Looks to me like CUPS isn't set to listen for incoming requests > # Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock Take a look at the CUPS Configuration info here : [CUPS Config]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/cups.html")

Hope this helps :)

---

### Post by uzd4ce on 2007-02-24
> **UltraMathMan said:**
> Looks to me like CUPS isn't set to listen for incoming requests  Take a look at the CUPS Configuration info here : [CUPS Config]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/cups.html")

Hope this helps :)

Yeah, commenting out all the existing Listen entries and adding just Listen *:631 did the trick.

Thanks

---

