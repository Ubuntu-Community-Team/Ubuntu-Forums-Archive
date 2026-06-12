---
title: "Xorg.0.log has no timestamps but there is an old patch for it"
date: 2014-08-18
forum: General Help
---

### Post by bulrush2 on 2014-08-18
- Windows 7 running Xming 6.x
- Connecting to Ubuntu 14.04LTS via Putty 0.63 and ssh

I'm having some issues with Xwindows and looked at /var/log/Xorg.0.log. There are no timestamps in the log but there is a 4+ year old patch for it here: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/285787](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/285787)

So do I have to turn on timestamps for this log? If so, how? 

Thank you.

---

### Post by tgalati4 on 2014-08-18
I think timestamps interferes with the real-time nature of mouse and keyboard inputs.  I presume that you are having problems with Xming on Windows?  The Xorg.0.log file handles the graphics server not the client.  For client errors look in .xsession-errors.  There are timestamps--I believe it is in seconds since boot of the client machine.

What specific issue are you having?

---

### Post by bulrush2 on 2014-08-18
My root problem is here: [http://ubuntuforums.org/showthread.php?t=2240160](http://ubuntuforums.org/showthread.php?t=2240160)

---

