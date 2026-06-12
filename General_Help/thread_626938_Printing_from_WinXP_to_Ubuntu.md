---
title: "Printing from WinXP to Ubuntu"
date: 2007-11-29
forum: General Help
---

### Post by bruban on 2007-11-29
Can someone point me in the right direction please?

I'm trying to share a printer on an Ubuntu 7.10 PC with WinXP users.

I appear to be having user authentication problems when I attempt to connect to the printer from WinXP.


I've followed the instructions at:

[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)


I've found the following:

[LIST]
[*]WinXP can see the printer when attempting to connect using http://<hostname>:631/printers/<printername>
[*]WinXP cannot finish setting up the printer as it needs an authenticated user
[*]I have tried a number of valid users on the Ubunutu PC
[*]My PC sees the requests on port 631. Each connection attempt is logged in the error log at /var/log/cups/error_log
[/LIST]

The error that I get in the cups error log is:

> D [30/Nov/2007:08:15:55 +1100] cupsdAcceptClient: 9 from 172.16.3.3:631 (IPv4)
D [30/Nov/2007:08:15:55 +1100] cupsdReadClient: 9 POST /printers/Photosmart_3100_series HTTP/1.1
D [30/Nov/2007:08:15:55 +1100] cupsdAuthorize: No authentication data provided.
D [30/Nov/2007:08:15:55 +1100] cupsdSendError: 9 code=403 (Forbidden)
D [30/Nov/2007:08:15:55 +1100] cupsdCloseClient: 9

The WinXP box is on a separate subnet to the Ubuntu box.

There is a firewall on the gateway in between.

Any ideas?

---

