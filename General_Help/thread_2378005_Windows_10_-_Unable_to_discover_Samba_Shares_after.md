---
title: "Windows 10 - Unable to discover Samba Shares after update"
date: 2017-11-18
forum: General Help
---

### Post by backspin on 2017-11-18
Ubuntu 17.10

I’ve had Samba running for quite some time and it appears just recently a Windows update has killed the machine from being able to discover Samba shares. It appears I can manually map the shares using a UNC path, but discovery is broken.


The issue is I use NextPVR to record OTA TV shows, and the recording destination is the Samba video directory share. I did a recent update and have to re-enter the UNC paths by following the “Network” icon in Windows, and since it no longer sees the server, I can’t record shows over the network.


Does anyone know if there is a workaround for this issue on the Ubuntu side or is this all Windows? One change I performed was to edit the smb.conf and appended a line for SMB2 minimum and restarted. 

*Update**


As a temporary workaround, I went into Nextpvr’s config.xml and manually typed in the UNC path, and I’m now recording over the network again.


However, I would like to know what should be done on the Ubuntu side to get Windowz discovery working correctly. Maybe it is all a Windoz issue?

---

