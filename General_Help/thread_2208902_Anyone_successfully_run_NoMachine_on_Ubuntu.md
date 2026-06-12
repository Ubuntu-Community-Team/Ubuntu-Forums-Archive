---
title: "Anyone successfully run NoMachine on Ubuntu?"
date: 2014-03-02
forum: General Help
---

### Post by tinker123 on 2014-03-02
Anyone successfully run NoMachine on Ubuntu?

If so, can you tell me which version of Ubuntu and NoMachine you have?

Thanks

---

### Post by TheFu on 2014-03-03
There is a client AND a server.
For the server, I use FreeNX. [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) follow the instructions CAREFULLY!
For the client, I use NoMachine v3.5 ... it was in a .deb package - nxclient_3.5.0-7*.deb

---

### Post by tinker123 on 2014-03-04
I didn't have any luck with FreeNX.

I did get NoMachine 3 ( required by my org ) to work on Mint 14.

For other people with similar problems Googling this is what I did
[http://forums.linuxmint.com/viewtopic.php?f=47&t=161232](http://forums.linuxmint.com/viewtopic.php?f=47&t=161232)

Thanks

---

### Post by TheFu on 2014-03-04
> **tinker123 said:**
> I didn't have any luck with FreeNX.

I did get NoMachine 3 ( required by my org ) to work on Mint 14.

For other people with similar problems Googling this is what I did
[http://forums.linuxmint.com/viewtopic.php?f=47&t=161232](http://forums.linuxmint.com/viewtopic.php?f=47&t=161232)

Thanks

Seems the guy at that link was trying to run 32-bit binaries on a 64-bit OS. Why not just use the amd64 version of the NoMachine NX client?

As far as FreeNX is concerned:
a) did you WANT to run it as a server?
b) "didn't have any luck" is a little vague -did you want help to use a F/LOSS NX server?

---

### Post by QIII on 2014-03-04
Yes.  I used to run 3.5 and now run 4.0.

4.0 has a Windows server now, so I do my remoting to my Windows machine with NoMachine (Win 7 Pro.  I don't know about Win 8).  But you don't SSH to Windows, so mind your firewall/security.

4.0 is dead easy to install (install openSSH or the like and get it set up correctly first).  

Sound now works properly, but being a remote you won't get satisfactory video.  Bandwidth usage is extremely low so you don't bog down your network.

---

