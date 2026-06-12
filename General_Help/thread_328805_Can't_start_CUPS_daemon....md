---
title: "Can't start CUPS daemon..."
date: 2006-12-31
forum: General Help
---

### Post by xpan on 2006-12-31
I have made some changes in the config files and now I can't start the CUPS daemon.

Here is why:

> 
E [31/Dec/2006:11:30:13 +0200] Creating missing directory "/var/run/cups/certs"
I [31/Dec/2006:18:15:12 +0200] Listening to :::631 (IPv6)
I [31/Dec/2006:18:15:12 +0200] Listening to 0.0.0.0:631 (IPv4)
I [31/Dec/2006:18:15:12 +0200] Listening to /var/run/cups/cups.sock (Domain)
I [31/Dec/2006:18:15:12 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
I [31/Dec/2006:18:15:12 +0200] Using default TempDir of /var/spool/cups/tmp...
I [31/Dec/2006:18:15:12 +0200] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [31/Dec/2006:18:15:12 +0200] Configured for up to 100 clients.
I [31/Dec/2006:18:15:12 +0200] Allowing up to 100 client connections per host.
I [31/Dec/2006:18:15:12 +0200] Using policy "default" as the default!
I [31/Dec/2006:18:15:12 +0200] Partial reload complete.
E [31/Dec/2006:18:15:12 +0200] Unable to bind socket for address :::631 - Permission denied.
E [31/Dec/2006:18:15:12 +0200] Unable to bind socket for address 0.0.0.0:631 - Permission denied.
I [31/Dec/2006:18:15:12 +0200] Listening to /var/run/cups/cups.sock on fd 0...
E [31/Dec/2006:18:15:12 +0200] cupsdStartBrowsing: Unable to bind broadcast socket - Permission denied.


and here is the cupsd.conf

> # Show general information in error_log.
LogLevel info
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow @LOCAL
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  # Only the owner or an administrator can cancel a job...
  <Limit Cancel-Job>
    Order deny,allow
    Require user @OWNER @SYSTEM
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>


I tried to make my CUPS server listen to remote computers. I have another KUBUNTU installation that doesn't connect to [http://192.168.1.64:631](http://192.168.1.64:631)

any help would be appreciated
Chris

---

### Post by ingo on 2007-01-02
Might the following have anything to do with your problem? Found it after googling one of your error codes...

** cupsd Runs as the User lp **

 On start-up, cupsd changes from the user root to the user lp as specified in /etc/cups/cupsd.conf: 
 User lp
Group lp
RunAsUser Yes
If "RunAsUser" is set to "No", cupsd will continue to run as root. 
Advantage:
 Improved security, as the CUPS print service does not run with unlimited permissions, but only with permissions needed for the print service. 
Disadvantage:
 The authentication (the password verification) cannot take place via /etc/shadow, as lp does not have access to /etc/shadow. Therefore "AuthType Basic" does not work in this case. Rather, the CUPS-specific authentication via /etc/cups/passwd.md5 must be used. In /etc/cups/cupsd.conf, this can be specified as follows: 
 <Location /admin>
AuthType BasicDigest
AuthClass Group
AuthGroupName sys
...
</Location>
Additionally, the following command must be used (as the user root) to enter a CUPS-specific password for the user root in /etc/cups/passwd.md5: 
 lppasswd -g sys -a root
If "AuthType" is set to "Basic", the password verification will take place with /etc/shadow. In this case, cupsd must run as root (i.e., "RunAsUser No"). 
Additional consequences:

 [LIST]
[*] If cupsd runs as lp, /etc/printcap cannot be generated, as lp is not permitted to create files in /etc/. For this reason, cupsd creates cupsd /etc/cups/printcap as specified in /etc/cups/cupsd.conf:[/LIST] Printcap /etc/cups/printcap
For applications that can only read queue names from /etc/printcap to work properly, /etc/printcap is a symbolic link to /etc/cups/printcap.
[LIST]
[*] As soon as cupsd starts running as lp, port 631 cannot be opened. Therefore, cupsd can no longer be reloaded with "rccups reload". Instead, use "rccups restart".
[*] If HP all-in-one devices (e.g., HP OfficeJet) are addressed by way of the "ptal" service, this will not work if the user root set an unsuitable "umask" when executing "ptal-init setup". In this case, ptal would have created the directories /dev/ptal-printd and /var/run/ptal-* with insufficient access permissions. Suitable access permissions that enable cupsd to send data to ptal devices as the user lp can be set with the following command:[/LIST] chmod a+rx /dev/ptal-printd /var/run/ptal-*
See the article "HP OfficeJet" for more information on HP all-in-one devices.

---

### Post by xpan on 2007-01-02
thanks, I 'll try what you suggest and report back! :)

---

