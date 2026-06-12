---
title: "Lan - Ubuntu VPN Client --&gt; MS Exchange Server Shares"
date: 2012-10-31
forum: General Help
---

### Post by CrouxL on 2012-10-31
I have an Ubuntu Command Line Server, 12.04. It started out to be just a file server, with backup. 2 Weeks later I was informed that I need to setup a connection to Head Office, a Microsoft Exchange Server, to access shares. 
[ATTACH]226381[/ATTACH]  -- ADSL Router IP 10.0.1.254
From the local site, Windows workstations(WS) needs to connect to the shares on the MS Server. Outlook on the WS's also connects to the MS Exchange Server via internet. 
Within Windows, a VPN connection to MS Server is no problem, but then each WS needs to be connected. 

I want to setup just one VPN connection. (If possible)

I have setup my Ubuntu server, as a PPTP VPN client, to connect to the MS Server. I can ping both the MS Server IP and name from the Ubuntu Server.

I have created samba shares, mount points and cifs mounts on my Ubuntu Server, via the VPN tunnel. On the Ubuntu Server I can access the mount points and see all the files and I can access all the subfolders. From any WS, via the samba shares, I only have access to the files in the root of the share, all the subfolders are displayed as files with 0 size.

My routing works, but I might have to change the way it works (not sure what to do?). I disabled the firewall to check if that is not causing the problem. Even with the mounting and samba shares disabled, I cannot ping the MS Server IP, 10.0.0.2 from any WS. I have even added to the Windows Host file, on one of the WS pc's, "10.0.0.2 MSServerName". But that did not help either.

I have searched the internet and followed guidelines as well. [http://pptpclient.sourceforge.net/routing.phtml](http://pptpclient.sourceforge.net/routing.phtml)

Am I setting it up the wrong way?, Is there option that I am missing? Do I need to reconfigure my whole network layout?


Hope there is an answer form me out there
Thanks

---

### Post by shreepads on 2012-10-31
What permissions do you have on the subfolders, especially for the Samba daemon?

AFAIK the Win PCs on your LAN will never be able to directly ping the MS Exchange server in the manner you want, they're not part of the VPN connection setup.

Can you setup the VPN tunnel at the router level instead at both ends? Basically a VLAN..

---

### Post by CrouxL on 2012-10-31
Full read/write on the mount folders. With no mount, I can go mad in the samba shared folders. As soon as I add the cifs mount, I can only open/save docs in root of that folder. I can create a subfolder, but once created, it shows up as a file, 0 size.

Don't know VLAN, have not set it up before, will look it up on net when I get a chance.
Thanks, if you have more info, would appreciate it.

---

