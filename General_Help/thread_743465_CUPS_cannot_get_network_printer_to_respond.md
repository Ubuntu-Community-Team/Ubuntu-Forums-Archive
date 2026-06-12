---
title: "CUPS cannot get network printer to respond"
date: 2008-04-02
forum: General Help
---

### Post by magicgeorge on 2008-04-02
I've been trying to connect to a network printer but cannot get it to respond.  The Gnome printer panel shows a Phaser-6180 with a ready status.  When I send a test page, the panel changes to show Job Printing.

The printer's own web-based interface shows No jobs.  Looking at the localhost:631/printers/ panel shows Network host "192.168.1.111" is busy; will try in 30 seconds.

Other information:  I can ping the printer at its IP address.  The printer is a freestanding network printer not attached to any PC or server.  The Windows clients all access it directly by IP address only.

After searching other CUPS threads I've added cupsys as a user in group lpadmin. That didn't seem to help.

A partial listing of the cups error_log follows:

D [02/Apr/2008:16:12:42 -0500] CUPS-Get-Printers
D [02/Apr/2008:16:12:42 -0500] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [02/Apr/2008:16:12:42 -0500] cupsdReadClient: 11 POST / HTTP/1.1
D [02/Apr/2008:16:12:42 -0500] cupsdAuthorize: No authentication data provided.
D [02/Apr/2008:16:12:42 -0500] Get-Printer-Attributes ipp://localhost/printers/Phaser-6180N
D [02/Apr/2008:16:12:42 -0500] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [02/Apr/2008:16:12:43 -0500] cupsdReadClient: 12 POST / HTTP/1.1
D [02/Apr/2008:16:12:43 -0500] cupsdAuthorize: No authentication data provided.
D [02/Apr/2008:16:12:43 -0500] CUPS-Get-Printers
D [02/Apr/2008:16:12:43 -0500] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
I [02/Apr/2008:16:12:45 -0500] Scheduler shutting down normally.
D [02/Apr/2008:16:12:45 -0500] cupsdCloseClient: 11
D [02/Apr/2008:16:12:45 -0500] cupsdCloseClient: 12
D [02/Apr/2008:16:12:45 -0500] cupsdCloseClient: 9
I [02/Apr/2008:16:12:45 -0500] Saving remote.cache...
I [02/Apr/2008:16:12:45 -0500] Saving job cache file "/var/cache/cups/job.cache"...
E [02/Apr/2008:16:12:50 -0500] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2008:16:12:50 -0500] cupsdAuthorize: Local authentication certificate not found!


I also tried commenting-out the authorization line in cupsd.conf as follows:

# Default authentication type, when authentication is required...
#DefaultAuthType Basic

This didn't seem to have any effect.One thing puzzling me is that I see error messages saying I am not authorized to add a printer, but the printer shows up as expected.  Have tried creating the printer numerous times and always restarted cupsys between changes.

Any suggestions based on the log file??

---

### Post by warp99 on 2008-04-02
Are you printing directly to the printer or using a print server? You could set up the printers as a AppSocket/HP JetDirect using port 9100. So the address CUPS would send the file is socket://192.168.1.111:9100 

This is the only way I can get both of my print servers to receive files.

Edit:

Duh, I read your post again. The network is connected directly to the printer. I checked and there is no Direct (port 9100) support for that printer, so ignore my post.

---

### Post by Ironica on 2008-06-09
magicgeorge, did you ever resolve this issue?  I'm considering purchasing this printer, but haven't found any other references to installing it under Ubuntu.  I'd love to know if you've had success!

---

### Post by halitech on 2008-07-03
The printer does indeed work using the AppSocket connection.

download the CUPS Printer package from here

[http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=6180&Family=Phaser&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=](http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=6180&Family=Phaser&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=)

and extract.

Then go to System - Administration - Printing and add a printer. For the connection, select AppSocket/HP JetDirect. Leave the port on 9100 and add the IP address of the printer. Then Select Provide PPD file and browse to where you extracted the files and select the model you have. Then select any additional options you have like extra ram, trays and a hard drive. Give it a name and finish. You should then be up and running.

---

