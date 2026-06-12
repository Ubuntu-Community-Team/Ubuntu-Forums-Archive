---
title: "upon booting 10.10 suddenly encounter error"
date: 2012-10-21
forum: General Help
---

### Post by Kalashnikoffee on 2012-10-21
I'm a recent convert so I have a VERY limited understanding of this.

I had just started using ubuntu 10.10 a few months ago and everything was just peachy but the other day I tried to boot up and here's what happened.

Upon a normal boot I'm met with the following script:

mountall: error while loading shared libraries: /lib/libudev.so.0: invalid ELF header
init:mountall main process (382) terminated with status 127

at this point I have no options (fyi 382 is a different number every time but 127 is always the same)

Upon Booting in recovery mode mode it ends up with: 

Begin:Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.

and then it just stagnates without any sign of activity. 

I looked around for some other threads that might mention the same error message but I couldn't find anything that looked liked it matched.

Anyone think they may have an idea about what I can do? Thanks in advance!

---

### Post by Starcruiser322 on 2012-10-22
The 382 is a randomly assigned process number, it will always change. The 127 is an error code, and I'm sure some more experienced user will have my head for even suggesting anything... but I'll give it a go.

Anyway, the first thing to try is removing all external devices and wires (ethernet) except the keyboard and monitor (if you have a desktop). Often newly installed hardware will cause some issues. If you boot successfully, try reconnecting one at a time and rebooting to pinpoint the problem.

If you have a live cd/dvd/usb, run this bootinfo script from it: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
This will help to diagnose

You may also want to look at this thread: [http://ubuntuforums.org/showthread.php?t=1730113](http://ubuntuforums.org/showthread.php?t=1730113)

---

### Post by Kalashnikoffee on 2012-10-22
I feel like an idiot. used my old keyboard after disconnecting my wireless usb keyboard/mouse combo and it booted without incident. thanks for the help!
\

---

### Post by MikeCyber on 2012-10-22
USB should work fine. Any errors are related to some misconfiguration. Search with google, I know some found solutions for alike in the x-plane.org forum.

---

