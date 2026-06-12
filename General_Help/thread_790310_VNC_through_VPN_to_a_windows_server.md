---
title: "VNC through VPN to a windows server"
date: 2008-05-11
forum: General Help
---

### Post by waspinator on 2008-05-11
Hi,

I'm trying to connect to a windows server with VNC through VPN. I have already installed the PPTP thing for network configuration tool, and can connect using the IP address to my office. Unfortunately thats where my luck ran out. I don't know how to access any computers on my network. I have tried remote desktop viewer, but it can't find any computers.

This is one of the many make-or-break things my company needs in order to switch. I hope there is any easy way to do this. On windows all I do is enter my destination computer name in 'Remote Desktop Viewer' or in Start->Run and I can access my remote computers.

Thanks,

Waspinator

---

### Post by Monicker on 2008-05-11
What version of Ubuntu are you running? On 7.10 I just go to Applications -> Terminal Server Client, and have no problems connecting to Windows servers at work over our vpn.  I can't remember if its in the same place on 8.04, but I know I also connected to Windows machines from 8.04 with no problem.

---

### Post by waspinator on 2008-05-11
> **Monicker said:**
> What version of Ubuntu are you running? On 7.10 I just go to Applications -> Terminal Server Client, and have no problems connecting to Windows servers at work over our vpn.  I can't remember if its in the same place on 8.04, but I know I also connected to Windows machines from 8.04 with no problem.

I'm using 8.04. Whats the difference between 'Remote Desktop Viewer' and 'Terminal Server Client'?

Lets say I want to connect to a computer named 'server' after I have used network manager to connect to the VPN. No matter what I enter it says it can't resolve the host name. I'm probably doing something stupid.

I would appreciate any help.

Thanks,

Waspinator

---

### Post by Monicker on 2008-05-11
I believe Remote Desktop Viewer is just for connecting to VNC servers.  The Terminal Server Client uses RDP, which is the technology Microsoft licensed from Citrix and integrated into Windows.

There may be an issue with DNS resolution if you can't connect to your servers by name.  If you happen to know the ip address for one of them, you could enter that and see if it works for you.

---

### Post by waspinator on 2008-05-27
I tried using the IP, but I still couldn't get it to work. I read somewhere about routing tables? I'm not sure what to do with those, so if anyone could please help me out with that. Also it would be good to be able to access remote shares somehow.

I really want to use ubuntu for work, but until I can get this to work, I have to stick to windows :(

Thanks,
Waspinator

---

