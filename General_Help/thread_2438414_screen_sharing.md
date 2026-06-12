---
title: "screen sharing?"
date: 2020-03-11
forum: General Help
---

### Post by hmiersch on 2020-03-11
Hi.
I have a PC, a laptop and a raspberry pi 4, all running Ubuntu 19.10 (yes, I installed a GUI on the pi). Now I want to share the pi's desktop with the other 2 (and preferably between the computers too). So I turned on screen sharing in the control panel on one computer and tried to connect to it from the other one using remmina but all attempts failed. A youtube video mentioned that i have to turn off encryption. But turning off encryption is simply not an option. 

So what can I do? 
Is there any software that lets me use screen sharing with encryption enabled?

---

### Post by TheFu on 2020-03-11
ssh -X user@pi4  /path/to/program

---

### Post by hmiersch on 2020-03-11
I was talking about screen sharing, not ssh.

---

### Post by TheFu on 2020-03-12
> **hmiersch said:**
> I was talking about screen sharing, not ssh.

Remote X11 will display almost all applications running on a remote system to the local machine.  Using ssh w/ X11 tunnelling just makes it easier.  I use this method every day, all day, to run programs on other systems, but display the window on my current desktop.  That's what the provided command accomplishes.

Another secure method, x2go, doesn't work on ARM platforms. It also uses ssh tunnels. Not all programs have been ported to ARM architectures.

I suppose VNC would work, but because the security for that protocol is so very bad, using ether an ssh-tunnel or full VPN needs to be mandatory.  VNC servers should only run a listener on the localhost interface, never any LAN or WAN IP.

If you just want pure read-only sharing with other systems, any of the 500 WebRTC solutions can work.  Zero security.

In theory, the Gnome3 Desktop Sharing included w/ 19.10 should be production ready.  That's the theory.  Then there is reality.
[https://help.gnome.org/users/gnome-help/stable/sharing-desktop.html.en](https://help.gnome.org/users/gnome-help/stable/sharing-desktop.html.en)   
> Currently only remote **passwordless** **unencrypted** VNC access to an existing session is supported.
which tells me all I need to know.  Avoid.

Which brings me back to the solution already posted, using remote X11.
```
ssh -X user@pi4 /path/to/program 
```

---

### Post by hmiersch on 2020-03-12
Now that you put it that way, I think it's worth a try. I'll give it a go when I get home...

---

### Post by HermanAB on 2020-03-12
IMHO, remoting a whole desktop, just to overwrite it with an application, is a waste of electrons.  Just remote the application using SSH -X as shown above.

---

### Post by TheFu on 2020-03-12
> **HermanAB said:**
> IMHO, remoting a whole desktop, just to overwrite it with an application, is a waste of electrons.  Just remote the application using SSH -X as shown above.

Really depends on the available bandwidth, IME.  Remote X11 only works well when the systems are connected by 100 Mbps or faster connections.  I generally don't have that bandwidth outside the building, so an efficient NX connection like x2go (with proper tuned settings) really becomes necessary.  The lack of an ARM port for any NX means I've never used ARM systems in that way, but connecting into the LAN where the ARM system is located using an NX/x2go connection, then using remote X11 for the last hop does work.  I also will make the last hop into a Windows RDP session after handling the remote x2go connection  between 2 x86 Linux desktops.

But remote X11 doesn't "share" any desktop or application.  It is a 1-client-to-1-server connection.  OTOH, x2go does support a 1-to-many-viewers capability, but alas - not with ARM CPUs.

For text stuff, tmux and screen can share a terminal with multiple users over ssh, so I've heard.

Until  hmiersch tries something, not much more to be answered.

---

### Post by hmiersch on 2020-03-12
well, i tried it and it didn't work. first i tried to use the hostname, but that got me error messages. so i started using the IP address instead, and that eliminated the error messages. but it still doesn't work. i entered   ssh -X harry@192.168.1.10 /usr/bin/firefox   but then nothing happened. no disk activity on the PC, no new window, no error messages, no nothing.  i tried the terminal too, with the same result. checking firewall settings now...

---

### Post by hmiersch on 2020-03-12
a question about UFW: when a connection is initiated, and it allows the packets to go out, does it automatically allow the response packets in or do i need another rule for that?

---

### Post by HermanAB on 2020-03-12
Note that for X forwarding to work over SSH, two things are required:
a. ssh must be running on the target
b. Xorg must be installed on both machines (not Wayland)

Test ssh with:
$ ssh -vvv user@ipaddress

Fix that first, before trying forwarding - one thing at a time.

---

### Post by TheFu on 2020-03-12
Troubleshooting ssh Connections: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)
ssh has to work before X11 forwarding can work.  
Name resolution may or may not work.  You can fix it, if you like, or ignore it using either the IP address or by setting up a ~/.ssh/config file that hides the IP from all your commands.  Whatever you like.

---

### Post by hmiersch on 2020-03-12
I'll check that when I get home.

---

### Post by TheFu on 2020-03-13
> **hmiersch said:**
> I'll check that when I get home.

Hopefully, the ssh server is installed on the remote system and ssh client (CLI version) is installed on the client.  The server needs to have the ssh-port used allowed through those firewall(s).  Most clients allow outbound connections.

If you think there is a firewall problem, please explain the networking between the 2 systems.  On the same LAN, usually means only the remote system firewall might be an issue.  Obviously, if going over the internet, there will be other considerations.

---

### Post by HermanAB on 2020-03-14
Debug tip:
Test ssh on the SAME computer first.  Only if that works, try it from a different networked computer:
$ ssh localhost

If the above doesn't work, then there is absolutely no way that it will work from another networked computer - so fix this problem first.

---

