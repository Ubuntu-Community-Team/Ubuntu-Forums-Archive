---
title: "LTSP questions, and Server Edition vs. Standard: what's different?"
date: 2007-08-26
forum: General Help
---

### Post by hndrcks on 2007-08-26
Hi everyone - I am in the midst of setting up an LTSP environment, and have a couple of questions about what might be the best way to proceed:

1)  I  downloaded a copy of 7.04 Server and installed that, and followed the instructions from the wiki to install LTSP and get things running - the install went fine, and the clients would boot to the login splash screen - but then, looking at the system logs,  I ran into problems with missing Xwindows stuff  (like xauth) when actually trying to log in from a client. The login screen would accept user name and password, but then come back to login screen after about two seconds. (ps I did create the users in the chroot - if I tried to log in as a user not in chroot it would give me a bad user / password error.  Valid user logins were accepted, then the login screen would pop back up after a couple of seconds)

My suspicion is that the LTSP packages need a working X environment installed first (outside the ch root) to get all the Xwindows bits required to work properly - is that correct? 

2) Besides the missing X environment, are there other differences between the server and desktop edition (tuned kernel, for instance?) I'm wondering if LTSP performance will be improved if I install the GUI on the server version vs. just working from the desktop version. The final install will have samba services + LTSP on each server; but no LAMP or anything like that.

3) Has anyone built the LTSP clients for various architectures and served them concurrently from one server? Can I offer, for instance,  powerpc and i386 from the same box? I see that the ltsp-build-client --arch will throw an error if one tries to build on the wrong hardware, but what about building elsewhere and then moving to the server?

Thanks for any help you can provide!

---

### Post by hsweet on 2007-08-26
It could be that you have to reset the ssh keys on the server

```
ltsp-update-sshkeys
```

---

### Post by sfgreenwood on 2007-08-30
I came across this post in looking for a similar problem. It's a little bit more esoteric as I am trying to learn how to use LTSP using VMWare and have a Xubuntu VMWare instance as a server and an 'empty' VMWare instance as a client. I was getting the splash screen on the client and then the process was timing out and dropping to the busybox shell. Finding that Ctrl-Alt-F1 returned the client to the boot shell was a great help, as it showed that the client was getting the boot image from the server, but was then trying to get mount data from the VMWare DHCP server. Turning off the VMWare DHCP server fixed the problem, so you might have something similar in your network - hit Ctrl-Alt-F1 after the splash and look for 'nfsmount: need a path' in the first instance. You might also see a different IP address range from the range that is in /etc/ltsp/dhcpd.conf.
I'm not quite sure what I'm missing in the server dhcpd.conf or the client dhclient.conf - I just want the clients to see the DHCP server on the server. I would assume that this wouldn't be an issue in most environments as the server would be expected to have a static IP address but of course there are situations where even static addresses are given out by DHCP.

---

