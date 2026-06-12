---
title: "Ubuntu Server used as Network storage Windows 2003 domain controller profile storage"
date: 2008-03-30
forum: General Help
---

### Post by nikolas22t on 2008-03-30
The situation:

I have a Windows 2003 Server that is used as a domain controller to handle my Windows users clients and roaming profiles. In that server i have limited storage so i want to use a second server running ubuntu as my network storage.

How i can connect the two servers together in order to Domain Controller will have the right to auto create Profile Folder of each of my users when a user logins for first time and give access only to that specific user to that folder... And also the user will be able to access only the folders in that network storage that his group have the permission to do...
 
I tried using samba but for some reason profile is not created , maybe because is asking for a username...(even that password is empty)

Any idea how i can solve this...?

---

### Post by HermanAB on 2008-03-30
Some black magic is required.  I presume that you know that you got to use Winbind to turn Samba into a Domain Client Server?

This may help:
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

Cheers,

Herman

---

