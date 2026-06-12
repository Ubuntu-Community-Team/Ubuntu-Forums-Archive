---
title: "Vncviewer - not accepting input"
date: 2007-12-21
forum: General Help
---

### Post by RudolfMDLT on 2007-12-21
Hi there,

When I run vncviewer or xvnc4viewer I get presented with a popup that requires me to enter a server IP. The input box doesn't accept my keyboard input. I can click the buttons but I can't type anything?? when I run the command "vncviewer 10.0.0.1" I get the password prompt and then I'm stuck again! I can't type the darn password?

Thanks for any help!

Rudolf

---

### Post by taenus on 2007-12-22
For what it's worth, I'm getting this too.  It worked find before a Gutsy upgrade and subsiquent reinstall.

---

### Post by RudolfMDLT on 2008-01-08
bump... 

Is anybody els getting this? Does YOUR vnc viewer work?

thanks,

Rudolf

---

### Post by fragos on 2008-01-08
I'm assuming you already set the remote to accept vnc.  The "Remote Desktop" preferences on the target machine.  My remote is all on a local wirelesss network.  this allows me to use host names instead of IPs.  For example my remote has hostname "dell" and I use the following command "vncviewer dell.local." (both "."s are required).

---

### Post by RudolfMDLT on 2008-01-10
My Problem is not connecting to the machines - though I appreciate the fact that you can type in names instead of IP's. My problem is that I can't type in the password for the machine that I am remoteing to!

When you type the command 

"vncviewer dell.local."

and press [enter] you get a password prompt? Is it text base or is it a little dialog box?

I get a dialog box that doesn't accept keyboard input.

Thanks for the reply!

Rudolf

---

### Post by fragos on 2008-01-10
I would get a dialog box but don't use the login.  You can require the remote to grant permission.  I use that when I help clients over the Internet.  Within my LAN I don't require security since I'm the only user with multiple boxes.

---

### Post by Tobbera on 2008-03-10
Same problem here after upgrade.

---

### Post by fragos on 2008-03-10
For some reason, using {host}.local. doesn't seem to work anymore.  I've returned to using the IP when addressing the other box.  An extra note on what IP is assigned by DCHP.  in the DCHP process, your box will first try to use the last IP it was assigned.  Therefore if you connect to multiple networks the highest numerical IP ever used will your default for all networks that are configured to use the same NAT range of addresses.  Many routers use 192.168.1.n but I've also seeen 192.168.0.n and in fact the NAT IP range is configurable on the router.

---

