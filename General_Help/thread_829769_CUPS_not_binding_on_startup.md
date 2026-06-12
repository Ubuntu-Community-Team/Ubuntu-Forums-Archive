---
title: "CUPS not binding on startup"
date: 2008-06-15
forum: General Help
---

### Post by jambalaya on 2008-06-15
Hi. I configured CUPS so that it listens on my LAN ip. However, when I start my laptop, CUPS is started, but it is not actually bound to my network interface. It only binds to 631/udp. When I invoke-rc.d cupsys start, nothing changes, but restart does the trick. So I think that CUPS is actually started, so another start is just a no-op, and restart works. Also, after restart, CUPS does bind to the address.
Could anyone tell me what happens? Why can't CUPS bind on startup? Maybe I'm used wrong numbers when I created the links in /etc/rcX.d directories? I creatd then using sudo update-rc.d cupsys defaults, so the links start with S20 prefix. It looks as if it was to early in the process, before networking actually started, but I might be wrong. Could anyone please tell me what to change to make it right?
Also, I don't fully understand the Browsing On/Off directive in the conf files. Does it relate to my machine getting or sending browse packets? I don't need to get those, as I have the only printer in the LAN. Here is my cupsd.conf in case you need to see it:
```

# Log level
LogLevel notice

# Administrator user group
SystemGroup lpadmin

# Listen for connections on LAN only, use UNIX domain sockets for local printing
Listen 192.168.1.17:631
Listen /var/run/cups/cups.sock

# Show my printer on the local network
Browsing On
BrowseAddress @LOCAL

# Default authentication type
DefaultAuthType Basic

# Do not use encryption
DefaultEncryption Never

# Retry jobs on error - maybe I forgot to turn on the printer?
# Defaults to 5 attempts, with 30s interval
ErrorPolicy retry-job

# Restrict access to the server
<Location />
  Order allow,deny
  Allow @LOCAL
</Location>

# Restrict access to the admin pages
<Location /admin>
  Order allow,deny
  Allow @LOCAL
  Require user @SYSTEM
</Location>

# Restrict access to configuration files
<Location /admin/conf>
  Order allow,deny
  Allow @LOCAL
  Require user @SYSTEM
</Location>

# Default policy to use
DefaultPolicy default

# Set the default printer/job policies
<Policy default>
  # Job-related operations must be done by the owner or an administrator
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Order allow,deny
    Allow @LOCAL
    Require user @OWNER @SYSTEM
  </Limit>

  # All administration operations require an administrator to authenticate
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    Order allow,deny
    Allow @LOCAL
    Require user @SYSTEM
  </Limit>

  # All printer operations require a printer operator to authenticate
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    Order allow,deny
    Allow @LOCAL
    Require user @SYSTEM
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Order allow,deny
    Allow @LOCAL
    Require user @OWNER @SYSTEM
  </Limit>

  <Limit All>
    Order allow,deny
    Allow @LOCAL
  </Limit>
</Policy>

# Don't preserve job files nor history
PreserveJobFiles Off
PreserveJobHistory Off

Timeout 30

```

Thank you.

---

