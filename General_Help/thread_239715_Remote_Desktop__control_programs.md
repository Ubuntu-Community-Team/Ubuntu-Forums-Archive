---
title: "Remote Desktop / control programs"
date: 2006-08-19
forum: General Help
---

### Post by WrathofthePenguin on 2006-08-19
I'm moving a couple of relatives to Ubuntu, and I'm looking for remote control/desktop options.  I'm constantly doing technical support (which is one reason I'd love to have them all move to Ubuntu) and I know I'll have to do some remote work at some point. I've used a couple of different options in the past, but what I really want to do here is make things as simple as possible. VNC (through a VPN tunnel) is probably what I'll end up doing (due to NAT being used on so many home routers). While it may be the best solution in my particular situation, I wanted to see what other users have used and what their thoughts are on the pros and cons of each.

My thoughts:

VNC pros: relatively simple to use, seems to work at a decent speed.
VNC cons: no default encryption, requires use of VPN or SSH

I've used Exceed in the past, but I'm looking for free options.

Ideally, I'd like a remote login similar to Windows remote desktop, rather than taking control of an existing session, but I'm not opposed to looking at all options, especially in light of the fact that most times I'd have to have them tunnel into my network due to NAT being used on their home routers.

Please help me with suggestions, experiences, pros and cons.

Thanks!

---

### Post by Patrick-Ruff on 2006-08-19
VNC has always worked well with me, however I've only used it on a networked setup, not remotely. VNC does have security options, in system, preferences, remote desktop you can set all kinds of security fetures and such. password protection AND prompting the user when someone attempts to control. over all, ubuntu's built in VNC works VERY well. I'de stick with that if I were you :).

good luck

---

### Post by scxtt on 2006-08-19
i "remote" VNC all the time - it's a breeze ... i just use the **vncserver** package in the repos, and upon 1st usage it has me create a password ...

as for creating session instead of 'viewing' existing ones, that's a breeze too ... you just ssh into a box, type **vncserver** and it'll create as many session for you as you want (or the box can handle -- :1. :2, :3, etc.) ...

---

### Post by bensexson on 2006-08-19
I prefer to use ssh with the -X flag to redirect X windows.  You should be able to do most troubleshooting from the command line and open X windows on your X server for GUI apps.

---

### Post by Patrick-Ruff on 2006-08-19
I thought VNC was in Ubuntu by default? it was merely a matter of going into System -> Preferences -> Remote Desktop and enabling it.

---

### Post by scxtt on 2006-08-19
that's vino, which is an easy way to share your :0 session ...

---

### Post by Patrick-Ruff on 2006-08-19
hmm that's odd, I was able to use the command vncviewer on my ubuntu setup, I don't recall installing it either.

---

### Post by scxtt on 2006-08-19
viewer is installed by default, server isn't ...

---

### Post by Patrick-Ruff on 2006-08-19
oh ic. well it appears whatever it has on it by default that acts like a server works perfectly. allow's password protection and a prompt before someone controls your computer, seems secure enough to me :).

---

### Post by scxtt on 2006-08-19
right, but it's only useful for an "already logged in" session ...

it's more of a "hey, can you take a look at this" scenario instead of a "i want to get a GUI on a box" {independent of any other users of the box} ...

---

### Post by WrathofthePenguin on 2006-08-20
> **Patrick-Ruff said:**
> oh ic. well it appears whatever it has on it by default that acts like a server works perfectly. allow's password protection and a prompt before someone controls your computer, seems secure enough to me :).

"Secure enough" is not enough for me. I'll have to check with the version included with Ubuntu, but I wouldn't be surprised if the password you entered in VNC is sent in the clear (like FTP or telnet).

As for the use of SSH -X, I'd have to do some port forwarding, and since the home router would be across the country, that might be more work than it's worth. It would actually be easier (and more secure) to have them tunnel into my network here.

---

### Post by ProjectGod on 2006-08-21
could you explain further the setup you have? are the relatives going to establish VPN to your (windows?) vpn server? if so VNC over the tunnel is fine. 

however establishing a PPTP tunnel from ubuntu is pretty tricky, i havent been able to do so myself. 

if on the other hand you want to connect remotely to relative homes (box to box) without any underlying tunnel. try using VNC over SSH. that too requires  installation and configuration of a virtual SSH server. 

freesshd (windows ssh server - freeware).

---

### Post by WrathofthePenguin on 2006-08-21
> **ProjectGod said:**
> could you explain further the setup you have? are the relatives going to establish VPN to your (windows?) vpn server? if so VNC over the tunnel is fine. 

however establishing a PPTP tunnel from ubuntu is pretty tricky, i havent been able to do so myself. 

if on the other hand you want to connect remotely to relative homes (box to box) without any underlying tunnel. try using VNC over SSH. that too requires  installation and configuration of a virtual SSH server. 

freesshd (windows ssh server - freeware).

I'd be using an IPSEC tunnel to a Contivity at my home. I'm not concerned at all with the tunnel setup. My only concern with using VNC over SSH is what I mentioned before. I'll be the one to initiate the session in that case and I'd have to have configured forwarding on their home router in advance, which could be problematic.

---

### Post by btdown on 2006-08-21
Why dont you use FreeNX? Best solution I've used yet. Extremely fast, and uses ssh.

---

### Post by Patrick-Ruff on 2006-08-21
FreeNX eh? link please? I'll have to try that one out as well :).

---

