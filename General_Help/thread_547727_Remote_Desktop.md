---
title: "Remote Desktop"
date: 2007-09-10
forum: General Help
---

### Post by Stoodle on 2007-09-10
I can't figure out how to do remote desktop. I want to do remote desktop with my girlfriend. She's running feisty fawn and I have Edgy Eft. I went to System>preferences>remote Desktop and on her laptop, I chose remote login but it didn't work. I also tried doing it from terminal but it said it couldn't find a host. This is when she did it at my house. I would like to do remote desktop from her house to mine. Also, how can I do file sharing with her?

Sorry, I'm a noob at networking.

---

### Post by reckless2k2 on 2007-09-10
some things you will need to know will be

[LIST]
[*]opening ports in the router to the machine

[*]ip address of both of your computers WAN not LAN
[/LIST]

---

### Post by Stoodle on 2007-09-10
WAN is working access network, right? Not sure what that is but I'll look it up. I was trying to find our IP addresses but I don't know how to find them and I don't know how to find open ports. Wait, I think I do. Isn't there something in Ubuntu that allows you to ping others and port scan them?

---

### Post by qtrader on 2007-09-10
This link helped me on my setup. 

[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)




> **Stoodle said:**
> I can't figure out how to do remote desktop. I want to do remote desktop with my girlfriend. She's running feisty fawn and I have Edgy Eft. I went to System>preferences>remote Desktop and on her laptop, I chose remote login but it didn't work. I also tried doing it from terminal but it said it couldn't find a host. This is when she did it at my house. I would like to do remote desktop from her house to mine. Also, how can I do file sharing with her?

Sorry, I'm a noob at networking.

---

### Post by Stoodle on 2007-09-10
I'm still reading it but what are the security risks that go along with this?

---

### Post by reckless2k2 on 2007-09-10
you bring up a good point with security. also, we are talking about adding additional software and tweaking files like crazy to get this going on both sides. i don't think you want to do that. rdesktop can be run without jumping through all those hoops in that blog. if you are clueless about what a WAN and LAN are then it's going to take a little more to walk you through this. it's really not terribly difficult though. you can do this without adding anything additional through rdesktop. 

google "what's my ip" and click on that site. it'll tell you a series of numbers probably starting with 68.xx.xx.xx. You need that number for you and your girlfriend. 

also, you are going to need to share a little about both of your internet connections. like are they highspeed? what's the provider? what equipment do they have at your house (cable modem? dsl modem? etc)? do you have a router plugged into that highspeed modem?

the rdesktop part is easy. 

yes this is a security risk. opening anything to the internet is a security risk though. depending on what or how you are doing it can make it more secure than not. you can install some other easy program(s) that will make all of this more secure like fail2ban or denyhosts. Let's get through the rdesktop gimmick first.

---

### Post by Stoodle on 2007-09-10
I use AT&T and she uses adsli. I have DSL and I think she does too.

---

### Post by reckless2k2 on 2007-09-10
ok so that means you have a dsl modem somewhere in your places more than likely near you computers. do you each have a router as well? 

you should each do the what's my ip query so you have your IP. obviously don't post that ip address on this forum. 

let me know if you each have a router or are directly connected to your dsl modems. you may have a gateway that does both. you will have to find out that kind of information to be able to give us the correct answers about your network and her's. this is where you are forced to learn a little more than you might like. this is necessary though be able to communicate across the internet in this manner.

---

### Post by Stoodle on 2007-09-10
We're both using routers. I'm not sure what you mean by gateway. And yes, I do know what LAN is.
Don't worry, I'm eating up everything you say. I want to be a computer whiz when I grow up. That's one reason I got Linux. You can do ANYTHING as long as you know how.
I'm going to do the ip query later, but I'm glad I know to do it.

---

### Post by reckless2k2 on 2007-09-10
ok...so now you have to go to the gui admin page of your routers and find the port forwarding area. you will need to know the ip of YOUR machine in your lan.....192.168.x.x  whatever it may be. then you have to open the port on your router to the outside world to that ip address (your box) in your lan. she will have to do the same thing on her router for her ip of her box. 

it would help if you both have static ip addresses. you will need to know a little about networking but just a touch because you can use your existing settings now you are getting for the router. just lock them in. 

for instance if you are getting 192.168.0.100 from the router. let me know if you knwo what static routing is and how to do it in ubuntu.

---

### Post by bodhi.zazen on 2007-09-10
See these links :

[uwiki]VNC[/uwiki]

[uwiki]VNCOverSSH[/uwiki]

[uwiki]SSHHowto[/uwiki]

In general, go to your router, forward the relevant ports (5900) (This is the hardest part)

Now go here and get your IP address : [http://www.showip.com/](http://www.showip.com/)

OK, then following the default VPN (vino) enable desktop sharing and set a password 

[Like This](https://help.ubuntu.com/community/VNC#head-31c7221101aa284602683c8281cb8c4df609fa85)

Then connect with the command line :

vncviewer <ip>:0

where <ip> is the ip address above ;)

[Like this](https://help.ubuntu.com/community/VNC#head-ecd48e306032e5972c3288622990426f3e955f45)

=====

You can also make a connection via the -listen option 

[http://www.ubuntuforums.org/showthread.php?t=299489](http://www.ubuntuforums.org/showthread.php?t=299489)

If you do this second method, only one of you needs to be able to open a port ...

=====

Security is an issue, I would look at tunneling VNC over SSH or FreeNX

[uwiki]FreeNX[/uwiki]

(FreeNX is popular and fast, but I will admit I have not been able to set it up, but I am on Gutsy ...)

---

### Post by reckless2k2 on 2007-09-10
thanks for the hot tag bodhi.zazen. i'm sure he has enough info to be able to handle it now.

---

### Post by bodhi.zazen on 2007-09-10
> **reckless2k2 said:**
> thanks for the hot tag bodhi.zazen. i'm sure he has enough info to be able to handle it now.

LOL

I think I overwhelmed him ...

---

### Post by Stoodle on 2007-09-10
:confused:

I thought there was a less painful way to do this. Man, I've got a lot of reading to do...

---

### Post by bodhi.zazen on 2007-09-10
LOL

I know the feeling, but to be honest, it is a snap, just requires a little reading.

The hard part is forwarding your posts from your router >_<

The rest is all gui, with the exception of a single command in the terminal.

But, if you want to tunnel over ssh, well that takes a few steps more, and is a little harder ...

But IMO security is increased. If you go with ssh, check out securing ssh (let me know and I can give you a few more links if needed, let the first steps settle first ...)

---

### Post by reckless2k2 on 2007-09-11
i run X over ssh from linux box to linux box. i find it much easier and the most secure rather than jumping through all of these hoops. i find it easier but it is a few shell commands before the gui pops up.

Read through this if you are interested in X over ssh:

[http://ubuntuforums.org/showthread.php?t=544567](http://ubuntuforums.org/showthread.php?t=544567)

Read the whole thing through and it won't be hard to understand. You'll still need to open port 22 (ssh) on the router though and know her WAN IP.

---

### Post by Stoodle on 2007-09-23
I still don't really understand much of it but I typed vncviewer followed by the IP and then :0. That's X terminal right? I don't know but I put it there and it worked.

I had the problem of not being able to see everything on the bottom and right and the colors were a little messed up. Any suggestions?

---

### Post by bodhi.zazen on 2007-09-23
\o/

Sounds like the server resolution is higher then the client. You should have some scroll bars on the sides to scroll up/down and across the screen.

Options : Reduce the resolution on the server, run a different vnc server (like tightvnc). You can then start a session with a different resolution :

vncserver -geometry 1280x1024 -depth 24 :1

geometry = resolution
depth = color depth

Then connect with vncviewer, change to IP:1 (ie change the :0 to :1).

---

### Post by Stoodle on 2007-09-23
what would changing 0 to 1 do?

---

### Post by bodhi.zazen on 2007-09-24
Like all things *nix , x sessions are numbered starting with 0

If you use the default vnc server (vino) or x11vnc you must be logged into X on the server and you will share that desktop, or X session , :0 and use a port of 5900.

If you install tightvnc you can start a vncserver without running X. This session must not conflict with your X session, so :1. This uses port 5901 to connect.

So, when you use a vnc viewer, no the client you type in the ip_address:0 ... This is == ip_address:5900 and corresponds with the first X session you log in with GDM.

ip_address:1 == ip_address:5901 = first tightvnc session.

To make matters more confusing, vino ONLY uses :0 
Tightvnc useses anything BUT :0, so you can :2 , :3 ... :56 ; these correspond to :5902, :5903 ... :5956

That should be clear as mud :twisted:

---

### Post by flat4 on 2007-09-24
Good suggestions, I like the Remote desktop built into ubuntu. I want to know how to disable the notification that pops up when you log in from another computer.

---

