---
title: "Printing via Print Server"
date: 2020-02-04
forum: General Help
---

### Post by 90buntu on 2020-02-04
Hi,

I would like Linux Ubuntu to be able to print via Print Server.  I understand that you can print via #1. Windows Print Server or #2. Linux Print Server.  
Could anyone provide steps to achieve #1 or #2?  Any advice would be appreciated.

---

### Post by TheFu on 2020-02-04
Run ... **system-config-printer**, 
"add"
choose a *network printer*, 
Choices will be shown ... I always select the IPP entry with IPP protocol. The URI looks like this:
ipp://romulus:631/printers/Samsung_ML-1740

That's it.  

You can search for the network printer using the DNS name or IP.  Supported protocols should be returned.
IPP completely rocks.

---

### Post by 90buntu on 2020-02-06
Thanks for the update.  I assume the IPP protocol is for direct printing from Ubuntu computer to the printer, but what if I want to keep records of the print job at a centralized print server for these Ubuntu computers?

---

### Post by TheFu on 2020-02-06
> **90buntu said:**
> Thanks for the update.  I assume the IPP protocol is for direct printing from Ubuntu computer to the printer, but what if I want to keep records of the print job at a centralized print server for these Ubuntu computers?

wrong assumption.  Dude, try it.

---

