---
title: "How do I share a printer"
date: 2023-10-19
forum: General Help
---

### Post by Onesimus on 2023-10-19
I have done a fresh install of Ubuntu 23.10, but I don't seem to be able to share a Printer over my local network.
In Ubuntu 22.04 I would simply set the Printer to be shared in the Printer settings, but there doesn't seem to be an option to do that

Any help would be appreciated.

---

### Post by TheFu on 2023-10-19
[https://ubuntu.com/server/docs/service-cups](https://ubuntu.com/server/docs/service-cups) is the server method. 

I'd expect this can be done on desktops, but my 23.10 install isn't a print server, just a print client to my 20.04 print server. Sorry I'm not more help.  I use IPP everywhere - on the server-to-printer connection and for all clients to connect.  My network printers were magically found by 23.10 and setup for me (it seemed).  That's due to CUPS on the server advertising it over avahi.  In the system-config-printer tool, they are listed as "discovered".

---

### Post by Onesimus on 2023-10-19
So, a little bit more info.  I have installed the 23.10 Desktop installation (cups is already installed).
My computer has a USB printer attached to it, and I want to share it over my local network.

I'm looking for a GUI method rather than command-line option (it seems as if functionality has been removed)

---

### Post by Onesimus on 2023-10-20
I have worked out a solution by installing:  system-config-printer

This allowed my to share printers on my local network

---

### Post by TheFu on 2023-10-20
> **Onesimus said:**
> I have worked out a solution by installing:  **system-config-printer**

This allowed my to share printers on my local network

If this is solved, please use the thread tools button near the top of the page to mark it so. This helps the community.

---

### Post by layolayo on 2024-01-01
many thanks I needed this one today! - 23.10 looks to have dropped a few things

---

