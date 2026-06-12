---
title: "Activate Remote Desktop from the Command Line"
date: 2007-11-21
forum: General Help
---

### Post by btrichardson on 2007-11-21
Hello all,

I'm currently away from my desktop machine running Ubuntu 7.10.  I can access it via SSH, but I did not activate the Remote Desktop option in System --> Preferences --> Remote Desktop before leaving my office.  I'm needing to access some GUI apps on my desktop, so I'm curious as to if I can activate the Remote Desktop functionality via the command line.  I know I could install vncserver using aptitude and such, but I'm trying to avoid installing software that I don't really need since the Remote Desktop functionality is already there, just not activated.

Does anyone know of a way to activate the Remote Desktop option via the command line in such a way that would be similar to activating it using the System --> Preferences --> Remote Desktop method?

Thanks in advance!!!

---

### Post by acti0nman on 2007-11-21
This should get you going.
vino-session --help
vino-preferences --help

---

### Post by scorp123 on 2007-11-21
> **btrichardson said:**
>  Does anyone know of a way to activate the Remote Desktop option via the command line in such a way that would be similar to activating it using the System --> Preferences --> Remote Desktop method? Login to your machine with the "ssh -X" option so that X11 forwarding is enabled ... You will need it to modify the preferences. Test it e.g. by executing something harmless such as "xclock". If you get a clock then everything is OK .... As for activating the remote desktop via command line: What you need is this:  **vino-preferences**

- enable it
- define a password
- but do NOT enable the option to "ask for confirmation". Because that means that a dialogue window would pop up locally on the screen and ask the user sitting in front of the PC for confirmation if the connection is allowed now or not ... If there is nobody in front of the PC, then nobody will be able to click on that "Yes" button and the connection will never be established. So you'll have to leave that option away.

---

### Post by btrichardson on 2007-11-21
That's awesome!!!  I never knew you could forward X11 stuff through ssh.  I knew vino-preferences was what I needed, but I figured I couldn't run it since it was a GUI.  Thanks for the help, as it worked perfectly!!!

Thanks again!

---

### Post by scorp123 on 2007-11-21
> **btrichardson said:**
>  I never knew you could forward X11 stuff through ssh. As a matter of fact you can pretty much tunnel *anything* through SSH if you do it right :) ...  Forwarding X11 via SSH is just one of the built-in defaults that can be activated via its own command line switch; but SSH offers many more interesting possibilities. :)

---

### Post by btrichardson on 2007-11-21
Yeah, I'm starting to figure that out!  I just noticed that vncviewer comes with its own switch, -via, that takes the work out of setting up SSH port forwarding.  Keeps me from having to do the whole -L <port>:<addr>:<port> thing.

Pretty cool!

---

### Post by vol_freak on 2007-11-21
> **scorp123 said:**
> As a matter of fact you can pretty much tunnel *anything* through SSH if you do it right :) ...  Forwarding X11 via SSH is just one of the built-in defaults that can be activated via its own command line switch; but SSH offers many more interesting possibilities. :)

Can you tunnel through 2ssh connections? What I mean is, could you use putty on a xp machine at work to log into a ssh server on your home network and then use vnc or nx to access a laptop inside your network? I've been thinking on this one for a while and can't seem to get a grasp on it. I'm dying to figure out how to access that laptop inside the network and I only have access to one port at work so I can't just run a separate ssh server on the laptop and have my router forward the traffic.

---

### Post by scorp123 on 2007-11-21
> **vol_freak said:**
> Can you tunnel through 2ssh connections?  Short answer: Yes, of course.

Long answer: What you seem to want is SSH tunnelling? Or maybe even a full-blown VPN? Let's take these topics apart ....

_**VPN:**_
I'd recommend **OpenVPN**. The server side is a bit tricky to configure (involves the command line and then a lot!) but there are some good tutorials out there that will get you started. Once you're done the server side configuring the client-side is very very easy (just "point and click" on pretty much every OS: just fill the few values you need, let your client load the cryptographic certificate files and you're done). Why I recommend this: an OpenVPN connection looks like "normal" SSL-encrypted traffic (e.g. HTTPS?) to anyone watching the IP packets (e.g. network adminstrators, intrusion detection systems, etc.) and such packets are usually allowed to leave most networks (e.g. work, school, university, etc.). So usually it's not a problem to establish a connection. The advantage with a full VPN is that you don't need to bother with tunnels and such things ... it's like you were actually there plugged in to the network directly (hence the term "virtual" private network ...). Take a look at these tutorials:
[http://www.thebakershome.net/?q=node/56](http://www.thebakershome.net/?q=node/56)
[http://www.techimo.com/forum/showthread.php?t=176687](http://www.techimo.com/forum/showthread.php?t=176687)


_**SSH Tunnelling**_
This one is probably easier to setup (you only need to have a server that is accepting SSH connections .... anything else can be done from the client side with one single command line!) but harder to understand at first. In your posting you talked about connecting from work to your home PC and from there to another system .... Yes, this can be done. I'd recommend some reading first: ```
man ssh
``` ... Jump to the section where it explains the "**[COLOR="Red"]-L[/COLOR]**" parameter and what it is used for. You will need that. You may also want to read these pages:

"Tunneling connections securely with SSH"
[http://www.debian-administration.org/articles/38](http://www.debian-administration.org/articles/38)

"SSH dynamic port forwarding with SOCKS"
[http://www.debian-administration.org/articles/449](http://www.debian-administration.org/articles/449)

"A couple of tricks with the secure shell"
[http://www.debian-administration.org/articles/438](http://www.debian-administration.org/articles/438)


To make it short again, here a coloured example that I indeed do use to tunnel VNC via SSH:
```
ssh -2 -C -c blowfish-cbc -p 8443 **[COLOR="Red"]-L 5810:[/COLOR][COLOR="Green"]192.168.1.211:5800[/COLOR] [COLOR="Red"]-L 5910:[/COLOR][COLOR="Green"]192.168.1.211:5900[/COLOR]** myusername@myremote.server.somewhere.net
```
What these parameters do:
-2: we explicitly want a SSH v.2 connection, not the now insecure v.1 of the protocol
-C: we want compression
-c blowfish-cbc: we want to use "Blowfish" as cryptographic method. It's very very fast but still considered very secure. This is nice to keep the overhead from encrypting the traffic as low as possible.
-p 8443: TCP port on the remote side (e.g. where the SSH server will be listening ... or from which port the firewall is forwarding SSH traffic from to your internal host)

Now the interesting parts:

... in Red:
"[COLOR="Red"]-L 5810:[/COLOR]" and "[COLOR="Red"]-L 5910:[/COLOR]" ... These are the TCP port numbers the tunnel entrance will have on **_our_** side of the tunnel. In other words: I connect to those tunnels on my local machine (= [COLOR="Red"]localhost:5810[/COLOR]) and I end up here .... (green parts):

[B][COLOR="Green"]192.168.1.211:5800
192.168.1.211:5900[/COLOR][/B]

(as anyone familiar with VNC will easily recognise I am forwarding VNC over SSH here ....)

So when I tell my vncviewer to connect to **localhost:5910** it will in fact go through the tunnel, pass through "**myremote.server.somewhere.net**" (where I logged in via SSH) and once inside my home network connect to my internal machine which has a 192.168.1.x address.

You can pack as many "-L:localport:RemoteTunnelHost:remoteport" parameters in one single "ssh" command line as you wish, even to different internal hosts (the machine you logged into would then act as some kind of router through which all traffic would have to pass). It will work for as long as there is something (e.g. a network daemon) actually listening on the ports you specify (e.g. in my case it would be useless to try to tunnel a VNC session trhough SSH if there were not a VNC session actually listening for connections).

The point is: Yes, you can also use port 22 (= SSH connection) there and thus with one single SSH login connect to multiple hosts at the same time.

But then again: Depending on how many hosts you want at the same time it may be better to forget about SSH tunnelling and start thinking about using something like OpenVPN where with one single connection you'd see all your internal network as if you were actually sitting at home.

Hope this was helpful.

---

### Post by rabbit20 on 2008-03-13
hmm tried to use putty to forward the x commands but i get rejected...trying to go from school (windows) to my server (ubuntu)

---

### Post by scorp123 on 2008-03-14
> **rabbit20 said:**
> hmm tried to use putty to forward the x commands but i get rejected...trying to go from school (windows) to my server (ubuntu) And you are sure you have a X server running on Windows?

---

