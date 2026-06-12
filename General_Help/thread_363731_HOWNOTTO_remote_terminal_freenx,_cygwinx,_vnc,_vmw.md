---
title: "HOWNOTTO: remote terminal: freenx, cygwin/x, vnc, vmware - days and days of GRIEF!"
date: 2007-02-17
forum: General Help
---

### Post by jom2000 on 2007-02-17
I've always been interested in linux in theory, but in practice it has been like waiting for a bus - the reboot time in a dual boot installation means that it's never there when you need it. Much quicker to load the windows application rather than the equivalent Linux one.

But now **everything has changed** - since I discovered vmware. I can switch from Windows to Linux apps instantly. I can't believe I didn't try this sooner. Fantastic I thought - until I tried to make it **WORK** properly.

The first problem is that the vmserver console is **dog-slow** (even with vmtools installed). Vnc is not much better. Remote Desktop (RDP) for Windows is great, but there is no server for Linux. Never mind, I tried Cygwin/x using XDMCP - and it worked very well. Well, I DID have this copy-paste problem, which I found the solution to on the-love-shack.net:

*"Ok, this has been driving me **INSANE** for weeks now. I use the Cygwin X server to connect to a Linux machine via XDMCP..."* [http://www.the-love-shack.net/2006/09/14/cygwin-x-clipboard-integration/]("http://www.the-love-shack.net/2006/09/14/cygwin-x-clipboard-integration/")

So for the first time in my life, I had a ***secure web browsing experience***, using Cygwin/x to control Firefox on Ubuntu 5.0.5 on the "browser appliance" which I had downloaded from vmware. I was really pleased and wanted to do more. Little did I realise what **GRIEF** was to follow.

I downloaded the latest 6.10 Edgy release, again as a vmware appliance. It didn't work properly with cygwin/x - a very annoying KEYBOARD DELAY as described in this bug report. Same story with 6.0.6. It took me hours and hours and HOURS to find this:
[https://bugs.freedesktop.org/show_bug.cgi?id=7911](https://bugs.freedesktop.org/show_bug.cgi?id=7911)

With gritted teeth I had to accept that cygwin/x is now **UNUSABLE**, and no-one is going to fix this problem anytime soon. I needed an alternative. I then spend several DAYS on the following:

**cygwin/x old** version - might have worked, except they don't provide OLD versions for download
**freeXer** - it CRASHED when trying to run
**Xming** - like a dumb b*strd I spent hours with this before I realised it only supported individual remote windows, and NOT what I wanted: a complete remote desktop
**xwinlogon** - worked very well, based on an old cywin dll. Except the clipboard copy and PASTE doesn't work.
**freeNX** - I decided to install on 5.0.5 first. Unfortunately it is not in Ubuntu (though it is in other linuxes). However it didn't take too long to find that the sveasoft repositories contain a freenx package - and that some b*std has deleted the version 5.0.5. I then tried on 6.10 and found that some b*strd didn't think it necessary to have freenx on 6.10. However the 6.0.6 version seemed to work on 6.10.

**Full of hope** I installed the nxclient on my PC (the OLD version 1.5.0, not the new 2.0 which doesn't work with freenx). It worked! I could copy from Ubuntu and paste in Windows. Then I tried from Windows to Ubuntu - it didn't work. I was ready to **SCREAM** insanely. Then I found I had an **old** OLD version: 1.5.0.114. I discovered the existance of a **newer** OLD 1.5.0.138 version of nxclient. If only someone had told me in the beginning to google for:
nxclient-1.5.0-138.exe
Still, it still didn't work.

I haven't given up yet. I've just come across this website:
[http://www.cs.cmu.edu/~rcm/RemoteClip/](http://www.cs.cmu.edu/~rcm/RemoteClip/)

Must give it a try...

---

### Post by jom2000 on 2007-02-18
I got the RemoteClipboard working, I just needed to install Sun Java. It works well with FreeNX, so at last I've got a working Remote Desktop which I am happy with.

---

