---
title: "Remoting into Windows XP desktop from Ubuntu"
date: 2007-02-06
forum: General Help
---

### Post by adam_pretty on 2007-02-06
I've spent the best part of today trying to find the best way of remoting into a pc on the network, as I have some .NET work coming up and really dont want to have to go back to using Windows!! 

So far I have followed the steps here: [http://www.ubuntuforums.org/showthread.php?p=2025967](http://www.ubuntuforums.org/showthread.php?p=2025967)


and managed to get ssh working, I can ssh into the cygwin prompt on the XP machine... which is a start! 

To be honest I dont know if I need ssh for this - thought I would just need VNC but a lot of the tutorials mentioned SSH and I could not get VNC working on its own at all. 

All I want is to remote in across the network ... if anyone knows a nice simple way of doing this, or if I am close ... would be much appreciated!

Cheers

---

### Post by kebes on 2007-02-06
What I typically do is run a TightVNC server on the windows machine and connect to it via VNC. TightVNC on Windows is super-easy to set-up.

However when I'm doing it, it's an internal, closed network. If you're going across the internet, then for security reasons you should probably tunnel the traffic through SSH. The network your Windows machine is on may very well block the VNC traffic anyway, which is why you would need to SSH. Running VNC through SSH is very easy, assuming you can get your windows machine to accept SSH connections.

To run an SSH server on Windows, this might be easiest:
[http://sshwindows.sourceforge.net/](http://sshwindows.sourceforge.net/)
(Never used it myself, but it looks good.)

---

### Post by adam_pretty on 2007-02-06
Just need to add ... trying to start VNC Server on the XP machine just tells me "connection failed"

---

### Post by adam_pretty on 2007-02-06
I'll try TightVNC, currently using RealVNC on the XP machine. 
I've used VNC to remote into Mac's in the office from Ubuntu... but things are never simple on Windoze.:roll:

---

### Post by ^rooker on 2007-02-06
You could also try using Windows's internal "Remote Desktop Protocol" (RDP) for this. On windows servers it's also called "Terminal Server".

---

### Post by juicemansam on 2007-02-06
Currently I use rdesktop to connect to WinXP PCs in the LAN (I'll be adding a VPN for real remote situations later). Though some programs don't work well with remote sessions (on the windows side). For instance, AVIDemux crashes as soon as I initiate the session, regardless of it's window being accessed or not. But that happens with WinXP to WinXP remote connections as well.

---

### Post by adam_pretty on 2007-02-07
All I had to do was set up Remote Desktop connection in XP and connect via RDP!  Easy!

At least I learnt a few things on the way....

---

