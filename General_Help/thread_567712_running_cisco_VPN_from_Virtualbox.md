---
title: "running cisco VPN from Virtualbox"
date: 2007-10-04
forum: General Help
---

### Post by kolibri on 2007-10-04
Problem:  I cannot get my VPN client to connect to a remote network while running it in Virtualbox, Ubuntu Feisty host.

My company provides a modified Cisco VPN client for me to connect remotely to their network.  The linux/unix version they provide doesn't work with Ubuntu apparently-it won't install.  While I'm trying to fix that, I'm trying to run their windows version in VirtualBox.  I have the VPN client installed in Virtualbox. 

I cannot connect to the remote network.  The error I get is "remote peer is no longer respondin"  (it never responded).

I also cannot ping a network computer out of virtualbox, so I believe the problem is that the VPN client is not able to utilize the ports in my host computer.  Internet in Virtualbox works fine, no firewall is running in the VIrtualbox.

If my supposition about needing a port connection between Virtualbox and Ubuntu is correct, how do i go about making that happen?

---

### Post by Dirk_DC on 2007-10-07
With the Cisco VPN client they usually block access to your local network once connected.
I am using vpnc, the open source cisco VPN client, this way I am not restricted from accessing my local network. I can even set my routes and DNS servers the way I want.
You will need to decrypt the shared secret supplied in the config from your company, but there are plenty of online decrypting tools available.

---

