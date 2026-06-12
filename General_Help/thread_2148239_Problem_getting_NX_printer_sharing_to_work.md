---
title: "Problem getting NX printer sharing to work"
date: 2013-05-24
forum: General Help
---

### Post by SaturnusDJ on 2013-05-24
Something goes wrong in connecting the printer of the client to the server containing the NX environment.

**After connecting:**
**- For shares, error: **
[I]Cannot mount share 'print$'
Error: Wrong character '$' in argument: '//computer/print$'.[/I]

**- For printer:**
[I]We detected, that you have previously configured a driver for printer 'printername'.
The old choice was: 'HP Color LaserJet 2800 Foomatic/Postscript'.
To accept your previous choice click on OK, to reconfigure the printer click on Configure.[/I]

This part is good. After clicking Ok for this window and the following (saying printer added etc), printing from gedit fails, with this error in /var/log/cups/error_log

[SIZE=4][I]Session setup failed: NT_STATUS_LOGON_FAILURE
No ticket cache found for userid=1003
Can not get the ticket cache for myusername
Session setup failed: NT_STATUS_LOGON_FAILURE
Tree connect failed (NT_STATUS_ACCESS_DENIED)
Unable to connect to CIFS host, will retry in 60 seconds...[/I][/SIZE]




Client is Vista. Firewall disabled.
Host is Ubuntu 12.04. Firewall disabled. Csf disabled. Apparmor disabled.


/etc/samba/smb.conf
```


[global]
        workgroup = WORK
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        printcap name = cups
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        print ok = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

```


/usr/NX/etc/server.cfg
```


ConfigFileVersion = "2.0"

SessionLogLevel = "7"

SSHDPort = "22"

EnableClipboard = "both"

EnableUserDB = "0"

EnablePasswordDB = "0"

SSHDAuthServer = "127.0.0.1"

SSHDAuthPort = "22"

```


/usr/NX/etc/node.cfg
```


ConfigFileVersion = "2.0"

SessionLogLevel = "6"

CommandFuser = "/bin/fuser"

ShareBasePath = "$(HOME)/MyShares"

EnableFileSharing = "1"

CUPSBinPath = "/usr/bin"

CUPSSbinPath = "/usr/sbin"

EnableCUPSSupport = "1"

CUPSAddPrinterMode = "localhost"

MountShareProtocol = "both"

SSHDPort = "22"

CommandStartGnome = "/etc/X11/Xsession gnome-session"

CommandStartKDE = "/etc/X11/Xsession startkde"

```

---

### Post by SaturnusDJ on 2013-05-27
Kick!

Some help is really appreciated.


/etc/cups/cupsd.conf
```
LogLevel warn
MaxLogSize 0
Listen localhost:631
Listen /var/run/cups/cups.sock
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseRemoteProtocols CUPS dnssd
BrowseLocalProtocols
DefaultAuthType Basic
WebInterface Yes
<Location />
  Order allow,deny
</Location>
<Location /admin>
  Order allow,deny
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>
<Policy default>
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
<Policy authenticated>
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Default
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

```

/etc/cups/cups-files.conf
```

SystemGroup lpadmin
AccessLog /var/log/cups/access_log
ErrorLog /var/log/cups/error_log
PageLog /var/log/cups/page_log

```


For reference, the /etc/cups/cups-files.conf containing comments is attached.

---

