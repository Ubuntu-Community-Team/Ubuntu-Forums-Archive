---
title: "cups server error in Ubuntu 15.04 after upgrade"
date: 2015-05-15
forum: General Help
---

### Post by sabinedoll on 2015-05-15
My Epson printer is not working any more after upgrade. Printer not detected. Supposedly CUPS is running, but cannot detect. Printer icon has everything greyed out. 

Listen /var/run/cups/cups.sock
Listen /var/run/cups/cups.sock
Browsing Off
BrowseLocalProtocols dnssd
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
JobPrivateAccess default
JobPrivateValues default
SubscriptionPrivateAccess default


I cannot find the following: There is supposed to be a line in the code, that allows the pritner to be connected to a port.

I appreciate help fixing the problem, as the printer is badly needed.

---

### Post by ian-weisser on 2015-05-18
Test if CUPS is running. Click on this link: [http://localhost:631](http://localhost:631)

What is the result? A CUPS web page? Or an 'unable to connect' error?

---

### Post by sabinedoll on 2015-05-20
It tells me, that it is unable to connect. But when I check the system processes, then CUPS is supposedly running.
I appreciate your help. Is there anything I can do?

---

### Post by sabinedoll on 2015-05-20
It tells me, that it is unable to connect. But when I check the system processes, then CUPS is supposedly running.
I appreciate your help. Is there anything I can do?

---

### Post by ian-weisser on 2015-05-20
> **sabinedoll said:**
> It tells me, that it is unable to connect. But when I check the system processes, then CUPS is supposedly running.
I appreciate your help. Is there anything I can do?

If your web browser cannot connect to [http://localhost:631](http://localhost:631) , then CUPS is definitely not running.
Restart CUPS using the following command and try connecting again.
```
sudo service cups restart
```

If you get any error messages, copy-and-paste the entire output here.

If it still doesn't work, please attach the file /var/log/cups/error.log here.

---

### Post by sabinedoll on 2015-05-23
There was no error message in the Terminal, but still did not connect.

Here is the log (s):

W [22/May/2015:07:12:47 -0700] Duplicate listen address "/var/run/cups/cups.sock" ignored.
E [22/May/2015:07:12:47 -0700] Unknown directive JobPrivateAccess on line 83 of /etc/cups/cupsd.conf.
E [22/May/2015:07:12:47 -0700] Unknown directive JobPrivateValues on line 84 of /etc/cups/cupsd.conf.
E [22/May/2015:07:12:47 -0700] Unknown directive SubscriptionPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [22/May/2015:07:12:47 -0700] Unknown directive SubscriptionPrivateValues on line 86 of /etc/cups/cupsd.conf.
W [22/May/2015:21:10:56 -0700] Duplicate listen address "/var/run/cups/cups.sock" ignored.
E [22/May/2015:21:10:56 -0700] Unknown directive JobPrivateAccess on line 83 of /etc/cups/cupsd.conf.
E [22/May/2015:21:10:56 -0700] Unknown directive JobPrivateValues on line 84 of /etc/cups/cupsd.conf.
E [22/May/2015:21:10:56 -0700] Unknown directive SubscriptionPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [22/May/2015:21:10:56 -0700] Unknown directive SubscriptionPrivateValues on line 86 of /etc/cups/cupsd.conf.
W [22/May/2015:21:11:13 -0700] Duplicate listen address "/var/run/cups/cups.sock" ignored.
E [22/May/2015:21:11:13 -0700] Unknown directive JobPrivateAccess on line 83 of /etc/cups/cupsd.conf.
E [22/May/2015:21:11:13 -0700] Unknown directive JobPrivateValues on line 84 of /etc/cups/cupsd.conf.
E [22/May/2015:21:11:13 -0700] Unknown directive SubscriptionPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [22/May/2015:21:11:13 -0700] Unknown directive SubscriptionPrivateValues on line 86 of /etc/cups/cupsd.conf.

W [21/May/2015:07:47:27 -0700] Duplicate listen address "/var/run/cups/cups.sock" ignored.
E [21/May/2015:07:47:27 -0700] Unknown directive JobPrivateAccess on line 83 of /etc/cups/cupsd.conf.
E [21/May/2015:07:47:27 -0700] Unknown directive JobPrivateValues on line 84 of /etc/cups/cupsd.conf.
E [21/May/2015:07:47:27 -0700] Unknown directive SubscriptionPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [21/May/2015:07:47:27 -0700] Unknown directive SubscriptionPrivateValues on line 86 of /etc/cups/cupsd.conf.

W [13/May/2015:07:41:21 -0700] Duplicate listen address "/var/run/cups/cups.sock" ignored.
E [13/May/2015:07:41:21 -0700] Unknown directive JobPrivateAccess on line 83 of /etc/cups/cupsd.conf.
E [13/May/2015:07:41:21 -0700] Unknown directive JobPrivateValues on line 84 of /etc/cups/cupsd.conf.
E [13/May/2015:07:41:21 -0700] Unknown directive SubscriptionPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [13/May/2015:07:41:21 -0700] Unknown directive SubscriptionPrivateValues on line 86 of /etc/cups/cupsd.conf.

There are a lot of error logs with, it seems to me, similar text. 

Thank you for your help.

---

### Post by ian-weisser on 2015-05-23
Problem 1:
> **sabinedoll said:**
> W [22/May/2015:07:12:47 -0700] Duplicate listen address "/var/run/cups/cups.sock" ignored.

Here's the relevant section of the etc/cups/cupsd.conf that you posted.

> **sabinedoll said:**
> [COLOR=#ff0000][B]Listen /var/run/cups/cups.sock
Listen /var/run/cups/cups.sock[/B][/COLOR]
Browsing Off
BrowseLocalProtocols dnssd
DefaultAuthType Basic
WebInterface Yes

As you can see, the warning says 'Hey, you wrote this twice.'
Interestingly, you also seem not listening on port 631.

Here's what mine looks like, for comparison:

```
**Listen localhost:631**
Listen /var/run/cups/cups.sock
Browsing Off
BrowseLocalProtocols dnssd
DefaultAuthType Basic
WebInterface Yes

```




Problem 2:
> **sabinedoll said:**
>  E [22/May/2015:07:12:47 -0700] Unknown directive JobPrivateAccess on line 83 of /etc/cups/cupsd.conf.
E [22/May/2015:07:12:47 -0700] Unknown directive JobPrivateValues on line 84 of /etc/cups/cupsd.conf.
E [22/May/2015:07:12:47 -0700] Unknown directive SubscriptionPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [22/May/2015:07:12:47 -0700] Unknown directive SubscriptionPrivateValues on line 86 of /etc/cups/cupsd.conf.


These cryptic errors usually just mean that lines 83-86 are policy statements, but are outside a <policy> section.

And, indeed, here's what you have:
> **sabinedoll said:**
> 
</Policy>
JobPrivateAccess default
JobPrivateValues default
SubscriptionPrivateAccess default

(One imagines line 86 was omitted from your cut-and paste.)
Easy fix: Move the </Policy> tag to after those lines (around line 87)


After these fixes, you should restart cups (Post #5 in this thread) to reload the updated config.

---

### Post by sabinedoll on 2015-05-25
Thank you for your help. I got it running again. I would like to mention, that I did not mess with the CUPS file. It happened after/during the upgrade from Ubuntu 14.10 to 15.04. I am not a programmer, so I do not know why this happened and how this could happen. Glad it is fixed!

---

