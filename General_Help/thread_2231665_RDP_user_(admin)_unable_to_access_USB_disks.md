---
title: "RDP user (admin) unable to access USB disks"
date: 2014-06-27
forum: General Help
---

### Post by vsp2 on 2014-06-27
I'm running Ubuntu 12.04 - updated as of June 23rd on my HTPC box

The XBMC user account is set to log on automatically; for admin and backup purposes I use xRDP w/ MS remote desktop to remote login from Windows

The issue I'm facing is:

1. The first user to log in (the XBMC account) gets ownership of any USB drive. The sudo user logging in via RDP has no rights to access the disk.
2. Have tried making the xbmc user an admin as well and then  (A) using chown (B) using chmod to give the main admin account the required permissions.

However, nothing seems to work. My only way out is to first log out from the XBMC session.

What I'm trying to do is: Let XBMC log in automatically and stay running, and letting me use the RDP session for making backups, etc.

Cheers,

VSP

---

