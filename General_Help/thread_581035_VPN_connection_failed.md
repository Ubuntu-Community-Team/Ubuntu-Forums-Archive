---
title: "VPN connection failed"
date: 2007-10-19
forum: General Help
---

### Post by larini on 2007-10-19
Hi, after install Gutsy, my VPN (pptp) connection does not work anymore (I want to connect to my work VPN).
My configuration was exatly the same that was in feisty.

But always I get the error: VPN connection failed

---

### Post by larini on 2007-10-19
bump!

---

### Post by mahousaru on 2007-10-19
I am connecting to a MS gateway *spit* and it worked out of the box with a default gutsy settings for me.  But with OpenSuSE it failed until I checked Refuse EAP in the authentication section.  In case it helps, my settings are:

Authentication
All unticked apart from 
Refuse EAP

Compression and Encryption
All unticked apart from 
Require 128 bit MPPE encryption
Enable stateful MPPE

---

### Post by larini on 2007-10-19
thanks! I will try this later, at home.

---

### Post by luvdemheels on 2007-10-19
I think this is a bug. I have a 6.06 LTS laptop that can connect via vpn just fine BUT my 7.10 gutsy machine cannot connect with the exact same config. :(

---

### Post by frenchcr on 2007-10-21
everytime you upgrade your kernel you need to reinstall vpn client

see my post below for gutsy cisco vpn fix

[http://ubuntuforums.org/showthread.php?t=581217&highlight=vpn+gutsy]("http://ubuntuforums.org/showthread.php?t=581217&highlight=vpn+gutsy")

---

### Post by nmsa on 2008-01-30
> **luvdemheels said:**
> I think this is a bug. I have a 6.06 LTS laptop that can connect via vpn just fine BUT my 7.10 gutsy machine cannot connect with the exact same config. :(

same problem here.
I have both the sever and the client on the same network

---

### Post by buggs187 on 2008-03-21
Same problem here. On a windows box the VPN works and with the same settings on 7.10 they don't..... Any help ????

---

