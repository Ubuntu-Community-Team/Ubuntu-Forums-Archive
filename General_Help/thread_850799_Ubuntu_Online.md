---
title: "Ubuntu Online"
date: 2008-07-06
forum: General Help
---

### Post by Sesshomaru on 2008-07-06
Hey all,

I'm a bit new to Ubuntu and even Linux in general.  But I've caught the bug and love it!

But what I am wondering is, would it be possible to run Ubuntu, or any Linux flavor for that matter,  online.  By that I mean, could you run the OS from an online server or web host and have a full, usable OS that you can access over the web at a dedicated IP or something.

I'm not even really sure why I anyone would want to do this, but I just thought it might be fun to do it.

Now, I'm presuming that you could do a VPN or VNC kind of thing with Ubuntu, but I'd like to do it using a web host or other server that isn't running from my home or office.

So, possible or crazy ramblings of someone not familiar enough with Linux?

Thanks for any thoughts, advice, and even spiteful criticisms about my lack of knowledge.

--Sesshomaru

---

### Post by tamoneya on 2008-07-06
it is possible to configure something called a PXE network boot.  It is often used in setups where most of the computers dont have harddrives (harddrives draw power).  In a PXE boot the bios basically boots off a network drive.  This is however typically done over a internal LAN or something.  Ive never seen it done across an internet connection and see no reason why it wouldnt work except that it would be slower.

---

