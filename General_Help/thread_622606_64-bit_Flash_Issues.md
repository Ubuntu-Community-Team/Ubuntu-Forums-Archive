---
title: "64-bit Flash Issues"
date: 2007-11-24
forum: General Help
---

### Post by ZachSka87 on 2007-11-24
Hey all!  I have an odd issue with Flash on my 64 bit installation.

I installed Firefox 3 in /opt/.  I know, it's beta and I probably shouldn't have.  Bit I did.  Thus the problem.

I relinked all my desktop and application settings to point to the opt directory.  I couldn't get flash installed so I replaced Firefox 3 with 2.0.0.9 again, and it still doesn't work.  I tried installing flash through synaptic and command line using nswrapper and such, putting a link to the wrapped flash in both my /opt/ directory and the default firefox install directory.  Still nothing.  Any ideas?

I also reinstalled EVERYTHING using synaptic.

---

### Post by Seq on 2007-11-25
Try removing flash plugin files from the  directory ~/.mozilla/plugins/

---

### Post by ZachSka87 on 2007-11-25
There's nothing in that directory?  I might have screwed this up bad.  Is there a way to use my CD and restore everything to the way it was originally?

---

### Post by ZachSka87 on 2007-11-25
I have chosen to just do a clean install of Ubuntu.  I'll let y'all know how it turns out.

---

### Post by Seq on 2007-11-25
> **ZachSka87 said:**
> There's nothing in that directory?  I might have screwed this up bad.  Is there a way to use my CD and restore everything to the way it was originally?

Don't worry, this is a good thing to have empty for flash issues :)

If you have not yet wiped your system, try viewing "about:plugins" in firefox, and let us know what it says. It should be something like:

> **Shockwave Flash**

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r48

---

### Post by ZachSka87 on 2007-11-25
Eh, too late.  Thanks for the help, though.  The fresh install fixed it.  From now on I just need to be a bit more careful.  I'm not quite a Linux noob anymore...but I think I try to push the envelope a bit sometimes.  Thanks a lot!

---

### Post by General_Luzi on 2007-11-25
Hello,

I'm quite a linux noob but i have already read a lot of posts to solve my flash problem.
The about:plugin page says that i installed npwrapper.libflashplayer.so Shockwave Flash 9.0 r48,  but i'm not able to use it. I have Ubuntu 7.10 x64! Perhaps somebody can help me!

Greetz

---

### Post by ZachSka87 on 2007-11-26
Does it show as installed in Synaptic?

---

