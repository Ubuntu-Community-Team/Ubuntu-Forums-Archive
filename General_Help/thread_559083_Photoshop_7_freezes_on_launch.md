---
title: "Photoshop 7 freezes on launch"
date: 2007-09-24
forum: General Help
---

### Post by earther on 2007-09-24
When the splash screen starts to load Photoshop 7, it freezes almost immediately at "initializing" and becomes unresponsive. Trying to kill process via System Monitor is very, very slow and unresponsive. Closing the terminal kills immediately.

I am able to launch Image Ready and then get to Photoshop that way. Just unable to launch directly. Here is the error printout:

```
~$ wine "c:\Program Files\Adobe\Photoshop 7.0\Photoshop.exe"
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:font:load_VDMX No suitable ratio found
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:font:WineEngRemoveFontResourceEx :stub
```

Launching with this path produces identical results:

/.wine/drive_c/Program Files/Adobe/Photoshop 7.0$


Ubuntu Feisty 2.6.20-16-generic
wine-0.9.45 - new install

Can this be fixed?


PS. When I finally got into Photoshop, the clone tool and healing brush wouldn't work.

---

### Post by p_quarles on 2007-09-24
While I've only used Wine a bit here and there, my understanding is that it calls your Linux partition the "z" drive, and you'll get errors with some programs if you don't install it to that. Here's a tutorial:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by earther on 2007-09-24
It's kind of a bug.  I came across the answer. 

Just keep hitting enter and it will eventually load.   Turning off "Let your window manager control your windows" in winecfg also helps a bit.

---

