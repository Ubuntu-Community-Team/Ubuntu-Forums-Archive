---
title: "root user cannot add printer through cups web interfce"
date: 2015-05-26
forum: General Help
---

### Post by sven19 on 2015-05-26
Hello:
I am running Ubuntu 14.04 LTS and I am attempting to add a locally attached printer via the cups web interface. 
I am accessing the cups web interface via a firefox browser session where the browser is running on the same system I am trying to add the printer to but the browser is displayed across the network.

I can bring up the cups web interface by accessing [http://localhost:631/admin](http://localhost:631/admin) and I can click on the add printer button. I am not prompted for any sort of authentication at this point.
It seems to have identified the printer attached locally to the parallel port as it correctly list the type of printer (HP LaserJet 1100 LPT #1 (HP LaserJet 1100))
and I can select the selector next to that option and click Continue down at the bottom of the page. I then get a page that lets me specify a Name, Description, Location, Connection and etc. I then click on another Continue button at the bottom of the page. I then get a page that lets me select a printer model or provide a PPD file. If I just select one of the appropriate filters there and select "Add Printer" at the bottom of the page, a dialog window appears where I have to specify a Username and a Password. I have tried repeatably putting in the system's root account and password for root (Yes, I definitely have one set and it works elsewhere) but each time all that happens if the same dialog window keeps popping up again.

I have turned on a debug level of 2 in the cupsd.conf file and I see the following in the error_log

d [26/May/2015:00:31:24 -0400] [Client 16] con->uri="/admin/", con->best=0x7f8a440b9e50(/)
d [26/May/2015:00:31:24 -0400] [Client 16] Authorization="Local 00C3EB765FB65167845F372D6FCE51A5"
d [26/May/2015:00:31:24 -0400] cupsdFindCert(certificate=00C3EB765FB65167845F372D6FCE51A5)
d [26/May/2015:00:31:24 -0400] cupsdFindCert: Certificate not found!
E [26/May/2015:00:31:24 -0400] [Client 16] Local authentication certificate not found.
d [26/May/2015:00:31:24 -0400] cupsdIsAuthorized: con->uri="/admin/", con->best=0x7f8a440b9e50(/)
d [26/May/2015:00:31:24 -0400] cupsdIsAuthorized: level=CUPSD_AUTH_ANON, type=None, satisfy=CUPSD_AUTH_SATISFY_ALL, num_names=0
d [26/May/2015:00:31:24 -0400] cupsdIsAuthorized: auth=CUPSD_AUTH_ALLOW...
D [26/May/2015:00:31:24 -0400] [Client 16] 2.0 CUPS-Add-Modify-Printer 1
d [26/May/2015:00:31:24 -0400] cupsdProcessIPPRequest(0x7f8a440f23a0[16]): operation_id = 4003
D [26/May/2015:00:31:24 -0400] CUPS-Add-Modify-Printer ipp://localhost/printers/HP_LaserJet_1100
d [26/May/2015:00:31:24 -0400] add_printer(0x7f8a440f23a0[16], ipp://localhost/printers/HP_LaserJet_1100)
d [26/May/2015:00:31:24 -0400] cupsdFindPolicyOp(p=0x7f8a440b6a10, op=4003(CUPS-Add-Modify-Printer))
d [26/May/2015:00:31:24 -0400] cupsdFindPolicyOp: Found exact match...
d [26/May/2015:00:21:35 -0400] cupsdIsAuthorized: con->uri="/admin/", con->best=0x7f0e17c7e2e0((null))
d [26/May/2015:00:21:35 -0400] cupsdIsAuthorized: level=CUPSD_AUTH_USER, type=Basic, satisfy=CUPSD_AUTH_SATISFY_ALL, num_names=1
d [26/May/2015:00:21:35 -0400] cupsdIsAuthorized: op=4003(CUPS-Add-Modify-Printer)
d [26/May/2015:00:21:35 -0400] cupsdIsAuthorized: auth=CUPSD_AUTH_ALLOW...
D [26/May/2015:00:21:35 -0400] cupsdIsAuthorized: username=""
D [26/May/2015:00:21:35 -0400] [Client 16] Returning HTTP Unauthorized for CUPS-Add-Modify-Printer (ipp://localhost/printers/HP_LaserJet_1100) from localhost
d [26/May/2015:00:21:35 -0400] [Client 16] cupsdSendError code=401, auth_type=0
D [26/May/2015:00:21:35 -0400] [Client 16] WWW-Authenticate: Basic realm="CUPS", trc="y"

I after trying to enter my root account creds several times as well as a local user account I finally end up clicking on a Cancel button in the dialog window and then I get an Unauthorized page.

Why is root not able to add a printer through the cups web interface and how can I solve this???

Any help or suggestions much appreciated.

---

