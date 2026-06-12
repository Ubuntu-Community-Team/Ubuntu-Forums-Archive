---
title: "No access to network mediaplayer with ubuntu 20.04"
date: 2020-05-29
forum: General Help
---

### Post by camilob on 2020-05-29
Hi,

I'm using ubuntu 20.04 on an HP Elite 8100 machine connected by wi-fi to the net. On the same wifi router I have wired a Western Digital media player which I cannot see or access from my machine with linux. I just see an icon ·windows network", when I click on it, nothing happens.
 However, from my Windows 10 machine  I can view and access the player without problems.

 I'll appreciate any help setting up.

Thanks in advance

---

### Post by TheFu on 2020-05-29
What is the WD model, exactly? Look for model number, but not S/N to go with the name.
You're going to need to know the exact versions of the the exact protocols supported by that WD machine.
CIFS, Samba, NFS, DLNA, something else?  It could be proprietary.  Some "players" don't have server code, they only have client code, so you'd need to setup your Ubuntu system to be the server using one of the protocols supported by that specific WD device.

Servers really should never use wifi.

---

### Post by grahammechanical on 2020-05-29
Having only one machine I have never done what you are trying to do. The Ubuntu Desktop Guide has a section on Networking, web & email>Sharing>Browse files on a server or network share.

You might get some answer there.

Regards.

---

### Post by camilob on 2020-05-30
Hi, thanks for your answer.

The player is a WD TV LIVE HUB. Works with [COLOR=#000000]Samba as well as DLNA.
[/COLOR][h=1][/h]

---

### Post by TheFu on 2020-05-30
> **camilob said:**
> Hi, thanks for your answer.

The player is a WD TV LIVE HUB. Works with [COLOR=#000000]Samba as well as DLNA.
[/COLOR][h=1][/h]

And the specific versions of those protocols?
i retired my WD TV Live HD media player about 8 yrs ago due to the lack of format support.
[https://blog.jdpfu.com/2011/02/10/very-cheap-nas-wd-tv-hd-live](https://blog.jdpfu.com/2011/02/10/very-cheap-nas-wd-tv-hd-live)
Since that article was written, default protocol versions have changed on Ubuntu and Windows for speed and security reasons.  i suspect the WD hub only supports v1 of samba where Ubuntu wants v3 now.

---

### Post by camilob on 2020-05-30
Hi TheFu

The firmware version of my WD box is 3.12.13. No idea about version for each sharing protocols...

Thanks again

---

### Post by TheFu on 2020-05-30
Try using the IP address to access the WD-TV Hub from Ubuntu.  Look at the Ubuntu logs when you do this. They are in /var/log/ somewhere.

---

### Post by camilob on 2020-05-30
Hi,

It is a Ubuntu issue!, I've check with other machine loaded with Debian 9 and...ohhh...surprise, I can see and access to the mediaplayer media files without problem. 

Thanks again.

---

### Post by Morbius1 on 2020-05-30
Probably not an Ubuntu issue. Debian 9 has a version of samba ( both server and client ) that went End-of-Life in March of 2018.

The version of Samba in Ubuntu 20.04 disables SMB1 on the client ( security reasons ) and without it it can't access anything that can only be accessed by SMB1. You can force a modern samba client to access things with SMB1 by editing /etc/samba/smb.conf and adding a line to the [global] section:  ```
client min protocol = NT1
```

You folks need to learn how to do a cifs mount if you have all of these devices that can only speak SMB1. Then it can be device specific rather than making it apply to everything.

---

### Post by camilob on 2020-05-30
Hi Morbius1

Thanks a lot!, you save me the day. I did it according your code and now is working perfect!

Thanks all again for the time and dedication

Cheers

---

