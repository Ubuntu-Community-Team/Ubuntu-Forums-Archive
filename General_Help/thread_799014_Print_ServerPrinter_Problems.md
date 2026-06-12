---
title: "Print Server/Printer Problems"
date: 2008-05-18
forum: General Help
---

### Post by BetaMaster on 2008-05-18
Hi,
I've been having trouble setting up my printer on Ubuntu Hardy Heron. My printer is an HP Deskjet 1220c, connected to the network through a Linksys PSUS4 wired print server. I set up the printer like so:

1. System > Administration > Printing > New Printer > Other
2. Device URI: ipp://192.168.2.200 (static IP I assigned the print server)
3. HP > Deskjet 1220c > Foomatic/hpijs [en] (recommended)
4. Apply

Upon initially doing this, I printed a test page, and it printed fine. When I went to print something else, it didn't print. I tried another test page, and again, it wouldn't print. I tried restarting (just in case), and deleting/readding the printer. Nothing.

Someone please help? What should I do?

---

### Post by mike2357 on 2008-05-18
I don't know the answer, but here are some things to try:

1.  First, I'd try connecting the printer directly to your Ubuntu computer.  If you can successfully print, that I would suspect some sort of network issue.  If you cannot successfully print, I'd try different printer drivers.

2.  Assuming you could print via the direct connection and you are now troubleshooting network issues, I'd make sure there are no firewall issues that might be involved.  There may be an IP address and/or port that may need to be unblocked.  Also, assuming your router has a web interface, I'd verify that the print server has the IP address you think it has.  You may need samba (I'm not sure about this).  If so, I'd look at your samba settings.

3.  You said that you first were able to print a test page.  Did you change anything shortly afterwards, such as a firewall setting?

Sorry I can't be of more help, but these are some things to try.  Good luck!

---

### Post by BetaMaster on 2008-05-18
Thanks for your reply.

1. Hooking the printer directly up is not an option, other computers on the network use it and it's two floors downstairs.

2. It does have a web interface, and I can connect to it,and there are no port issues (the printer port is open).

3. I didn't change any settings after the successful test print, which makes all of this all the more frustrating.

Any more questions or suggestions, let me know..I'm at a loss for this right now though.:confused:

---

### Post by hencke on 2008-05-26
> **BetaMaster said:**
> Hi,
I've been having trouble setting up my printer on Ubuntu Hardy Heron. My printer is an HP Deskjet 1220c, connected to the network through a Linksys PSUS4 wired print server. I set up the printer like so:

1. System > Administration > Printing > New Printer > Other
2. Device URI: ipp://192.168.2.200 (static IP I assigned the print server)
3. HP > Deskjet 1220c > Foomatic/hpijs [en] (recommended)
4. Apply

Upon initially doing this, I printed a test page, and it printed fine. When I went to print something else, it didn't print. I tried another test page, and again, it wouldn't print. I tried restarting (just in case), and deleting/readding the printer. Nothing.

Someone please help? What should I do?

Hi BetaMaster!

I originally searched the forums because I couldn't find the HP > Deskjet 1220c driver. Anyway, I got my printer installed after a bit of trouble. So I also have a HP DeskJet 1220C in my network, connected to a HP JetDirect print server. To install it I did this:

1. System > Administration > Printing > New Printer > AppSocket/HP JetDirect
2.1. Host 192.168.x.y
2.2. Port number: 9100 (that was the default)
3.1. HP > DeskJet 1200C > Foomatic/hpijs [en] (recommended) > Oops, wrong driver > 1220C isn't in the list > Back
3.2. Provide PPD file > Browse to the PPD file that I downloaded from (A)
4. Apply

(A) [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_1220C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_1220C)

So you use Hardy Heron and did find the right driver in the list? I seem to have the printer working now with 2 different Device URIs:

a) socket://192.168.x.y:9100
b) hp:/net/DESKJET_1220C?ip=192.168.x.y

They might be worth trying, although you do have a different print server.

---

### Post by Andy17MB on 2008-06-09
Hi,

I'm looking into a similar problem, but I am getting it with completely different Hardware..

I've got a samsung ML-1510 laser Printer and An Epson R800 Inkjet connected to a 3205uw print server.  The connection is over wired ethernet and a Windows PC also uses these printers.  The windows PC works faultlessly.  

I have configured the Printers through cups ([http://localhost:631](http://localhost:631)).  Both printers have the correct drivers and are being addressed correctly via IPP.  I can get an initial test print off each and then that's it.  The cups screen shows no active jobs but the status of both printers as "waiting for active job to complete".  In Gutsy cancelling the job cleared this.  It does not appear to do so in Hardy.

I've used Firestarter to allow incoming traffic from the Edimax Printserver, so I don't think it's a firewall problem.

Digging a bit deeper I had a look at /var/log/cups/error_log and found:
```
E [02/Jun/2008:08:22:12 +0100] [CGI] Unable to send 46 bytes to 192.168.0.255: Operation not permitted
E [09/Jun/2008:08:10:26 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [09/Jun/2008:08:10:48 +0100] cupsdAuthorize: pam_authenticate() returned 10 (User not known to the underlying authentication module)!
E [09/Jun/2008:08:10:48 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [09/Jun/2008:08:12:24 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [09/Jun/2008:08:13:18 +0100] [Job 1] Destination printer does not exist!
E [09/Jun/2008:08:13:18 +0100] PID 21074 (/usr/lib/cups/backend/ipp) stopped with status 4!
E [09/Jun/2008:08:16:29 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [09/Jun/2008:08:17:41 +0100] Purge-Jobs: Unauthorized
E [09/Jun/2008:08:20:02 +0100] CUPS-Add-Modify-Printer: Unauthorized

```

It looks like some sort of permissions problem but I can't figure out what as yet.  I suspect it's in CUPS, but I'm not clear what.  I've tried setting the CUPS Server to allow any user to cancel jobs, but that has not worked

That's where I'm at - I'm not sure that it gets us nany further on, but hopefully provides something useful that someone else can spot the problem in

Andy

---

### Post by rem8114 on 2008-09-07
I am having the same issue with a Hawking print server.  After going through the not printing at all scenario ([http://ubuntuforums.org/showthread.php?t=787166](http://ubuntuforums.org/showthread.php?t=787166)) I got it to print but now it is leaving the printed job in the queue as described.  Canceling doesn't clear the waiting status.  The only way I found is to stop and start the printer.  Has anyone solved this?

Ron

NOTE: Solved this by putting ?waitjob=false after URI.

---

### Post by mpentney on 2008-09-24
I'm having the same problem. My Ubuntu system has a wired ethernet connection to an Edimax 1203 printer server linked to an HP Laserjet4000. I've set up the printer using AppSocket (and the correct IP address for the printserver), and I can print ONE document. After that, the queue hangs and I have to reboot/switch off to re-initialize it.

I switched to Ubuntu from Windows about 6 weeks ago - but this issue is really driving me nuts! (Sad to say, this is one area where Windows beats Ubuntu...)

Can anybody suggest a hack that will allow me to print more than one document without having to reboot?

Thanks,

Mike.

NOTE: fixed this problem by adding the following line to /etc/sysctl.conf:

net.ipv4.tcp_frto = 0

See thread 787166 on this forum...

---

