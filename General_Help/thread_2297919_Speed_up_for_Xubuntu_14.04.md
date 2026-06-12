---
title: "Speed up for Xubuntu 14.04????"
date: 2015-10-07
forum: General Help
---

### Post by s9032g@comcast.net on 2015-10-07
Before I try this suggestion to speed up Xubuntu 14.04 I want to ask if anyone sees a problem with it. These suggestions often are not what they seem.

Create a file named .gtkrc-2.0 in home directory and paste in the following lines:

gtk-menu-popup-delay = 0 
gtk-menu-popdown-delay = 0 
gtk-menu-bar-popup-delay = 0 
gtk-enable-animations = 0 
gtk-timeout-expand = 0
gtk-timeout-initial = 0
gtk-timeout-repeat = 0

Save file > close > Logout > Login back

Thanks

---

### Post by ajgreeny on 2015-10-07
I have the first five lines of that suggested text file in my .gtkrc-2.0 and have had now since I first started using Xubuntu.

It can make a big difference particularly if your computer is of low spec than it might be, and it is dependent on your resources/spec; if you have a fast machine you may not see any noticeable differences.

The most noticeable speed up I found was to make thunar to open much quicker on first use after booting the computer by  editing **/usr/share/gvfs/mounts/network.mount** and change it from:
```
[Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
AutoMount=true
```
to
```
[Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
AutoMount=false
```
it will make opening up thunar very quick again even for the first time.  If you want smb browsing you just click on the network:/// link in thunar and it will then do the browsing search which takes a bit of time.  I don't have windows or need to use smb so this is not a problem for me.

---

