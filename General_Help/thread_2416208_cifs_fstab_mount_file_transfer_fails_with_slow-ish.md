---
title: "cifs fstab mount file transfer fails with slow-ish connection"
date: 2019-04-06
forum: General Help
---

### Post by marcus.pearlman on 2019-04-06
This is a problem I've had forever with Ubuntu, since 12.04. I am now using 16.04. The drive is at my work and I mount it from home using Cisco anyconnect vpn. I use cifs mount in fstab to easily mount it. Here is my fstab entry

```
//file/location /media/marcus/place  cifs users,uid=1000,gid=1000,credentials=/home/place/.smbcredentials,iocharset=utf8,noauto,file_mode=0600,dir_mode=0700 0 0
```

First of all, browsing the mount is slow in nautilus, and it seems to do a lot better in Thunar, but that's not what this post is about. When transferring a number of files using a drag and drop in both nautilus and Thunar, the transfer freezes and I need to kill the process. Using the terminal and the mv command works. What is going on with the drag and drop failing?

I don't think it has anything to do with Cisco anyconnect because I recall these problems when transferring files on a local network. The problem is more common with very slow connections. The slower the connection, the more likely the problem will occur. Command line file transfers pretty much never fail.

Another thing to note, when connecting to the mount using the standard Ubuntu dialogue, the drag and drop method works and browsing the shares is smoother. The method uses smb directly in the nautilus browser. see following syntax

```
smb://file/location/
```

The smb connection is what I will use for now, but it would be nice to get the fstab cifs mount working so I don't have to type a password. I'm the type of lazy who doesn't want to type a password for 5 seconds but will spend an exorbitant amount of energy trying to figure how to not type my password :D

EDIT: I just tried drag and drop using dolphin file browser, and it worked. What is the difference between these file explorers? Dolphin is not as pretty, I'd like to use nautilus...

---

### Post by TheFu on 2019-04-07
Are both systems Linux?  If so, perhaps NFS would be faster (since it is usually about 20% faster than CIFS on a LAN).  I've used read-only NFS over the internet for decades.  In the old days, it was how we got software packages - ah ... gatekeeper.dec.com, how I remember you.

Simplify and test.  First step, remove the VPN from the testing.  Do the testing on the local network first.  VPN settings are controlled by the VPN server, so many times security settings are chosen over using performance settings.  CIFS is a poor protocol for use over VPN. The openvpn team explains why numerous places.

Slowness can be cause by any part of the chain. The drive, the cable, the PSU, the computer, the OS, the network card, the ethernet cable, the client versions of all that. Basically, as "why is accessing the drive on the same machine slow."  Prove that isn't the case.  Do the same on the client.  Then move to the networking.  PROVE those aren&#8217;t the issues. Work through each subsystem before you try LAN tests.

Don't use a GUI.  The shell programs doing the copy will be as fast as possible.  Try using **smbclient** directly. How fast is that?  You'll need to run this 10 times and be certain that all buffers have been cleared in exactly the same way before beginning any testing. Normally, that happens with a reboot.  Then use the mount and use the **cp** command directly to copy the files 10 times.  Faster or slower?  You have data now that you can compare.  Which is faster? Why might that be?  Could some options be the issue?

I would being with the storage subsystem, specifically looking at the file system used.  NTFS is slow. VERY slow.  There are some mount options which can make it faster.

But it all begins with simplify and test.  This implies that "it feels slow" is backed up with real data. Facts.  We should be making decisions on facts, not feelings.  Some tools - bonnie++, iperf3, free, iotop, nettop.

Prove it to yourself using the smallest amount of code possible.   And it is probably best to use Mbps, not MBps.  Mbps is what all disk and network manufacturers use.  Using the wrong units of measure will lead to incorrect actions.

After all that, then test the GUIs.  After you've found the issue, if any remains, in the GUI, only then should the VPN be added back into the total test.

IMHO.

---

