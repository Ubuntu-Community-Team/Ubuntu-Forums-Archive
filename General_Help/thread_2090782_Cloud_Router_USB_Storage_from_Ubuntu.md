---
title: "Cloud Router USB Storage from Ubuntu"
date: 2012-12-03
forum: General Help
---

### Post by bkfitz on 2012-12-03
Looks like Cisco/Linksys and DLink (and maybe others) now offer wireless N routers with the ability to plug in external storage and access it not just from your living room, but from anywhere in the form of cloud storage.  Anyone have any experience with these devices and how access to the 'cloud' storage works from Linux?

I'm looking at D-Link's Cloud Router 1200 with 'myDLink' and/or the Linksys EA6500 Smart Router:

[http://homestore.cisco.com/en-us/Routers/Linksys-EA6500-App-Enabled-AC-Dual-Band-Wireless-Router-with-http://homestore.cisco.com/en-us/Routers/Linksys-EA6500-App-Enabled-AC-Dual-Band-Wireless-Router-with-Gigabit_stcVVproductId148919965VVviewprod.htm](http://homestore.cisco.com/en-us/Routers/Linksys-EA6500-App-Enabled-AC-Dual-Band-Wireless-Router-with-http://homestore.cisco.com/en-us/Routers/Linksys-EA6500-App-Enabled-AC-Dual-Band-Wireless-Router-with-Gigabit_stcVVproductId148919965VVviewprod.htm)

[http://www.dlink.com.au/mydlink/cloud-storage.html](http://www.dlink.com.au/mydlink/cloud-storage.html)

Thx!

---

### Post by bkfitz on 2012-12-03
Talked to DLink support and it sounds like from a laptop or desktop machine, you can only access the shared storage via a web-browser, not as a shared folder like Dropbox does with /home/Dropbox...

However, on Android and IOS, there is an app called "SharePort" that allows you to access the shared space as if it is local storage... to play movies remotely, play music remotely, open documents, save documents etc.

So.... if Android and IOS can do it, then why can't it be done on a laptop/desktop... they must be using CIFS/SMB or NFS yes???

---

### Post by bkfitz on 2012-12-03
Linksys Smart Wi-Fi routers forum post seems to indicate access via browser or FTP only:

[http://homecommunity.cisco.com/t5/Facebook-Support/Cisco-Connect-Cloud-External-Storage-Support/td-p/565976](http://homecommunity.cisco.com/t5/Facebook-Support/Cisco-Connect-Cloud-External-Storage-Support/td-p/565976)

So I guess I could mount the FTP site as a local folder using CurlFTPfs like this:

[http://www.ubuntugeek.com/how-to-mount-ftp-folder-to-local-directory-in-ubuntu.html](http://www.ubuntugeek.com/how-to-mount-ftp-folder-to-local-directory-in-ubuntu.html)

???

---

### Post by bkfitz on 2012-12-04
Anyone?

---

### Post by venik212 on 2013-01-31
I have a Netgear N900 wireless router, which I bought because it has 2 USB ports, and their adertisement said it could be used to create a private cloud.  However, once I got it, I discovered that they support only Windows & Macs, but not Linux...

---

