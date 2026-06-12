---
title: "NIS, NFS, and autofs issue"
date: 2013-01-25
forum: General Help
---

### Post by rbroberts on 2013-01-25
I've just converted a server from Fedora 14 to Ubuntu 12.04. "Converted" of course means a clean install.

I'm now trying to get all of the services back up and running and have some working pretty quickly, but I'm stymied on getting automount to mount work with a local directory. The new Ubuntu 12.04 machine serves home directories; previously, with Fedora, I had the filesystem mounted as /data/home so that /data/home/X will mount as /home/X when the user logs in. This works fine for other client hosts on the network, but doesn't work for the 12.04 machine (it worked with Fedora). I can't even find any indication in syslog that the mount is attempted.

One "obvious" thing which i have not yet attempted is to simply mount at /home instead of /data/home. With some (maybe only old) versions of Fedora, this created a problem because the automounter would try to mount on top of /home/X leaving the directory unusable.

Related to this, I have one Ubuntu 12.10 client host that doesn't like the NIS maps for /home. I had to "manually" enter the auto.home map into /etc/auto.home before it would work. Obviously, that's not ideal, but it works for now.  However, that doesn't work on the server itself. 

/etc/nsswitch.conf includes "automount: files nis" 
Simply putting +auto.master (the default) in /etc/auto.master, which worked for Fedora, and I've tried adding an explicit "/home /etc/auto.home" with that file containing +auto.home or with the actual map of

* archos:/data/home/&

Neither works. Nor does removing the host part.

So...how do I get Ubuntu to work as an NIS/NFS client with the automounter?

---

### Post by rbroberts on 2013-01-25
Okay, here's a fun update. If I try to have a local auto.home, then this doesn't work:
```
*    archos.rlent.pnet:/data/home/&
```
But this does
```
*    localhost:/data/home/&
```
Where auto.master (locally) is 
```
/home    /etc/auto.home
```
In other words, I not using the NIS maps at all.

So the Ubuntu server doesn't like to refer to itself by its name.

---

### Post by rbroberts on 2013-01-25
Aha! It looks like the issue is that when I installed, it picked up the name archos for the host and put it into /etc/hosts as 127.0.1.1. I don't know what the justification is for that, but I've edited the entry to be the actual (static) IP for the host. Now it is happy to remount locally.

---

