---
title: "Share drive (external NAS)"
date: 2008-05-24
forum: General Help
---

### Post by ScottMartin on 2008-05-24
I am having problems with a new install of 8.04 recognizing a NAS drive using the share name. I can access the drive as follows:

*All XP machines (share name)
*Ubuntu box that had 7.10 installed and upgraded to 8.04 (share name)
*From the new 8.04 using the IP address ONLY

samba/smbfs are installed.

Places/Network/Windows Network/<Workgroup Names> appear, but I cannot see the drive when I click on the workgroup.

30 sec timeout, then NT_STATUS_ACCESS_DENIED error.

This all works fine from the 7.10->8.04 upgrade box.

I have:


*Updated smb.conf to match the workgroup info. 
*Updated the network config to a static IP and proper gateway.
*Rebooted the NAS, and new 8.04 box.
*Jumped on 1 leg while drinking a beer.

Is there something in the setup of a new install of 8.04 that would be casuing this problem? It acts like a firewall issue, but I do not have a software firewall on that install (I have an Untangle box)

I have read that it may have to do with problems using the new gvfs?

smbclient allows connection using the IP, not using the share name. I am able to create a mount drive, but I have to use the IP address and I would prefer to use the share name since a reboot of the NAS would break this link.

Related Note: Places/Network takes about 20 seconds to load nautilus when you first start it.

Any ideas?

U8.04
AMD-64

Regards,
Scott.

---

