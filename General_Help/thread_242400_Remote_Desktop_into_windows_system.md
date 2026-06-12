---
title: "Remote Desktop into windows system"
date: 2006-08-23
forum: General Help
---

### Post by ezkim0x on 2006-08-23
what's the best program for this?

I've used krdc, it's alright.. but it makes the colors really crappy.

I tried downloading the remote desktop client for windows and run under wine, when I open it, it opens fine.. but when I start to type in the ip.. it just closes out.

do you know how to fix this? or another rdp client?

---

### Post by bswilson on 2006-08-23
You might want to try VNC Server.  There are several packages like vncserver, UltraVNC, TightVNC, and RealVNC.  I'm partial to [UltraVNC]("http://ultravnc.sourceforge.net/") myself.

---

### Post by transactionlogfiller on 2006-08-23
sudo aptitude install rdesktop

---

### Post by wjp.reg on 2006-08-23
TightVNC is easy to install and just works :D

---

### Post by funchords on 2006-08-23
> **transactionlogfiller said:**
> sudo aptitude install rdesktop

If connecting to XP Pro or Windows Server, then this gets my vote, too.  Works very nice and, unlike VNC, redirects sound and devices.  Remote Desktop Protocol also provides user/password authentication and encryption.

If connecting to XP Home, then TightVNC on the Home machine and vncviewer on the Linux box.  There is (generic) password security available.  Consider adding sshd, a VPN, or some such if you plan on connecting to this from outside of your LAN.

---

### Post by ezkim0x on 2006-08-23
I have UltraVNC installed and it's working fine. :)

---

### Post by rcmullins on 2007-05-02
This thread is a bit old, but I didn't want to start a new one.

I have been r emoting into MS 2003 server with XP for several years.  I have converted over to Ubuntu, and am having trouble remote-ing into the server.

I have tried rdesktop and Krdc, both have yielded the following error;

'The system cannot log you on due to the following error:
The RPC server is unavailable.  Please try again or consult your system administrator.'

Any advice?

---

### Post by rcmullins on 2007-05-02
Disregard question.  Serious bonehead I pulled.   Wrong IP.

---

