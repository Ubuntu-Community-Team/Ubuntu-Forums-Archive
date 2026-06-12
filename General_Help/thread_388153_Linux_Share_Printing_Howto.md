---
title: "Linux Share Printing Howto??"
date: 2007-03-19
forum: General Help
---

### Post by CaptainHowdy on 2007-03-19
Hello all!

 I ve been searching ubuntu forums for a howto in linux sharing printers
but i found nothing that could help me. It seems that every single
page that i found does not work. I have a Hp LaserJet on an Ubuntu Dapper
server and i am trying to share it so that Linux and Windows machines could print
on it. I ve used samba and cups and everything but it seems that when a Windows
machine finds the printer, it cannot print because it displays a message "the printer
did not respond" and it is taking too long to find the printer, and finally it does not print. 

Anybody, any ideas? :confused: :confused: 

Regards.

---

### Post by alamba on 2007-03-19
It's pretty trivial once you have the printer setup on the ubuntu box. Post your samba config and I'll have a look see.

A

---

### Post by CaptainHowdy on 2007-03-29
Sorry about the late reply!

My smb.conf looks like:

[global]
netbios name = Downer


security = user
encrypt passwords = yes
smb passwd file = /etc/samba/smbpasswd
log file = /var/log/samba/%m.log
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
wins support = no
hostname lookups = yes
hosts equiv = /etc/hosts
hosts allow = All
hosts deny = None
interfaces = lo eth0
bind interfaces only = yes
guest ok = yes
browse list = yes
printcap name = cups
printing = cups
load printers = yes

[printers]
comment = All Printers
browseable = no
printable = yes
writable = no
public = yes
guest ok = yes
path = /var/spool/samba
printer admin = root

[hplaserjet1320] <--- The name I will be referring to my printer from now on
comment = HP LaserJet 1320
printable = yes
path = /var/spool/samba
public = yes
guest ok = yes
printer admin = root


[print$]
comment = Printer Drivers
path = /etc/samba/printer # this path holds the driver structure after cupsaddsmb command
guest ok = yes
browseable = yes
read only = yes
write list = root



I remember i found a website and i copied it from there.

---

### Post by defishguy on 2007-03-29
I followed this guide to share a Dell A920 printer connected via USB to Edgy over my home network.  This is the guide I followed that worked for me when others didn't. **oblig disclaimer:  Your Mileage May Vary**

[http://www.faqs.org/docs/Linux-mini/Debian-and-Windows-Shared-Printing.html](http://www.faqs.org/docs/Linux-mini/Debian-and-Windows-Shared-Printing.html)

Scroll on down to section 4 to get to the meat of SMB/Cifs and sharing printers with Windows.

Good Luck!  I hope it works out for you.

---

### Post by Fishsticks on 2007-04-01
That guide got me further than any guide so far.

Before, neither of my windows machines could see that my Ubuntu machine was sharing a printer.  Now, both of them can see that I have a printer shared, and both can connect to it, but any print jobs I send to it just seem to get lost.  (The Ubuntu machine that the printer is directly connected to can still print just fine.)

As the guide suggested, I ran the [FONT="Courier New"]tail -f /var/log/cups/error_log command[/FONT] with [FONT="Courier New"]LogLevel debug[/FONT] set, and then tried to print a text file from Windows.  All I got was this:

```
D [01/Apr/2007:15:20:32 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [01/Apr/2007:15:20:32 -0400] cupsdAuthorize: No authentication data provided.
D [01/Apr/2007:15:20:32 -0400] CUPS-Get-Printers
D [01/Apr/2007:15:20:32 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [01/Apr/2007:15:20:37 -0400] cupsdAcceptClient: 10 from localhost:631 (IPv4)
D [01/Apr/2007:15:20:37 -0400] cupsdReadClient: 10 POST / HTTP/1.1
D [01/Apr/2007:15:20:37 -0400] cupsdAuthorize: No authentication data provided.
D [01/Apr/2007:15:20:37 -0400] Get-Jobs ipp://localhost/printers/PhotoSmart-D7300
D [01/Apr/2007:15:20:37 -0400] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [01/Apr/2007:15:20:37 -0400] cupsdReadClient: 10 POST / HTTP/1.1
D [01/Apr/2007:15:20:37 -0400] cupsdAuthorize: No authentication data provided.
D [01/Apr/2007:15:20:37 -0400] Get-Printer-Attributes ipp://localhost/printers/PhotoSmart-D7300
D [01/Apr/2007:15:20:37 -0400] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [01/Apr/2007:15:20:37 -0400] cupsdCloseClient: 10
D [01/Apr/2007:15:20:37 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [01/Apr/2007:15:20:37 -0400] cupsdAuthorize: No authentication data provided.
D [01/Apr/2007:15:20:37 -0400] CUPS-Get-Printers
D [01/Apr/2007:15:20:37 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [01/Apr/2007:15:20:42 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [01/Apr/2007:15:20:42 -0400] cupsdAuthorize: No authentication data provided.
D [01/Apr/2007:15:20:42 -0400] CUPS-Get-Printers
D [01/Apr/2007:15:20:42 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [01/Apr/2007:15:20:47 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [01/Apr/2007:15:20:47 -0400] cupsdAuthorize: No authentication data provided.
D [01/Apr/2007:15:20:47 -0400] CUPS-Get-Printers
D [01/Apr/2007:15:20:47 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [01/Apr/2007:15:20:52 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [01/Apr/2007:15:20:52 -0400] cupsdAuthorize: No authentication data provided.
D [01/Apr/2007:15:20:52 -0400] CUPS-Get-Printers
D [01/Apr/2007:15:20:52 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [01/Apr/2007:15:20:57 -0400] cupsdNetIFUpdate: "lo" = localhost...
D [01/Apr/2007:15:20:57 -0400] cupsdNetIFUpdate: "eth0" = 192.168.1.50...
D [01/Apr/2007:15:20:57 -0400] cupsdNetIFUpdate: "lo" = localhost...
D [01/Apr/2007:15:20:57 -0400] cupsdNetIFUpdate: "eth0" = fe80::208:2ff:fe6b:6fc9%eth0...
D [01/Apr/2007:15:20:57 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [01/Apr/2007:15:20:57 -0400] cupsdAuthorize: No authentication data provided.
D [01/Apr/2007:15:20:57 -0400] CUPS-Get-Printers
D [01/Apr/2007:15:20:57 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [01/Apr/2007:15:21:02 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [01/Apr/2007:15:21:02 -0400] cupsdAuthorize: No authentication data provided.
D [01/Apr/2007:15:21:02 -0400] CUPS-Get-Printers
D [01/Apr/2007:15:21:02 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [01/Apr/2007:15:21:07 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [01/Apr/2007:15:21:07 -0400] cupsdAuthorize: No authentication data provided.
D [01/Apr/2007:15:21:07 -0400] CUPS-Get-Printers
D [01/Apr/2007:15:21:07 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
```

I'm new at this so I'm not entirely sure of the significance of this data.  I'm guessing that the [FONT="Courier New"]cupsdAuthorize: No authentication data provided.[/FONT] lines are my problem.  I'm not sure why that would make sense, though; the guide said that any computer on my local network should be able to connect.  Even if that were not the case, I already have Samba set up and working to share files from my Ubuntu machine to my Windows machines, so my Windows machines should already be authenticating themselves anyway, right?

---

