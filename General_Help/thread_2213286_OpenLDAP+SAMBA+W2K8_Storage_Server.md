---
title: "OpenLDAP+SAMBA+W2K8 Storage Server"
date: 2014-03-25
forum: General Help
---

### Post by rhunt2 on 2014-03-25
After numerous months I am at a confused stand still my issue:
I have a separate network set up within VirtualBox on Windows7 to do all of this before going into production.
I have OpenLDAP 2.4.35-r1 on a Gentoo server for authentication only for Users, Groups, & Computers. (Trying to move off of W2K3 Active Directory and Domain Controller)
I have a W2K8 Storage Server that I need to have our Groups access by Group authentication  (I have installed Samba 3.26 on Ubuntu 12.04LTS server) I prefer not to configure as a PDC.
I have manually mounted the Windows shares with mount -t cifs  I cannot get the shares to mount in /etc/fstab/ I get a Plymouth error upon Reboot.
Question 1. With OpenLDAP  I have a very basic slapd.conf with core, cosine, inetorgperson, samba, nis, ppolicy schema not using TLS at this time.  I have LDAP set up as the backend in my Samba, how do I go about setting ACL's for the Windows Shares to access an authenticate by the Groups in OpenLDAP/SAMBA? 
Question 2. I will have the majority of PC's be Win7 Pro & Ultimate that will need to authenticate user and computer to OpenLDAP and then access the W2K8 Storage Server via the Samba server?
I have DHCP/DNS working on a Gentoo server.
I have Googled & Bing and tested many variations of the Samba sever setup to try and get this to work and I am failing. If there is anybody that can point me in the right direction I would appreciate it. I can post config files if needed. Regards Lost in Linux Land:confused:

---

