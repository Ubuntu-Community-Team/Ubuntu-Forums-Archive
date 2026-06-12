---
title: "tsp"
date: 2008-05-15
forum: General Help
---

### Post by ts_patil on 2008-05-15
I am a new user. I have Windown on one partition and Ubuntu on another. I have installed the VirtuslBox 1.6 on Ubuntu. I want to open the Windows from the existing partition.

Please any one help me.

I have created the virtal disk file and when I am trying to adding the virtual disk, I am getting the following error


VD: error opening image file '/home/user/.VirtualBox/Win.vmdk' (VERR_ACCESS_DENIED).


Result Code: 
0x80004005
Component: 
HardDisk
Interface: 
IHardDisk {fd443ec1-000f-4f5b-9282-d72760a66916}
Callee: 
IVirtualBox {2d3b9ea7-25f5-4f07-a8e1-7dd7e0dcf667}

---

### Post by ibuclaw on 2008-05-15
Install a fresh copy of Windows onto your Virtual Drive. You can't boot from real hard-drives in VirtualBox.

Regards
Iain

---

