---
title: "[SOLVED] Locked out of CUPS - 401 Unauthorized"
date: 2008-02-03
forum: General Help
---

### Post by akudewan on 2008-02-03
I have set up a print server on my Ubuntu desktop, so that I can print from my Vista laptop (which is on LAN). Setting this up was a bit of a pain, and after making some configuration changes from localhost:631, I finally got it to work.

I had to enable Kerberos authentication for the printer to work. Without it, the printer would just print one line and get stuck (the error log would say something like "authentication failed"). Everything was working fine until I realized that I'm locked out of CUPS. I can't make any changes to the server any more! It does not prompt me for any username and password. I simply get a page saying: 
```

401 Unauthorized

Enter your username and password or the root username and password to access this page. If you are using Kerberos authentication, make sure you have a valid Kerberos ticket.

```

So what do I do now? 

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
DefaultAuthType Negotiate
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

Help!!!

PS: I don't even know what Kerberos is...lol

---

### Post by jjalocha on 2008-02-03
Just for the CUPS part, I had to do the following in order to give a user (peter) the needed authorizations:

```

$ sudo lppasswd -a peter  # enter CUPS password for peter twice when prompted
$ sudo gpasswd -a peter lpadmin

```

If this doesn't work, and it is a kerberos problem, you will need someone else's help.

...hope this helps...

---

### Post by akudewan on 2008-02-04
> **jjalocha said:**
> Just for the CUPS part, I had to do the following in order to give a user (peter) the needed authorizations:

```

$ sudo lppasswd -a peter  # enter CUPS password for peter twice when prompted
$ sudo gpasswd -a peter lpadmin

```

If this doesn't work, and it is a kerberos problem, you will need someone else's help.

...hope this helps...

Nope, this didn't work. Thanks for replying though.

Any other suggestions ?

---

### Post by akudewan on 2008-02-07
Hmm...Maybe I'll just reinstall CUPS after purging the configuration files...

---

### Post by mickza on 2008-02-15
```
DefaultAuthType Negotiate
```
change to:
```
DefaultAuthType Basic
```
this turns off kerberos and lets you back in

---

### Post by akudewan on 2008-02-15
> **mickza said:**
> ```
DefaultAuthType Negotiate
```
change to:
```
DefaultAuthType Basic
```
this turns off kerberos and lets you back in

Thanks a million! I was hoping someone would come up with a solution, so I didn't reinstall CUPS.

The problem is solved, and printing over the network is also working fine :)

---

### Post by ddragas on 2008-02-22
> **akudewan said:**
> Thanks a million! I was hoping someone would come up with a solution, so I didn't reinstall CUPS.

The problem is solved, and printing over the network is also working fine :)

can you please write step by step how did you install printer on vista to be able to print to printer attached to ubuntu.

I'm having problems with this in last 7 days.

I have maneged to have those 2 OS in network to see each other (samba), but sharing printers is problem, I can print from ubuntu, and from other 2 XP pro, but can not instal printer to vista.

Please help me

Thank you in advanced

Kind regards

ddragas

---

### Post by akudewan on 2008-02-23
> **ddragas said:**
> can you please write step by step how did you install printer on vista to be able to print to printer attached to ubuntu.

I'm having problems with this in last 7 days.

I have maneged to have those 2 OS in network to see each other (samba), but sharing printers is problem, I can print from ubuntu, and from other 2 XP pro, but can not instal printer to vista.

Please help me

Thank you in advanced

Kind regards

ddragas

I don't quite remember the step-by-step detals. I simply added a new printer in Vista from the Control Panel. Instead of looking for the printer, I added the path manually (\\192.168.1.2\Deskjet_1280)

Vista was also complaining that the driver was incompatible. So I downloaded the driver separately and installed it in Vista.

---

### Post by dakkil on 2008-03-23
Thankyou micka you have solve my problem too, I think that when you ar configurating the printer with samba this parameter is automaticly changed, thats my case at least

---

