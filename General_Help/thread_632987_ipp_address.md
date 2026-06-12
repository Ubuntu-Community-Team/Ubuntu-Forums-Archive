---
title: "ipp address"
date: 2007-12-06
forum: General Help
---

### Post by honiball on 2007-12-06
I have my printer working off a usb port (Manufacturer = Kyocera; Model = FS-1000).  I want to print to the exact same printer over the network. It's IP address is 192.168.10.115.  

I can add it in the CUPS web interface ([http://localhost:631](http://localhost:631)) but don't know what URI line to use.  

I assume it will be something like ipp://192.168.10.115, but that didn't work.  

Any help with the ipp URI will be appreciated.

---

### Post by honiball on 2007-12-06
Oh yes, this might help as well:  its URI as a USB printer is

usb://Kyocera/FS-1118MFP

---

### Post by daengbo on 2007-12-06
Is the second printer using CUPS, as well? Is it set to share from the second computer?

If these are true, then System -> Administration -> Printing should show it on your netowrk. Just click on it there.

---

### Post by honiball on 2007-12-06
I want to create it as a second (IP network) printer with my PC as the print server.  My problem is I don't know what ipp URI to use, or in what format it must be for this printer.

Thanks, Andrew.

---

