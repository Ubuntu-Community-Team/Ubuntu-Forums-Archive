---
title: "No access to Readyshare usb storage after Ubuntu 18.04.1 LTS install"
date: 2018-08-24
forum: General Help
---

### Post by telegramsam23 on 2018-08-24
Hi, I have no access to my usb storage ( Readyshare ) connected to my Netgear router since a new install of Ubuntu 18.04.1. I have tried the obvious - Files > Other Locations, which gives me 'Windows Network' and 'LPTP' ( my laptop's name). If I click on Windows Network I get an error message - 'Unable to access location - Failed to retrieve share list from server: No such file or directory' I have tried using the connection bar at the bottom of the Other Locations page ie - smb:\\readyshare\cruzerdrive, and smb:\\ [IP address]\cruzerdive or substituted 'cruzerdrive' ( the name of my flashdrive ) with usb_storage but nothing is working. Samba is installed correctly I believe and the flashdrive is set up properly ( I can access it with my wife's ipad ) I could access it perfectly with my old laptop with MATE  OS installed no problem so I'm at a loss as I'm not a massive computer boffin. Any help would be greatly appreciated, thanks

---

### Post by TheFu on 2018-08-24
Welcome to the forums.

Check that the Readyshare protocol level meets the same level that 18.04 uses. If not, you'll need to modify the protocol level used on either the Readyshare or on Ubuntu.

I thought the 18.04 release notes said something about that?

---

### Post by telegramsam23 on 2018-08-25
Hi, thank you for your reply, I must admit I didn't read the release notes, I doubt they would make much sense to me anyway but I will have a look and see if there is something in there that's relevant. Thanks again for your time
Update - I have checked the release notes and it suggests that I may need to 'specify vers=1.0 on mount' if the server does not support smb version3?  As I suspected this is over my head. At this moment in time I don't know if my Netgear router meets such a requirement, or where to look for that information, or if I did, how to modify such a setting. Any help would be appreciated, thank you.

---

### Post by TheFu on 2018-08-25
**18.04 Release notes on CIFS:**

> Default CIFS/SMB protocol version change in CIFS mounts

Since 17.10, the default SMB protocol used when mounting remote CIFS filesystems via mount.cifs (from the cifs-utils package) changed to 2.1 or higher, depending on what is negotiated with the server. If no version is specified when mounting such a remote share, the following will be logged:

No dialect specified on mount. Default has changed to a more secure dialect, SMB2.1 or later (e.g. SMB3),
from CIFS (SMB1). To use the less secure SMB1 dialect to access old servers which do not support SMB3
(or SMB2.1) specify vers=1.0 on mount.

Should you encounter compatibility issues, like #1764778 or #1572132, please specify vers=1.0 when mounting the share and please file a bug if that fixes the problem for you. 

---

### Post by telegramsam23 on 2018-08-25
Hi, thank you for your help, given that there is a security issue with smb-1 I will look for a different solution, my router page has a 'new firmware' link which has appeared since I looked last so I'll give that a go, thanks again

---

### Post by TheFu on 2018-08-25
> **telegramsam23 said:**
> Hi, thank you for your help, given that there is a security issue with smb-1 I will look for a different solution, my router page has a 'new firmware' link which has appeared since I looked last so I'll give that a go, thanks again

Current router firmware is security 101.

Connecting any storage directly to a WAN-facing router is anti-security 101, if that is your plan.  Unless the goal is to share all the files over the internet to everyone.  It is kinda like saying don't post your private information on the internet thinking that nobody else will see it. ;(

---

### Post by telegramsam23 on 2018-08-25
Thank you

---

### Post by TheFu on 2018-08-26
Solved?  Please use "thread tools" button to mark it. This greatly helps the community.

---

### Post by faure212 on 2018-11-30
TheFu-- Could you please explain what you mean?  If I plug a USB flash-drive into my Netgear router, is it exposed more than my computer that is hooked up to the same router?  The folders on the USB flash-drive require a username/password to access them.

---

