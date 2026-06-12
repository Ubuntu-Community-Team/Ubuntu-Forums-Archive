---
title: "Ubuntu Samba Share Help"
date: 2014-06-05
forum: General Help
---

### Post by seriousxd on 2014-06-05
Hello everyone,
I am VERY new to linux and Ubuntu, so sorry if it is a little frustrating to work with me.  I have been spending the past day trying to understand how linux ubuntu works!

So basically I just installed Ubuntu on an old laptop and followed this tutorial:[http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu](http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu)

it has me share the drives that I want on the network through right clicking them and clicking properties in and the local network share tab in nautilus.  It tells me to select add persmissions and read and write
Then I use:
```
sudo smbpasswd -a user 
```
to create a user and password to access the share.

But I have run into some problems.  When I go onto my windows 8 machine to try and connect it will not let me get in.  I click map network drive and type in the credentials and it says the domain is the name of my windows 8 machine.  But it tells me that I do not have permission to access the shared folder.  Is there something that I am doing wrong in terms of setting up samba?  Or do I need to change something in windows

Thanks, I really appreciate the support

---

### Post by TheFu on 2014-06-05
So ... I've never seen Win8 - not once. Don't have a clue about that.

Also, learning the basics to Linux/Ubuntu requires more than a few days.  After 6 months ... perhaps.  Linux may appear like Windows, but it most definitely is NOT. It has a completely different philosophy, so almost everything under the GUI works differently from Windows.  Security is at the core, not added on later. Everything inside the kernel was written for a multi-user system from the beginning in Linux. There isn't any way to get around that ... well, except the way that Puppy does it - by running everything as root - which is highly, highly, highly, non-secure.

So - I googled "win8 samba connection ubuntu" and that found a few how-to articles specific to Win8. Hope those help.

And if you are active on Lifehacker, tell Whitson that I said hello!

---

### Post by seriousxd on 2014-06-05
Okay, well thanks for helping!

---

