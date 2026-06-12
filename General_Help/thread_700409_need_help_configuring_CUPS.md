---
title: "need help configuring CUPS"
date: 2008-02-18
forum: General Help
---

### Post by akudewan on 2008-02-18
My father is using a Vista laptop, and he uses the printer quite often, which is connected to my Ubuntu desktop. I've set up CUPS, and it usually works. But every now and then, the printer just stops after printing one line. I have to start the printer manually, and then it resumes printing, after wasting that page.

This is possibly an authentication issue, from what I can tell from the error log:

```

I [18/Feb/2008:20:54:57 +0530] Listening to :::631 (IPv6)
I [18/Feb/2008:20:54:57 +0530] Listening to 0.0.0.0:631 (IPv4)
I [18/Feb/2008:20:54:57 +0530] Listening to /var/run/cups/cups.sock (Domain)
I [18/Feb/2008:20:54:57 +0530] Loaded configuration file "/etc/cups/cupsd.conf"
I [18/Feb/2008:20:54:57 +0530] Using default TempDir of /var/spool/cups/tmp...
I [18/Feb/2008:20:54:57 +0530] Configured for up to 100 clients.
I [18/Feb/2008:20:54:57 +0530] Allowing up to 100 client connections per host.
I [18/Feb/2008:20:54:57 +0530] Using policy "default" as the default!
I [18/Feb/2008:20:54:57 +0530] Full reload is required.
I [18/Feb/2008:20:54:57 +0530] Saving job cache file "/var/cache/cups/job.cache"...
I [18/Feb/2008:20:54:57 +0530] Loaded MIME database from '/usr/share/cups/mime:/etc/cups': 36 types, 40 filters...
I [18/Feb/2008:20:54:57 +0530] Loading job cache file "/var/cache/cups/job.cache"...
I [18/Feb/2008:20:54:57 +0530] Full reload complete.
E [18/Feb/2008:20:54:58 +0530] Unable to find IP address for server name "ranjandesk"!
I [18/Feb/2008:20:54:58 +0530] Listening to :::631 on fd 4...
I [18/Feb/2008:20:54:58 +0530] Listening to 0.0.0.0:631 on fd 10...
I [18/Feb/2008:20:54:58 +0530] Listening to /var/run/cups/cups.sock on fd 11...
I [18/Feb/2008:20:54:58 +0530] Resuming new connection processing...
I [18/Feb/2008:20:56:47 +0530] [Job 50] Adding start banner page "none".
I [18/Feb/2008:20:56:47 +0530] [Job 50] Adding job file of type application/octet-stream.
I [18/Feb/2008:20:56:47 +0530] [Job 50] Adding end banner page "none".
I [18/Feb/2008:20:56:47 +0530] [Job 50] Queued on "Deskjet_1280" by "ranjandewan".
I [18/Feb/2008:20:56:47 +0530] [Job 50] Started backend /usr/lib/cups/backend/hp (PID 6030)
[B]E [18/Feb/2008:20:56:49 +0530] Pause-Printer: Unauthorized
I [18/Feb/2008:20:56:49 +0530] Saving printers.conf...
I [18/Feb/2008:20:56:49 +0530] Printer "Deskjet_1280" stopped by "root".[/B]
I [18/Feb/2008:20:58:04 +0530] Started "/usr/lib/cups/cgi-bin/jobs.cgi" (pid=6128)
I [18/Feb/2008:20:58:15 +0530] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6136)
I [18/Feb/2008:20:58:19 +0530] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6137)
E [18/Feb/2008:20:58:19 +0530] Resume-Printer: Unauthorized
I [18/Feb/2008:20:58:24 +0530] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6138)
E [18/Feb/2008:20:58:24 +0530] Resume-Printer: Unauthorized
I [18/Feb/2008:20:58:24 +0530] Saving printers.conf...
I [18/Feb/2008:20:58:24 +0530] Printer "Deskjet_1280" started by "root".
I [18/Feb/2008:20:58:24 +0530] [Job 50] Started backend /usr/lib/cups/backend/hp (PID 6139)
I [18/Feb/2008:20:58:29 +0530] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6153)
I [18/Feb/2008:20:58:29 +0530] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6154)
I [18/Feb/2008:20:58:41 +0530] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6169)
I [18/Feb/2008:20:58:52 +0530] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6170)
I [18/Feb/2008:20:58:59 +0530] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6171)

```

Here is my /etc/cups/cupsd.conf
```

LogLevel info
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
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

```


Please help! This is driving me nuts!!

---

### Post by akudewan on 2008-02-19
*bump*

---

### Post by doug1212 on 2008-02-19
Hi,
I you will need to have samba server set  up for windows printing. Loads of good how-to's about.
[HTML]https://help.ubuntu.com/community/SettingUpSamba[/HTML] 
Doug.

---

### Post by akudewan on 2008-02-19
I already have samba running. The printer can be seen from the laptop, and it even starts printing, but then stops after printing a line.

Could this be a samba issue? I'm attaching my /etc/samba/smb.conf
```

# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2008/01/28 22:05:12

[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[printers]
        comment = All Printers
        path = /var/spool/samba
        printable = Yes

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[Deskjet_1280]
        path = /var/spool/samba
        read only = No
        guest ok = Yes
        printable = Yes
        printing = cups
        printer name = Deskjet_1280

```

---

### Post by doug1212 on 2008-02-19
Hi,

My samba server is a headless box and I cheat a bit and used webmin to do the config after configuring cups.
Here is my smb.conf:

```
[global]
	printer = Samsung_ML-2010_USB_1
	name resolve order = hosts wins bcast
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	announce version = 5.0
	username map = /etc/samba/smbusers
	null passwords = true
	passdb backend = tdbsam
	wins support = yes
	netbios name = ubuntuserver
	server string = 
	printing = CUPS
	workgroup = MSHOME
	syslog only = yes
	printcap name = CUPS
	security = user
	syslog = 1
    ; General server settings

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /mnt/300gb-drive/music
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    valid  users = doug
    writable = yes
    public = no
    create mask = 0660

```

Hope it helps.
Doug.

---

