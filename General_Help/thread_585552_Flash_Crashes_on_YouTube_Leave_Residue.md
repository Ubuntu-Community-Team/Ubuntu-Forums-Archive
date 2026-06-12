---
title: "Flash Crashes on YouTube Leave Residue"
date: 2007-10-21
forum: General Help
---

### Post by Falcorian on 2007-10-21
So I'm used to Flash crashing Firefox, and I live with it. I can always kill the window and reopen it. But since installing Gutsy, I get a residue when I get the crash (as the screen shot shows).

Any one have any idea on how to remove the residue when it crashes? Killing firefox leaves it, and it's on all my desktops over everything else. Logging out fixes it, but this is of course sub-optimal.

I'm running a nVidia 8800 GTS with the NVIDIA-Linux-x86_64-100.14.19-pkg2.run installed on 64AMD Gutsy (which I freshly installed). I'm using the flash from flashplugin-nonfree. I'm using Compiz as well.

---

### Post by CyberK on 2007-12-12
I can confirm that exactly the same  thing is happening for me. Almost exclusively on YouTube (and rather a lot at that), but also on a few other occasions with other flash sites. My system specs are near identical with Falcorians, and it's rather annoying how a grey rectangle gets left behind exactly where the flash object used to be.  Could this be some sort of combination GNOME-Firefox-Flash problem? Anyone else seeing this sort of behaviour?

---

### Post by emid on 2008-02-03
I have a similar issue.  It happens regularly enough where this is seriously becoming annoying.  Anyone ever figure out a way to stop this?

---

### Post by Falcorian on 2008-02-05
I had to turn off Compiz, that was my "solution" unfortunately.

---

### Post by movil on 2008-02-05
The same here.

What 's the way to turn off Compiz guys ?

It's Compiz really what is messing?
```

martin@martin-xps:~$ ps -ax | grep flash
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
15030 ?        RLl   16:56 /usr/lib/nspluginwrapper/i386/linux/npviewer.bin --plugin /usr/lib/flashplugin-nonfree/libflashplayer.so --connection /org/wrapper/NSPlugins/libflashplayer.so/14930-1
16037 pts/0    R+     0:00 grep flash
martin@martin-xps:~$ kill 15030

```

When I see the process I have to kill this nspluginwrapper thing.

---

### Post by Falcorian on 2008-02-12
I just had this happen without compiz. Not on Youtube, but another flash site left some residue which I had to use ' ps -ax | grep flash' to remove.

---

### Post by Battie on 2008-02-12
Hi!  I had this happen to me last night, actually.

In the system monitor (or in ps, if you like), you will find a program called nswrapper. Kill this and the residue will go away.

I don't know if it's a 64-bit problem, but nswrapper can wreak all kinds of havoc on my machine.  On a few occasions (thankfully not recently), it's locked up my machine so badly that I had to hit the reset button.

Edit: I typically don't run Compiz, by the way.  The problem still occurs.

---

### Post by movil on 2008-02-13
I second that . It's a 64 bits issue. 

Any way to deal with this except killing NSWRAPPER?

---

### Post by Thingymebob on 2008-02-13
I get this too on my 64bit, even with compiz off so I don't think its a compiz issue. I don't use nswrapper for flash so just kill the npviewer process. I'ts been like this since I set up Ubuntu on this system over 12 months ago. Hoping that adobe will release a native 64bit player soon

---

### Post by Battie on 2008-02-13
> **Thingymebob said:**
> I get this too on my 64bit, even with compiz off so I don't think its a compiz issue. I don't use nswrapper for flash so just kill the npviewer process. I'ts been like this since I set up Ubuntu on this system over 12 months ago. Hoping that adobe will release a native 64bit player soon

You're right.  It is npviewer that causes it, not nswrapper.  I got mixed up.

---

