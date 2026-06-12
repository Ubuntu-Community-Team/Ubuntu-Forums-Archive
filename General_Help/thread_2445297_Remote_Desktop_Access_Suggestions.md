---
title: "Remote Desktop Access Suggestions?"
date: 2020-06-11
forum: General Help
---

### Post by rsteinmetz70112 on 2020-06-11
As a result of recent events I find I need to have a remote access to Windows desktop for administration. I would like to be able to access my Linux servers as well. What tools are available for Linux to accomplish that? It needs to be secure and to preform reasonably.

---

### Post by TheFu on 2020-06-11
I don't know of any secure methods to access Windows remotely from Linux without using a VPN. None of the RDP or VNC tools are secure enough for use over the internet without some network security added on. That's either an ssh tunnel or VPN running between where you are and where the other Windows machine is located.

Windows to Windows connections aren't secure enough for over-the-internet connections in this way either. Don't believe the claims.  People have their RDP and remote VNC connections hacked **all the time**. Clearly the security provided is not sufficient.

What I do when away from home, and I need to access a Windows system there, is to use x2go to connect to a Linux desktop at home, then use RDP from that Linux machine into the Windows machine running on the same LAN. It is sorta like Inception with a remote desktop running inside a remote desktop.  x2go provides the secure ssh tunnel from the hotel to the house, so that part is properly secured.

If you are willing to trust a 3rd party (why?!), then you might look at TeamViewer.  Someone else would need to speak towards that.  Just be 100% certain that you trust that company and that any credentials used aren't trivial.  You should probably have the other person set a password that you choose which is long and complex enough to not be hacked in a year of attempts.  I'd use a password manager to create a random password at least 30 characters long. It isn't like I'll ever be typing it, right?

---

### Post by HermanAB on 2020-06-12
I have tried many different methods over the years, but mostly, I just use SSH.  Nowadays, even Windows has SSH.  It is a Swiss knife and can do anything if you would bother to read the online book and some howto guides.

---

### Post by ActionParsnip on 2020-06-12
What are you wanting to do on the servers when you get connected? What is the purpose of the connection? What will you be doing on the remote systems once connected, exactly?

---

### Post by rsteinmetz70112 on 2020-06-12
I have two potential uses in mind - administration of the Windows machines and allowing employees to access their work desktops to work remotely. I currently mostly use ssh on the Linux servers for remote administration but I sometime need a Windows desktop to see what the user sees.

---

### Post by TheFu on 2020-06-12
> **rsteinmetz70112 said:**
> I have two potential uses in mind - administration of the Windows machines and allowing employees to access their work desktops to work remotely. I currently mostly use ssh on the Linux servers for remote administration but I sometime need a Windows desktop to see what the user sees.

If employee access is to be provided, then only setup a VPN.  Require the VPN be used to get inside.

For remote desktop working, most non-trivial companies deploy a windows terminal server using some sort of ICA through the VPN they use.

But the first thing needed is a VPN. It is probably worth paying for a commercial openvpn license to make VPN certificate management easier.  You might want to require a Yubikey device for added authentication to the VPN.  [https://developers.yubico.com/yubico-pam/YubiKey_and_OpenVPN_via_PAM.html](https://developers.yubico.com/yubico-pam/YubiKey_and_OpenVPN_via_PAM.html)

If it were me, I'd look at NOT having Windows desktops deployed and switch to a clustered KVM VM deployment for Windows access.  Doing that and having daily snapshots means should anything really bad happen, it is 2 minutes to step back to when the snapshot was created and still be able to work.  With sufficient storage, having 4 snapshots a day between when the daily backups are taken can handle most non-storage failures.

I've deployed VPNs for 25K employees. There are all sorts of details necessary. We didn't do remote desktops. Instead it was decided that laptops would be more cost effective for our needs. In that environment, very little work data was actually stored on the desktop systems. The workflow between different groups all used a project management server that all team members had access where tracking, issues, documents, were stored. This project server was professionally maintained and backed up. It had a web interface, so any client could be used.  At my next job, we deployed the same project management server and allowed our clients to have read-only access to their project(s).  

We used redmine, a F/LOSS solution.  It works for software or building a house from a project management standpoint. 

Anyways - setup the vpn first.

---

