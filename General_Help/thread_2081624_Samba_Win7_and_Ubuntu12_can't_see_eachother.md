---
title: "Samba: Win7 and Ubuntu12 can't see eachother"
date: 2012-11-07
forum: General Help
---

### Post by sienile on 2012-11-07
I'm trying to configure samba to be able to share with Win7. After much tinkering I finally was able to get Ubuntu to be able to see its own shares, but it can't see the Win7 shares and Win7 can't see Ubuntu at all.

I've read a lot of old forum posts regarding this and have applied the following registry changes to Win7, but still I am not able to see Ubuntu.```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System
DWORD
EnableLinkedConnections
1

HKLM\SYSTEM\CurrentControlSet\Control\Lsa 
DWORD
LmCompatibilityLevel
2
```
On one occasion Win7 did momentarily see Ubuntu, but could not access anything or even see the names of the shares. That was immediately after I changed the shared folder's properties to enable simple file sharing (i.e.: not using the samba config app). But after rebooting Win7 (no settings changed), it was gone.

From the Ubuntu end, it might be simpler. When attempting to access the Win7 share, it asks for a password... but my Win7 share has no password. I'm pretty sure there's a samba setting to fix this, but I'm a total newb when it comes to samba, so I have no clue what to do.

---

### Post by sienile on 2012-11-08
I know there's got to be a samba guru around here somewhere. Please help!

---

### Post by sienile on 2012-11-20
Still need help. :confused:

---

### Post by Mark Phelps on 2012-11-20
Try walking through the steps in the linked thread to see that you did everything needed:

[http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/]("http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/")

Yeah -- I know this is for Precise, but it should work the same way for 12.10.

---

### Post by sienile on 2012-11-29
I have already done all of that.

I can now see the Ubuntu share in Win7, but can't access it. Any ideas?

---

