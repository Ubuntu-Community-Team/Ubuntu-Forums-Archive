---
title: "Going To Ubuntu When Heron Is Released, Need Some Help Though"
date: 2008-04-18
forum: General Help
---

### Post by linuxsudo on 2008-04-18
I've been using the Ubuntu in a Virtual Machine (7.10) and I've got used to a lot of stuff Ubuntu has to offer and what it can really do. Before I fully switch one of my machines to Ubuntu when Hardy is released there are some questions which I would like to be cleared up before I go for the install.

1. The MTU on my networking devices I require is for it to be set to 1492, I can change this by running sudo ifconfig (NIC) mtu 1492 every time I log on but I want it to stay this way for both of my Network devices and for all users.

2. Wireless WEP Encryption code, when I log in as myself I have to enter the WEP code the first time I use wireless. After this I get a Passcode Dialogue or something when I log in after. Also can I set my WEP once for the device and have it set so I don't have to re enter it every time I create a new user which logs on.

3. WINE, I've searched this forum for a guide which told me how to set up a system wide WINE C:\ drive by creating a WINE account and then doing a soft link to the other users of the .wine folder. However when I install a Windows Application on WINE it only appears in my Applications menu, not the other users, although I would like them all to be able to access the Windows applications installed.

4. Samba, I can connect to my Windows Workgroup fine and everything displays, however it keeps asking me to enter a Username & Password mostly all of the time. This can be a real annoyance especially when I'm simply setting an image as a wallpaper or copying a Word Document. Once I've entered in my Username & Password once I want it to be remembered.

This is all of the assistance I need for now, thankfully everything else I wanted it to do can be done and i'm generally very pleased with Ubuntu, though it will be a while before it replaces my primary machine I feel that it's ready for the rest of my machines. I'm considering to Install it on my Budget Machines which I sell to my customers instead of using Windows XP as this will be ending support soon.

---

### Post by ibuclaw on 2008-04-18
1) Type this in the terminal.
```
 gksu gedit /etc/gdm/PreSession/Default 
```

And at the bottom, add in the stuff you do with MTU **before** the line that says **exit 0**.

This script, to my knowledge is ran as root each time you log in, so including **sudo** is **not neccessary** in the line you add.

Once. Finished. Save it and quit.
That should fix issue no.1

2) This has been an issue with Ubuntu for a while now.
You'll be glad to hear that I think that it's been solved with Hardy.
See, they've completely scrapped the whole PassKey idea because it was flawed and once it broke there was no way (or no easy way) for even root to fix.
They now have a totally re-vamped integrated key system called [PolicyKit]("https://wiki.ubuntu.com/HardyHeron/RC#head-3410a16ba1e54dc657d8bd9ad77a5acbc54140c9") that works a treat.
At least, I've only ever had to enter it in once for myself. All other users / new users of my system get access to my WPA network just fine without password.

3) No simple way to do this without giving everyone read/write access to the entire system file menu. (ie: when it's gone, it is really gone, not just for your user).

I have a small idea on what to do, but I couldn't explain it straight off on the spot, because it would be sketchy, flawed and dangerous to give to someone to try out.
I'm just gonna try to attempt this with a virtual environment, so I will post later on this question.

4) Again, I think that the new PolicyKit should solve this problem too.
But if it doesn't You can go and look for specific help on that topic when you switch to Hardy.

Regards
Iain

---

### Post by linuxsudo on 2008-04-19
Okay thanks for that. For Number 3 though, isn't there a method which is similar to Windows to have sort of an:

All User Menu
Current User Menu

Or is this not possible in GNOME?

---

### Post by linuxsudo on 2008-04-26
Actually is it possible to have this sort of "All users" menu on KDE instead? I'm going to try Kubuntu KDE 4 Remix.

---

