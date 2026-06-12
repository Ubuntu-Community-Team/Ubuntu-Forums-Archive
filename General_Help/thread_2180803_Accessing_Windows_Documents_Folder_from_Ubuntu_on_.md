---
title: "Accessing Windows Documents Folder from Ubuntu on dual boot system"
date: 2013-10-14
forum: General Help
---

### Post by testconfig on 2013-10-14
Hi, just wanted to post my solution that I couldn't post on an old closed thread...

**Environment**:  dual boot laptop (Acer) with Windows and Ubuntu installed
**Problem**:         Accessing the Documents folder on Windows from Ubuntu
**Solution: **
        (1)In the left hand pane of Nautilus file explorer (if that's what you call it) there's a "Devices" and "Computer" grouping
                       (2)Under "Devices" click on "**Acer**" drive 
                       (3)In the right pane, navigate to: ** /Documents and Settings/<username>/Documents, **where <username> is the user id you use to login to Windows

Hope this helps the noobs out there!

Steph
PS.  Why would you need this?  You downloaded a tool from inside Ubuntu that only runs on Windows, and before you reboot into Windows to install it, you need to store the file on the Windows "Documents" folder (since you can't access Ubuntu partition from Windows, only Windows partition from Ubuntu).  Of course you can work around this by using a thumb drive LOL.

---

