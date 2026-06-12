---
title: "Remote Desktop"
date: 2005-10-23
forum: General Help
---

### Post by JediPottsy on 2005-10-23
Hi,
I like Linux alot, however theres some applications that just wont run. 
So can i install a remote desktop on my home windows machine, and then use it on my laptop from anywhere?

i heard about FreeNX, but isnt it just for linux based? Ie 2 linux machines, not 2 windows machines.

---

### Post by AJRitz on 2005-10-23
Terminal Services is a Remote Desktop client and is part of a default Ubuntu install.  You can access your WinXP machines via Terminal Services if you have RDP set up on the WinXP machines.  IIRC, you can only set a WinXP Pro machine up to accept incoming RDP though.

---

### Post by dtfinch on 2005-10-23
I have a launcher on my desktop for my old, now headless XP Pro system.
It goes something like: rdesktop -u *username* -p *password* -a 16 -f -x b -r sound:local *remoteipaddress*

3D acceleration is not possible over remote desktop. VNC could allow this, and it'll transfer clipboard changes, but it'll probably be less responsive, and you'd get no audio. Also, I might just be unlucky, but I had to leave a wheel mouse plugged into the XP system to be able to use my mouse wheel over remote desktop.

---

### Post by JediPottsy on 2005-10-23
ahhh, using TightVNC :D works great. Can connect from any pc using web browser.

---

