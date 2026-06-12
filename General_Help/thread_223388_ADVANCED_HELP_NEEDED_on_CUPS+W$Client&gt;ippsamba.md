---
title: "ADVANCED HELP NEEDED on CUPS+W$Client&gt;ipp/samba"
date: 2006-07-26
forum: General Help
---

### Post by 666 on 2006-07-26
Introduction:
I have a Dapper server for file and print services on a architecture office.
This is important because wen a work is finished plotters and printers print for days "non stop".
There are several printers and 2 plotters attached directly or remotly on Windows clients through
SAMBA (printers shares also samba+cups).

All works well, everyone prints and heavy work seems like nothing for the "little server".
But (there is always a but) names on queue are the old
"smbprn.00000000.Remote Downlevel Document" that windows clients generate on there
RAW print jobs. Raw jobs are needed because of quality control on drawings plotted, as PostScript
tends to add extra problems on hatch, and line expression that I cant deal with on the moment.
As you imagine on "plotting days" as I call them it gets "messy": "just send wrong job to printer, u cancel it?"
or "this is urgent and needs to be printed ahead!!!" OOPS... 
Forget login names as almost everyone uses the same basic one (doesn't matter why) but
the print job name is the needed gold.

PLAN B:
As this smbprn thing seems unresolvable I've passed to IPP.

IPP solves the name problem imidiatly and my money goes on this, but (it's never easy)
the windows client print spooler behaves strangely (w2k and xp).
Once set up the W$ queue connects with cups completly, it pauses the printer,
it even cancels all jobs in queue for that printer on the dapper server, except for one important thing:
once printed, the queue is incapable of showing the job displaying a "Failed to open, retrying".
All is normal on server.
Once the print job is gone (printed or canceled) the error status is also gone.
Is this an expected behavior or can I troubleshoot?

You coul'd say: "it works, why bother!?"
Th eproblem is that the spoolsv.exe on windows gets crazy and goes over the roof stalling everything,
even on printer install time.
I'm gessing a permissions thing, and I think that I've tried it all.
Nevertheless, I have duplicated (from fresh) the system at home and same thing happens.

To simplify I've cleaned and restored defaults on cupsd.conf, printers.conf, ports.conf, etc and I think
I just managed to remove all security there.
All its left is file permissions. I stell can't figure out wich user/group to set for CUPS as nothing seems to work.
"La piece de resistence" (192.168.0.10 is the W$ client):
192.168.0.10 - - [26/Jul/2006:09:25:18 +0100] "POST /printers/ESC1520 HTTP/1.1" 200 167 Get-Jobs successful-ok

FINALLY: 
At this point I don't much care wich one is the solution, but i really need one.
Even if there is a parallel solution for the spoolsv.exe problem I accept.
if anyone can give me a tip, I would really be happy
Thank you.

SETTINGS:
no firewall/iptables on server/clients
confirmed full/admin access to web interface on network

CUPSD.CONF
-------------------------------------
ServerName tvbera
# Show general information in error_log.
LogLevel info
SystemGroup lpadmin
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAllow 192.168.0.0/255.255.255.0
BrowseAddress @LOCAL
#BrowseAddress 192.168.0.255:631
BrowseAddress 255.255.255.255:631

DefaultAuthType Basic
<Location />
AuthType None
# Allow shared printing and remote administration...
Order allow,deny
Allow @LOCAL
</Location>
<Location /admin>
AuthType None
# Allow remote administration...
Order allow,deny
Allow @LOCAL
Allow 192.168.0.0/255.255.255.0
</Location>
<Location /admin/conf>
AuthType None
# Allow remote access to the configuration files...
Order allow,deny
Allow @LOCAL
Allow 192.168.0.0/255.255.255.0
</Location>
<Policy default>
<Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
AuthType None
Order deny,allow
Allow @LOCAL
Allow 192.168.0.0/255.255.255.0
</Limit>
<Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
AuthType None
Order deny,allow
Allow @LOCAL
Allow 192.168.0.0/255.255.255.0
</Limit>
<Limit CUPS-Authenticate-Job>
AuthType None
Order deny,allow
Allow @LOCAL
Allow 192.168.0.0/255.255.255.0
</Limit>
<Limit All>
Order deny,allow
</Limit>
</Policy>
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf
PreserveJobFiles True
# Allow remote access
Listen /var/run/cups/cups.sock

---

### Post by 666 on 2006-07-27
Some developments...

I've insstalled IIS on a Win2k to try to understand there ideia of IPP.
It works slow but it is functional.
They also accept the 4 types of authentication (none as the 4th). Apparently nothing much differs but there are 2 details to consider.

1) They use port 80 for interface.
2) They have a diferent url [http://server/printers/epson/.printer](http://server/printers/epson/.printer)

If u dont use the ".printer" finale no comunication is achieved.

I've tried port 80 with same results as for port 631, in fact they can't even be both on or black magic starts to happen (things like missing printers although in printers.conf file and all sort of things).

So I'm gessin a ".printer" link to fool windows... but I dont know where to put it so that I could get a similar URL...

---

