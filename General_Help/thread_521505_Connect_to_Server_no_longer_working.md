---
title: "Connect to Server no longer working"
date: 2007-08-09
forum: General Help
---

### Post by msergent on 2007-08-09
For the past 4-5 months I have been using the Gnome connect to server smb connections to access various W2k3 file server shares. Today however when I tried to open a share using the keyring to authenticate with the passwords I receive an access denied which after several attemps locks out my domain account (which I reset using my domain admin account). I am able to log into the file servers using RDP and my domain credentials. I receive the following error from scanning the security event logs on the W2K3 file server:

Logon Failure:

 	Reason:		Unknown user name or bad password

 	User Name:	nrp123456

 	Domain:		US

 	Logon Type:	3

 	Logon Process:	NtLmSsp 

 	Authentication Package:	NTLM

 	Workstation Name:	CNU40605VK

It seems to be an issue with any of my W2K3 servers.

My password is ~30 days old on a 90 day rotation and I can log into any of the W2K3 boxes without any issues.

---

