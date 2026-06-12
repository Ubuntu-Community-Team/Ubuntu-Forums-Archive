---
title: "I can’t connect my vps using vnc sever"
date: 2018-06-27
forum: General Help
---

### Post by hunter94 on 2018-06-27
[FONT=Helvetica]i had tried everything to connect my vps usin vnc server but i didn’t succeed i don’t know why
i fllowed thes stips but it didn’y work
update
upgrade
install kde enviromnent
install tightvncsever[/FONT]
[FONT=Helvetica]and there is somthing else when i connect my vps with hostname using putty works but when i use vps ip i doesn’t work[/FONT]
[FONT=Helvetica]please is there anything i can do ?[/FONT]

---

### Post by TheFu on 2018-06-27
Welcome to the forums.

You shouldn't attempt to connect to VNC directly. Encryption of VNC, if there is any, is very poor.  That is a bad security issue.
Always use a VPN or ssh tunnel to connect to any VNC.

First, startup vnc-server with the -localhost option to prevent any connections except from the local machine.
Then use ssh to make a tunnel that can be used for VNC traffic. 
[https://crl.ucsd.edu/handbook/vnc/index.php](https://crl.ucsd.edu/handbook/vnc/index.php) looks like a reasonable how-to guide.

If you get tired of poor VNC performance, perhaps x2go, based on the NX protocol, which feels 2-3x faster than VNC, would be userful?  x2go has clients for all 3 main OSes and works really well.  ssh is part of the NX protocol, so your ssh-keys can be used to make authentication fast and more secure than with passwords.  Password-based authentication should be avoided over the internet. 

 I don't use KDE, but I know x2go works with lxde, xfce and openbox quite nicely.  Remote desktops really don't work well with heavy graphics systems that demand access to GPU hardware.  Years ago KDE was supported by x2go. I haven't looked since KDE went heavy-GPU.

---

### Post by hunter94 on 2018-06-27
thank you sir for your reply
but when i start vncserver every thing looks good but when i try to connect it via vncviewer it doesn't connect and provider specifics a port for me so i can-t use the port 5901 is there any way to include this port

---

### Post by TheFu on 2018-06-27
edit - removed link that might help bad-guys.

Could it be that someone else already hacked in?

---

### Post by hunter94 on 2018-06-27
no i don't think that is the problem
but why i cant connect to my server in putty using the port 22 
unless i use the port which my provider gave me and this port changes after every restart

---

### Post by hunter94 on 2018-06-27
no i don't think that is the problem
but why i cant connect to my server in putty using the port 22 
unless i use the port which my provider gave me and this port changes after every restart

---

### Post by TheFu on 2018-06-27
So, I'm unsure of your knowledge level.

Putty is an ssh client, so connecting on port 22/tcp is the default.  There will be thousands of attempted hacks an hour on that port, so definitely don't use passwords with it if you don't move it to a different port.

5901 is the standard VNC port.   5901- 5920 are expected to be VNC ports and will be scanned and attacked.  Hacking into VNC over the internet is extremely common.  I would be shocked if a good provided gave direct VNC access over the internet.  

If this is not on the internet, say so and that will help figure out the issue.

To  figure this out, please be extremely clear on what you've done, with special care about which system each step was performed.
How do you run the VNC server? Any log messages?  Just installing it is not enough.
Can you prove it is listening on the port you expect?  I would use netstat or lsof.
How do you connect to VNC?  Any errors or does it time-out?  Can you telnet to that port and see a connection header?
Could a router or firewall be blocking VNC connections?
Can you ssh into the machine?   The 1st post is about VNC and ssh seems to be working. Later posts say ssh isn't working anymore, huh?

It isn't clear, but is the ssh port moving around?  That would be strange, though not being on port 22/tcp would be good and common based on my experience.  I'm pretty good at getting ssh to work.  My troubleshooting steps: [http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)  It assumes Linux, not Windows.  I don't use Windows much and haven't used putty more than  1-2 times a year for over a decade.  Linux ssh clients have many more  features and are much easier to use than putty.

Hopefully, someone better with VNC will help. I used VNC only to learn it for a certification test, which required using an ssh tunnel, nothing more.  I use x2go daily, for many hours, and have used it from 5 continents.  x2go really is easier and because ssh-tunnels are built-in, more secure over any network.

---

### Post by hunter94 on 2018-06-27
i removed the thightvncserver and i am going to try with x2go 
my server system is ubuntu
i don't get errors while installing vnc but the problem is to connect my vnc server 
i am able to connect the server via putty using the hoste name but i can't connect using my ip why is that ?
now i am going to try X2go if it goona work 
and thanks again

---

### Post by hunter94 on 2018-06-27
Setting up x2goserver-printing (4.1.0.0-0~1517~ubuntu14.04.1) ...
Creating x2goprint group.
Adding group `x2goprint' (GID 110) ...
Done.
Creating x2goprint user.
Adding system user `x2goprint' (UID 105) ...
Adding new user `x2goprint' (UID 105) with group `x2goprint' ...
Creating home directory `/var/spool/x2goprint' ...
Setting up x2goserver-xsession (4.1.0.0-0~1517~ubuntu14.04.1) ...
Setting up systemd-services (204-5ubuntu20.28) ...
Setting up libpam-systemd:amd64 (204-5ubuntu20.28) ...
invoke-rc.d: unknown initscript, /etc/init.d/systemd-logind not found.
invoke-rc.d: policy-rc.d denied execution of start.
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
Processing triggers for initramfs-tools (0.103ubuntu4.4) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-151-generic
/usr/sbin/iucode_tool: cpuid kernel driver unavailable, cannot scan system processor signatures
Processing triggers for ureadahead (0.100.0-16) ...

is that means it installed successfully or not ?

---

### Post by TheFu on 2018-06-27
If you don't show the command, I can anyone possibly know if what you requested was reasonable or not?   If you didn't setup the PPA first, it is likely not what you want.

[https://www.howtoforge.com/tutorial/x2go-server-ubuntu-14-04/](https://www.howtoforge.com/tutorial/x2go-server-ubuntu-14-04/) is a tutorial for 14.04.  BTW, 14.04 really shoudn't be used on a new install without a really good reason. It has less than a year of support left.  At this point, 16.04 is the oldest release that should be used and 18.04 if you have time to troubleshoot new issues.

You can follow the x2go website instructions too, but the howtoforge is usually pretty clear and reasonable. But no instructions will include the security stuff you'll want.  [https://wiki.x2go.org/doku.php/doc:newtox2go](https://wiki.x2go.org/doku.php/doc:newtox2go) has an overview and installation instructions.

x2go only uses the ssh port, so ssh-keys should be used.  Until you get it working, disable printing and audio. Those require 2-way connections which often aren't possible.

In general, on Unix systems, failures are announced loudly and success isn't announced. Just because you asked the system to do something, that doesn't mean what you asked for was what you really intended.   When providing information here, it is best to show the command used AND the relevant output. This prevents misinterpreted facts.

And answering questions is important.  You've left me/us hanging on a bunch of questions. Hard to help.

---

