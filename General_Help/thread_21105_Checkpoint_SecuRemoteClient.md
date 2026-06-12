---
title: "Checkpoint SecuRemote/Client"
date: 2005-03-20
forum: General Help
---

### Post by cedricthegreat on 2005-03-20
Has anyone managed to get a client that can connect to Checkpoint Firewall-1 VPN ?
Something that is compatable to SecuRemote or SecureClient

This is one of the last hurdles before throwing out Windows

---

### Post by jaming on 2005-04-01
You might have a look at FreeS/wan [http://www.freeswan.org/](http://www.freeswan.org/) an Open Source VPN client.

more here: [http://www.freeswan.org/freeswan_trees/CURRENT-TREE/doc/interop.html#checkpoint](http://www.freeswan.org/freeswan_trees/CURRENT-TREE/doc/interop.html#checkpoint)

and check out: [http://www.openswan.com/](http://www.openswan.com/)

---

### Post by Ric_ on 2005-04-06
Has anyone got a working example of connecting using this?

---

### Post by rverrips on 2005-04-06
Oh yes!  

I need SecuRemote / SecureClient on Windows 'cause the firewall/vpn management at my company is outsourced and I can't use the openswan / freeswan setups 'cause I can't change the Checkpoint NG setup - All I have is a username, password and VPN ip-address.  I use those in Windows and all works fine.

Sadest of all, I only need the VPN to connect to the Citrix Servers, and I have a linux Citrix Client - If only I could run SecuRemote on Ubuntu I could drop the windows partition my laptop once and for all, and be aan Ubuntu only man!

Please help!

Thanks ...

---

### Post by Ric_ on 2005-04-07
The only way I have found around this so far is to have a windows box connect via secuRemote. Load putty up and ssh into an internal box and use port forwarding. The go to my linux box and work in a happy place.

I supose I could install exceed on the windows box and use X11 forwarding. This is not ideal though. 

Checkpoint have an old linux client its designed for redhat 7 and 8 i think. Would be great if some one with the skills could convert this and bring it upto date maybe even a .deb package! This would truely set ubuntu ahead of the competion.

---

### Post by bamarob on 2005-04-20
[QUOTE=Ric_]The only way I have found around this so far is to have a windows box connect via secuRemote. Load putty up and ssh into an internal box and use port forwarding. The go to my linux box and work in a happy place.

I supose I could install exceed on the windows box and use X11 forwarding. This is not ideal though. 

Checkpoint have an old linux client its designed for redhat 7 and 8 i think. Would be great if some one with the skills could convert this and bring it upto date maybe even a .deb package! This would truely set ubuntu ahead of the competion.[/QUOTE]

It would be awesome if someone produced a .deb with a working Debian/Ubuntu Checkpoint client.  Please keep me posted on any progress on this.  In the meantime, could you please provide a little more technical detail (a HOWTO, perhaps) on the work-around you describe above (windows box connect via secuRemote, load putty up and ssh into an internal box and use port forwarding)?  I occasionally work from home and am force to use WinXP to connect to the office.  Short of connecting directly from Debian, I'd love to be able to at least use Debian, even if I'm having to go through a WinXP box.

Thanks,

BamaRob

---

### Post by Ric_ on 2005-04-23
Ok its pretty easy stuff to do!

What you need

Linux box
Check point
Linux box with the VPN your connecting too (with SSH)

1. Install checkpoint and putty on the windows box. (I always use the latest snap shot dev of putty.)

2. Connect checkpoint to your VPN

3. Open up putty and configure a session to use ssh tunnels and port forwarding. For example I have port 22 forwarded to the machine i'm already connected too. Now in that section of config you can say local ports accept connections. so now port 22 on my windows box is configured to port forward to my linux box at work ;)

4. Connect putty to your work machine.

5. Go to your Hone Linux box and SSH -X <WINDOWS_IP>. BINGO you have a X tunnel into work. You could choose to forward ports all over the place for specific job. I have port 143 and 25 for e-mail forwarded to the M$ exchange servers at work. On my home linux box i just set up a mail account to connect to the windows IP on those ports and all is good.


Hope that helps. Feel free to mail me if you need some more help.

---

### Post by rverrips on 2005-05-14
[QUOTE=bamarob]It would be awesome if someone produced a .deb with a working Debian/Ubuntu Checkpoint client.  Please keep me posted on any progress on this.  In the meantime, could you please provide a little more technical detail (a HOWTO, perhaps) on the work-around you describe above (windows box connect via secuRemote, load putty up and ssh into an internal box and use port forwarding)?  I occasionally work from home and am force to use WinXP to connect to the office.  Short of connecting directly from Debian, I'd love to be able to at least use Debian, even if I'm having to go through a WinXP box.

Thanks,

BamaRob[/QUOTE]
 I agree, BamaRob, it would be AWSOME to have a .deb of SecuRemote - I'd even be willing to pay for it!

---

### Post by Ric_ on 2005-05-16
I wonder if we could raise a bounty for it?

---

### Post by chiefofthejojos on 2005-09-19
[QUOTE=Ric_]Ok its pretty easy stuff to do!

What you need

Linux box
Check point
Linux box with the VPN your connecting too (with SSH)

1. Install checkpoint and putty on the windows box. (I always use the latest snap shot dev of putty.)

2. Connect checkpoint to your VPN

3. Open up putty and configure a session to use ssh tunnels and port forwarding. For example I have port 22 forwarded to the machine i'm already connected too. Now in that section of config you can say local ports accept connections. so now port 22 on my windows box is configured to port forward to my linux box at work ;)

4. Connect putty to your work machine.

5. Go to your Hone Linux box and SSH -X <WINDOWS_IP>. BINGO you have a X tunnel into work. You could choose to forward ports all over the place for specific job. I have port 143 and 25 for e-mail forwarded to the M$ exchange servers at work. On my home linux box i just set up a mail account to connect to the windows IP on those ports and all is good.


Hope that helps. Feel free to mail me if you need some more help.[/QUOTE]


This is an acceptable solution for me at least for now.  But, if you could, I could use a little more detail.

I believe I understand the basic idea of port forwarding over ssh, because I was able to get an ssh tunnel into my work box using the command you specified (SSH -X <WINDOWS_IP>.  However, I would like to rdesktop into my computer at work (or vnc).  I tried to set up an ssh tunnel for port 3389 (I read that's the correct port) and connect using "rdesktop <WINDOWS_IP>" but it doesn't forward correctly.  Is there an option I need to pass to rdesktop like the "-X" that was passed to ssh?

If anyone could help me with this I would appreciate it very much.

---

### Post by Ric_ on 2005-09-21
In order to get to a windows machine on your work network, you must first SSH to a linux machine on the work network. For example,

1. Connect to Work using your windows machine and checkpoint.
2. Set up putty to ssh to your linux machine. In the port forwarding section set up port forwarding from local machine port XXXX to work windows IP on port 3389. Make sure your tick the section about allowing other machine to connect if your going to use a local linux box.
3. SSH to your linux machine at work.
4. Now rdesktop to your local windows machine on the local port you specified and wham you get fired off to windows network machine.

---

### Post by chiefofthejojos on 2005-10-09
Thank you Ric_!!  Your post helped me so much!  I kept playing with it after I got it working that way and now I've got a new way to connect without needing the intermediate windows box.
All you have to log is ssh into your home box from work, and configure the ssh client to forward a *remote* (home) port to a local (work) port.  As long as the ssh session doesn't time out, you're set.  Now I just need to figure out how to keep it from ever timing out. :)
Thanks again Ric_!

---

### Post by beow on 2005-10-31
I use autossh and ssh-agent from Cygwin on my windows box at work in order to do reverse port-forwarding of VNC to home. It works fine and you don't need to worry about loosing your tcp connection.

But this is not enough for me to quit using windows at my work laptop since the VPN has to work on the road also. The above solution is only good for connecting from your linux box at home.

So again, with a SecuRemote client for Ubuntu I could finally drop Windows, but not before. Have the same restriction as earlier in this thread, have only user name, password and Firewall-1 gateway, no possibility to change the VPN server.

---

### Post by andre16354 on 2007-05-28
Install Cygwin. It has a much smaller footprint than Exceed and sshd is in there as well...



> **Ric_ said:**
> The only way I have found around this so far is to have a windows box connect via secuRemote. Load putty up and ssh into an internal box and use port forwarding. The go to my linux box and work in a happy place.

I supose I could install exceed on the windows box and use X11 forwarding. This is not ideal though. 

Checkpoint have an old linux client its designed for redhat 7 and 8 i think. Would be great if some one with the skills could convert this and bring it upto date maybe even a .deb package! This would truely set ubuntu ahead of the competion.

---

### Post by idrinktoomuch on 2008-01-11
There may well be much more elegant solution than mine by now (and if so I'd love to know!) but an alternative to running a physical windows box and using ssh port forwarding is simply to run Windows in a VM using vmware etc.

I have a Windows 2003 server vm running and the securemote client runs on it just fine. (Actually its more stable than it is on a physical vista machine, so another big score for vista...)

Thanks

Andy

---

### Post by cider101 on 2008-01-13
I have some good news! 
A friend of mine patched Racoon to work with the hybrid-mode of the checkpoint firewall (login, passwd needed only). He did the work initially for OsX. We already compiled the code on Ubuntu and could successfuly establish a connection with the checkpoint firewall. In a week or so, he is going to release/publish the code somewhere (still trying to figure out what the best option will be). I'll post any news/results here. 

have fun

---

### Post by plink on 2008-01-13
Thanks in advance for this.  I just found a reference in Google to raccoon before I found your post but I'm not technical enough to prepare it for Ubuntu.

I'll keep my eyes on this thread and hope for the best!

---

### Post by dubcat on 2008-02-15
Any news on this front?  I'm having to run an entire install of virtualbox and windows xp just to get a vpn connection to my office :(  I've gotten lazy and I even use outlook running in there to talk to my exchange server.

---

### Post by tala on 2008-07-07
Has anyone tried this guide?
[http://lists.openswan.org/pipermail/users/2006-December/011397.html](http://lists.openswan.org/pipermail/users/2006-December/011397.html)

it sounds long and hard
i found this one:
[http://emsi.it.pl/auto/opensclienthowto](http://emsi.it.pl/auto/opensclienthowto)
i'll give it a go , and update here if it working well

---

