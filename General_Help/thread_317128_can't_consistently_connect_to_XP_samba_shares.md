---
title: "can't consistently connect to XP samba shares"
date: 2006-12-11
forum: General Help
---

### Post by newlinux on 2006-12-11
Info:
[LIST]
[*]I have a mixed Ubuntu/XP environment, with samba set up on all Ubuntu computers. 
[*]My XP machine to can browse to all of linux samba shares.
[*]All the linux computers consistently mount each other's shares
[*]however sometimes they are able to mount the XP shares, sometimes they aren't. 
[*]It doesn't matter whether I use fstab (sudo mount -a) or simply use the mount command. When it doesn't work I get:
```
6137: session setup failed: ERRDOS - 71
SMB connection failed

``` for each XP share that doesn't mount
[*]Sometimes I am able to mount one of the 4 XP shares, and sometimes I am not. Which ones I can mount are not consistent.
[*]Sometimes one linux computer can mount the XP shares, while the other two can't.
[*]I have all the machines set to the same workgroup, netbios over TCP/IP is enabled.
[*]I am using the username and password of an adminstrator account on the XP machine when trying to connect.
[/LIST]

My google searches have led me to ERRDOS - 71 meaning NT_STATUS_REQUEST_NOT_ACCEPTED.
 Below is a line from fstab that I use that works sometimes and sometimes it doesn't
```
//home-desktop/DATA-NTFS    /mnt/DATA-NTFS-home smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0
```
I can ping home-desktop whether or not I can connect to the share, so it isn't a problem of being able to see the computer on the network.

Any help is greatly appreciated. I can't figure out why this doesn't work sometimes and sometimes it does. I'm at my wits end...

---

### Post by newlinux on 2006-12-12
Could it be too many connections from the same username to the shares? It seems that I can never have all 3linux computers connect to all 4 XP shares at the same time...

---

### Post by technodigifreak on 2006-12-12
> **newlinux said:**
> Could it be too many connections from the same username to the shares? 

First thing I would try is to disconnect all three linux machines, and then try connecting to Ubuntu1 to XP1, then Ubuntu1 to XP2, and so on, then do the same with Ubuntu2 and Ubuntu3.  I know it's twelve combinations to try, but it may at least nail it down to one machine or two machines.  After that, we can go from there....  Let us know what you find out!

---

### Post by wpshooter on 2006-12-12
Newlinux:

You are observing the very same behavior that I have with SAMBA, i.e. it works, but NOT on a consistent basis.

I think they still have some work to do on that software !!!

---

### Post by newlinux on 2006-12-12
> **technodigifreak said:**
> First thing I would try is to disconnect all three linux machines, and then try connecting to Ubuntu1 to XP1, then Ubuntu1 to XP2, and so on, then do the same with Ubuntu2 and Ubuntu3.  I know it's twelve combinations to try, but it may at least nail it down to one machine or two machines.  After that, we can go from there....  Let us know what you find out!

This was going to me next step, and I think the simultaneous connection issue may be the problem. I run XP Home, and from what I've discovered from my investigation (during lunch at work, hopefully I'll have time tonight to test this out) is that XP Home can handle only 5 simultaneous connection sessions, and XP Pro can handle 10. Now the question is are each of these SAMBA connections from my Linux boxes considered a individual session (is each connection to each windows share a session, meaning if computer Ubuntu1 connects to XPshares 1,2,3, and 4 is that 4 sessions or 1 session?) If it is 4 - that's my problem, and explains why I often see the behavior where one Ubuntu computer can get all 4, and the others can only get 1 or none. I never systematically documented that as happening, but I think that is the behavior I am observing. It would also explain why when rebooting some of the computers the other ones sometimes can magically mount them all of a sudden, or after a while which linux computers can mount the shares change. This is because Windows auto disconnects every 15 minutes or so - which would free up connections.

Of course, I think the connections from 1 Ubuntu box to the 4 XP shares should be just one session, but that may not be the way it works. If it is considered 1 session maybe XP just isn't releasing the connections properly, or some other service is connecting as well. Anyway, i have a lot of testing to do to confirm this behavior. I also have a networked DVD player that can browse samba shares to test this out on too...

I will test by first powering down all computers. Then I will boot the XP machine, and then Ubuntu1. If it connects fine, I'll try unmounting and mounting a couple times and observer the behavior. Then I'll reboot Ubuntu 1 and try again. If that goes well, I'll shut Ubuntu1 down and repeat this test with the other Ubuntu machines. If they all work by themselves, then I'll boot one up, connect to all 4 shares and then see what happens when I boot a second up. If I can only get one share, then I know I'll have a pretty good idea that this is the problem. I can then play with the number of shares each computer connect to, seeing what the total number of connections I can get is. If it is always 5, then there you have it... this may take a little while...

I'll post results in a couple days...

---

### Post by newlinux on 2006-12-12
The 5 simultaneous connection problem is the culprit. You can actually see this happening if you connect and browse and XP share and then go to Administrative Tools->Computer Management and look at Shares and sessions. It counts each connection to a share as a session, so XP Home is the problem. You can also see that eventually it disconnects the sessions, so that other computers can grab it. I know somewhere you can change the time it takes to disconnect, which might help most people if you set this number lower, but I think I'll skip that option. I'm going to attempt to get around this by "daisy chaining" my mounts (have one ubuntu computer mount to all the XP shares, and have the others simply mount to that ubuntubox). Hopefully that bypasses the windows XP Home restriction. I'll post an update after I try that...

---

### Post by newlinux on 2006-12-12
so far so good - daisy channing works and solves my problem. WinXP doesn't show any new connections when I connect through the Samba share on another Linux box that maps to XP. Using Ubuntu to get linux to get around windows limitations again...

---

### Post by technodigifreak on 2006-12-13
Newlinux,

Excellent!  I'm glad you were able to get it running.  Had I known it was Home Ed.  I would have told you it was client connections.  And anytime a machine remote machine accesses a share, that's considered to be a connection.  I hadn't thought of daisy chaining the samba machines, but it makes sense.  Did you have to change any settings in samba or did you simply share a mounted share from the XP machine?

---

### Post by newlinux on 2006-12-13
I didn't change any settings, I simply setup a share of a mounted share - I have to admit, I haven't tested it thoroughly (I had some other things to do) but I did test that It didn't show up as a connection in XP when I was browsing them from the "share of a share" and that I was able to list files and directories. Although it shouldn't matter (because on the machine that mounts the XP share it shows up as a connection as soon I even list the directory contents) I won't officially count this as working until I access the files (play a song, open a document, etc.) a few different times -- to make sure XP doesn't count that as a connection. But hopefully I didn't jump the gun on saying it works.

I new there were networking differences between XP Home and Pro - but I hadn't given them any thought in quite some time so I didn't think to mention which one I was using at first... The sad thing is that this is a dual boot XP/Ubuntu machine, but my wife primarily uses it for windows, so I have to have a solution that works when it is booted to windows...

---

### Post by newlinux on 2006-12-13
Okay. I haven't had any problems accessing the daisy chained shares from multiple computers at the same time, so I think it all works. wpshooter, what issues are you having?

---

