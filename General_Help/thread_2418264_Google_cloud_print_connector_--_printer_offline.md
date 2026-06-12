---
title: "Google cloud print connector -- printer offline"
date: 2019-05-04
forum: General Help
---

### Post by ski-brimson on 2019-05-04
The printer works from cups.

I have tried chrome://devices and click manage.  This doesn't do anything.

I used it for a long time in gentoo.

Now on the google web site reports the printer as off line:

[https://www.google.com/cloudprint#printers](https://www.google.com/cloudprint#printers)

I re-did the initialization steps, and google said it was connected, but the printer is still offline.

I see the following in the log:
```

I [04/May/2019:10:34:31 -0500] Using config file /home/klugja/gcp-cups-connector.config.json
I [04/May/2019:10:34:31 -0500] Google Cloud Print Connector for CUPS version DEV-linux
I [04/May/2019:10:34:32 -0500] Connecting to CUPS server at /run/cups/cups.sock:631 encrypting IF REQUESTED
I [04/May/2019:10:34:32 -0500] Connected to CUPS server successfully
I [04/May/2019:10:34:32 -0500] Local printing enabled (Avahi client is running).
I [04/May/2019:10:34:32 -0500] Synchronizing printers, stand by
I [04/May/2019:10:34:33 -0500] [Printer Phaser6500 aa7866b2-724a-bbce-40de-12dc35adbc62] Updated in the cloud
I [04/May/2019:10:34:33 -0500] Finished synchronizing 1 printers
I [04/May/2019:10:34:33 -0500] [Printer Phaser6500] Registered locally
I [04/May/2019:10:34:33 -0500] Ready to rock as proxy 'a48185cb-13d7-4b44-9361-8ed1706a409f' and in local mode
I [04/May/2019:10:35:29 -0500] Shutting down
I [04/May/2019:10:35:29 -0500] XMPP connection was closed
```

And the browser/manage reports the following (is unknown below a problem?):
```

Owned by me
Last print job was 47 minutes ago
Location not available
Printer is offline
Printer Type
Cloud Ready Printer
Registered with Cloud Print
Mar 2, 2019, 2:06:50 PM
Last Updated
May 4, 2019, 10:18:22 AM
Printer ID
3366e01c-2f51-40e0-b23d-d89bd7ad5915
Google Cloud Print Version
1.0
Supported Content Types
application/pdf
Proxy
2b9dc3b9-b437-49a7-b95e-8c34706d4e24
Tags
^own
^can_share
^can_update
^can_delete
__cp_printer_passes_2018_cert__ UNKNOWN
```

---

