---
title: "Using Mac apps in Linux?"
date: 2008-01-17
forum: General Help
---

### Post by runemaste644 on 2008-01-17
How can i install Mac apps on Linux? Since OS X  is UNIX, it is possible to use Mac apps in Linux, but Mac drivers wont work in Linux (You cant have an emulator recognize something that the host doesnt recognize!) In specific, i want to run iTunes, Safari, and maybe Quicktime.

---

### Post by morgan_greywolf on 2008-01-17
Not really.  You can have the QuickTime codecs installed either from Synaptic or by downloading a QuickTime movie and trying to play it -- the system will prompt you and walk you through installing them automatically.

You could run OS X in a virtual machine -- if doing so were comletely legal.  I'll tell you that a modified OS X for Intel Macs can run in [VirtualBox](http://www.virtualbox.org/), but you would have to already own an Intel Mac and live in a jurisdiction where hacking OS X isn't a violation of the law like it is in the United States (it violates the Digital Millennium Copyright Act)

It is possible to run the Windows versions of iTunes and Safari under a VirtualBox (or other) vritual machine running Windows XP.  Windows XP doesn't need to have any DRM code removed in order to run under VirtualBox, and if your PC came with Windows XP you probably already have a legal license to run it in a virtual machine.

iTunes and Safari may possibly run under Wine, but you'd have to ask someone who's tried it.  Wine (Wine Is Not An Emulator) is a tool for running win32 code under Linux.   It's a bit complex to get up and running and you'd be much better off with something like VirtualBox, which can even seamlessly integrate Windows into your existing desktop.

---

### Post by staticvoid on 2008-01-17
sudo apt-get install wine

then find an older version of safari, iTunes and quicktime. The older ones will work.

iTunes is bloated. try some linux apps like banshee, exaile, rhythmbox, audacious

its fun stuff. U can run linux apps in mac for the unix reason but not vice versa... i don't think so at least...

sv

---

### Post by runemaste644 on 2008-01-19
well safari 3 for win works for a second but not for long.
Oh, and if i try to get xp working in vm from my hard drive, it gives me a nice, big BSOD

---

