---
title: "VNC stops working on server"
date: 2013-03-10
forum: General Help
---

### Post by 8301 on 2013-03-10
Hello

This is probably the weirdest problem I have encountered yet.

I use Ubuntu desktop as a server host to Virtualbox. I do not change Ubuntu more than that I install nfs , samba, ddclient (DNS software), ssh and Virtualbox. To access the host I need to have remote access to it. I connect to the host through VNC (Ubuntu desktop sharing software) because xRDP does not let me connect to the same session. After I had re-installed the system and checked that  samba and NFS shares, SSH, xRDP and VNC etc worked accordingly, connected to a screen, keyboard, lan-cable and mouse, it was time to move the server back to another room.

I connect the server to the same router (and even to the same router ports) with a longer lan-cable (both lan-cables are cat6) and start the server. Now when I try to connect to the server through VNC I receive the message "connection failed"...

The funny thing is that NFS and samba shares work as do rdp (but it opens another session). SSH does also work fine. The IP number is still the same and I can connect to the server with SSH externally.

I have by now re-installed the system 3 times and now are lubuntu installed with x11vnc and still the vnc connection only works when everything is standing beside the screen and when I move it to another location vnc fails.

I have tested other router ports and restarted the modem and router countless times.

So I am out ideas by now please help

Br.

---

### Post by steeldriver on 2013-03-10
when you connect via ssh, can you see that x11vnc is running and listening on the chosen port (default 5900)? can you see that the X server is running?

---

