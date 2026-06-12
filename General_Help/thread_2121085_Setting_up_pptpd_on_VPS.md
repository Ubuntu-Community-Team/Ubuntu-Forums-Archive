---
title: "Setting up pptpd on VPS"
date: 2013-02-28
forum: General Help
---

### Post by thrasx on 2013-02-28
I am trying to setup a PPTP VPN server on my ubuntu minimal server 12.04 LTS hosted by linode

There are many instructions on doing this online, and I have looked through nearly all of them.  I was able to set this up successfully on my netbook on my home network.  

On my VPS server, I only have 1 available public IP address and 1 private IP address.  I can't figure out how to allocate IP addresses for pptpd to use, since I can't use my provider's router.

Is there some way I can create a virtual network interface and use it to assign IPs to my PPTP clients?

---

### Post by thrasx on 2013-02-28
This is from the syslog, maybe the issue isn't what I thought it was 

](*,)

> Mar  1 01:55:05 system pptpd[5019]: GRE: Bad checksum from pppd.
Mar  1 01:55:05 system pptpd[5019]: GRE: read(fd=7,buffer=8058520,len=8260) from network failed: status = -1 error = Protocol not available
Mar  1 01:55:05 system pptpd[5019]: CTRL: GRE read or PTY write failed (gre,pty)=(7,6)
Mar  1 01:55:05 system pptpd[5019]: CTRL: Reaping child PPP[5020]
Mar  1 01:55:05 system pppd[5020]: Hangup (SIGHUP)
Mar  1 01:55:05 system pppd[5020]: Modem hangup
Mar  1 01:55:05 system pppd[5020]: Connection terminated.
Mar  1 01:55:05 system pppd[5020]: Exit.
Mar  1 01:55:05 system pptpd[5019]: CTRL: Client 70.230.11.86 control connection finished
Mar  1 01:55:05 system pptpd[5019]: CTRL: Exiting now
Mar  1 01:55:05 system pptpd[5014]: MGR: Reaped child 5019

---

