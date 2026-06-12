---
title: "Print from Mac"
date: 2007-04-19
forum: General Help
---

### Post by MacPC on 2007-04-19
Hi,

My HP printer is connected to my Ubuntu PC. I want the Mac to use it as a network printer. I tweaked the cupsd.conf to turn on printer sharing, at least that's what I think it's done. On my Mac, I used Add Printer, in it I used IPP printer and typed in the URL  [http://192.168.1.102:631/printer/Deskjet-630C](http://192.168.1.102:631/printer/Deskjet-630C)
I thought this is the way to connect to a IPP printer. But when I try tp print from the Mac, I got a error mesage saying the printer is busy, what did I do wrong? 

Below is my cupsd.conf configuration, I hope someone can help me. I appreciate it.

MacPC


My cupsd.conf file:

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
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
 Listen localhost:631
 Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
# The 'Browsing' setting is configured in /etc/cups/cups.d/browse.conf
# so that changing it does not require to change this file.
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

# Include files in /etc/cups/conf.d
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf

#
#

---

### Post by fanatik on 2007-04-19
Hi,

I'm no cups expert, but perhaps the

**Listen** option should be opened up to allow connections from other machines? you could try:

Listen *:631

Also take a look at /var/log/cups/error_log and see if there is anything obvious in there.

James.

---

### Post by MacPC on 2007-04-19
Hi fanatik,

Thanks for the reply.

Silly me, my cupsd.conf was all wrong. :lolflag:  I found this [http://ubuntuforums.org/showthread.php?t=310450](http://ubuntuforums.org/showthread.php?t=310450).

It really helps, Thanks to metalhippyrich. It works great now. :guitar:  

MacPC.

---

