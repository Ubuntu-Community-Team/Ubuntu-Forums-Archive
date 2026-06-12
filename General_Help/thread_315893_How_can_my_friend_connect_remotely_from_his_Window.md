---
title: "How can my friend connect remotely from his Windows XP  to my UBUNTU?"
date: 2006-12-09
forum: General Help
---

### Post by UltraSonicSite on 2006-12-09
We're both total newbies on the subject. I told him to install Putty and type in my IP in the first box and click ok and nothing happens. I have set up Ubuntu to accept remote connections. Other than that, no Idea. Any help?

---

### Post by cptjaben on 2006-12-09
I don't really know if this would work, but perhaps you could install [realVNC]("http://www.realvnc.com/") on ubuntu through Wine. I'm sure there is a better way of doing it though.

---

### Post by UltraSonicSite on 2006-12-09
LOL, I'll try it out, but for everyone else who may respond, assume it didn't work.

---

### Post by UltraSonicSite on 2006-12-09
> **cptjaben said:**
> I don't really know if this would work, but perhaps you could install [realVNC]("http://www.realvnc.com/") on ubuntu through Wine. I'm sure there is a better way of doing it though.

ACTUALLY, it worked, but instead of runnit it through wine I just gave it to my buddy =D Thanks ^^

---

### Post by cptjaben on 2006-12-09
good to hear.

---

### Post by Cronjob on 2006-12-09
As already mentioned, the easiest solution is to just use VNC. TightVNC is a good solution on the Windows side and and should be fine on the linux side, too. However, your linux install should already come with a VNC client (and perhaps server as well). On KDE< it would be kdrc.

TightVNC is just a variation on RealVNC, but it's my goto.

---

### Post by az on 2006-12-09
> **UltraSonicSite said:**
> ACTUALLY, it worked, but instead of runnit it through wine I just gave it to my buddy =D Thanks ^^

Enabling the remote desktop in Ubutnu is the VNC server.  There is also a VNC client for you to install in Ubuntu to access another machine.

Putty is an SSH client.  For someone to connecto to you using ssh, you would have to install the ssh server

sudo apt-get install ssh

But a secure shell (SSH) is a command-line login to the other machine.  If the other machine is running an X server, the other machine can run graphical apprs from your box and have them displayed over there.  That's different from VNC which shares your current desktop.

---

### Post by max.diems on 2006-12-09
Have your friend use an Ubuntu live CD.

---

### Post by UltraSonicSite on 2006-12-09
Actually, it didn't work, it seems I can connect to myself with vncviewer.exe but my friend, when typing my ip address in, and hitting ok, just gets the screen saying "attempting to connect" forever.

---

### Post by Cronjob on 2006-12-09
You need to make sure that your machine is setup to allow connections on whatever port you are using for the connection and that any firewall or router you may be using is also configured to forward connections on that port.

---

### Post by UltraSonicSite on 2006-12-09
Whats the default port vncviewer uses?

---

### Post by Cronjob on 2006-12-09
> **UltraSonicSite said:**
> Whats the default port vncviewer uses?

You'd need to check whatever specific client/server you're using and see what their docs say, but I believe it's typically 5800 and 5900 (one would be for direct software to software connection and the other would be used if you didn't have a client to connect with; you could just fire up [http://192.168.1.104:5800](http://192.168.1.104:5800) or whatever and connect via a java interface in your browser (at least, with TightVNC).

You can, of course, set them to whatever you want them. But whatever you do, make sure you configure a password for clients to be able to connect or anyone who comes along and finds the open port will be able to connect.

---

### Post by UltraSonicSite on 2006-12-09
I'm just using the built in remote connection thing for ubuntu.

---

### Post by UltraSonicSite on 2006-12-09
[img]http://img134.imageshack.us/img134/5595/remoteca1.png[/img]

---

### Post by UltraSonicSite on 2006-12-10
download the linux version of vncserver

```
ultrasonicsite@uss-desktop:~$ vncserver

New 'uss-desktop:1 (ultrasonicsite)' desktop is uss-desktop:1

Creating default startup script /home/ultrasonicsite/.vnc/xstartup
Starting applications specified in /home/ultrasonicsite/.vnc/xstartup
Log file is /home/ultrasonicsite/.vnc/uss-desktop:1.log


```But other than that, nothing. I HIGHLY doubt that in the host box if he types uss-desktop:1 that it will connect to my computer.

---

### Post by UltraSonicSite on 2006-12-10
Typing localhost works for me, when running vncviewer with wine, by my friend, typing my IP adress cannot get it to work

He's using windows xp, with vncviewer.

---

### Post by az on 2006-12-10
> **UltraSonicSite said:**
> Typing localhost works for me, when running vncviewer with wine, by my friend, typing my IP adress cannot get it to work

He's using windows xp, with vncviewer.

Is your friend on the same network as you or is this through the internet?  How are you connected?  Do you have a modem and a router?

---

### Post by UltraSonicSite on 2006-12-11
Internet; Modem; I have a modem that's also a router.

---

### Post by dbott67 on 2006-12-11
What is it that you want to accomplish (or your friend)?
- SSH terminal
- remote desktop support
- do you want him to see your desktop or vice-versa

I've written a [HOWTO on using 'reverse VNC']("http://www.ubuntuforums.org/showthread.php?t=299489") to help bypass routers & NAT firewalls.  You need to make sure that your router forwards the correct ports to your internal IP address.  [Post #6]("http://www.ubuntuforums.org/showthread.php?p=1864058#post1864058") illustrates a Windows XP user initiating a reverse session to a Linux computer.

**_Port Forwarding:_**

As mentioned by others, VNC server uses ports 5800 & 5900 (if you want to connect to another desktop, then add 1 to the port.  5901, 5902, etc.).  These ports would need to be opened on your router and forwarded to your internal IP address (typically 192.168.1.xxx).  

VNC Viewer 'listens' on port 5500, so if you want to establish 'reverse VNC' connections you need to forward port 5500 to your internal IP address (this would allow you to see other people's desktops.

The website [www.portforward.com]("http://www.portforward.com/english/routers/port_forwarding/routerindex.htm") has details on how to do it for most routers.

**_Remote XP user connecting to your Ubuntu computer:_**

1. As posted by UltraSonicSite, enable remote connections.
2. Login to your router and forward ports 5800 and 5900 to your internal IP address (**ifconfig -a** will reveal your internal IP).
3. Using [IPchicken.com]("http://ipchicken.com/"), determine your external IP address.
4. Have your friend open VNCviewer and connect to your external IP address from step #3.
5. Your friend will need to know your VNC password.

The other issue that arises when using port-forwarding is DHCP assigned addresses.  You may want to switch to static addresses or see if your router allows 'reservations'; essentially reserving the same IP address for your computer.

If you can post the make & model of your router, I can help you.

-Dave

---

### Post by DeffeDefect on 2006-12-19
Hi Dave,
I have just setup an Ubuntu server (6.06 LTS - Dapper Drake).
I have a Belkin G+ Router (mod F5D7231-4)
[http://catalog.belkin.com/IWCatProductPage.process?Product_Id=179477](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=179477)

I aim to run the Ubuntu-server as a web and ftp -server for both internal and external use. I also want to be able to controll the server from a windows client within the firewall and also external (I want to be able to do this in terminal mode (ssh) and graphic mode). And I also wan't to reach files (music and movies) on the server for an upcoming media center. =)

Both my machines within the firewall use the same router but notyet same network.
Ofcourse, fixed IP for both my server and windows XP machine would be nice. =)

How do I set up this in the best way and correct?

Best regards/
DeffeDefect

---

### Post by lucky_chouhan on 2006-12-20
i have 2 machine one is xp and other is ubuntu i just installed ssh on add remove package. install the putty in xp and type my ip address and i am connected to my ubuntu terminal.:) 

i try several other linux machine and its working if ssh is open and running on server. but i am block at root login and pass.:(

---

### Post by dbott67 on 2006-12-20
With Ubuntu, the root account is not enabled by default.  You would need to login as a defined user (such as your own account).  Then use 'sudo' to elevate your permissions.

-Dave

---

### Post by shahzadmasih on 2006-12-20
Hi, This post is very informative, however I would like some specific information. If someone can help me then please send me a private message. Best Regards,

---

### Post by DeffeDefect on 2006-12-20
Hi Dave,
I have just setup an Ubuntu server (6.06 LTS - Dapper Drake).
I have a Belkin G+ Router (mod F5D7231-4)
[http://catalog.belkin.com/IWCatProdu...duct_Id=179477](http://catalog.belkin.com/IWCatProdu...duct_Id=179477)

I aim to run the Ubuntu-server as a web and ftp -server for both internal and external use. I also want to be able to controll the server from a windows client within the firewall and also external (I want to be able to do this in terminal mode (ssh) and graphic mode). And I also wan't to reach files (music and movies) on the server for an upcoming media center. =)

Both my machines within the firewall use the same router but notyet same network.
Ofcourse, fixed IP for both my server and windows XP machine would be nice. =)

How do I set up this in the best way and correct?

Best regards/
DeffeDefect:-k

---

### Post by Dubbayoo on 2006-12-20
> **UltraSonicSite said:**
> [img]http://img134.imageshack.us/img134/5595/remoteca1.png[/img]

nice theme; what is that?

---

### Post by dbott67 on 2006-12-20
> **DeffeDefect said:**
> Hi Dave,
I have just setup an Ubuntu server (6.06 LTS - Dapper Drake).
I have a Belkin G+ Router (mod F5D7231-4)
[http://catalog.belkin.com/IWCatProdu...duct_Id=179477](http://catalog.belkin.com/IWCatProdu...duct_Id=179477)

I aim to run the Ubuntu-server as a web and ftp -server for both internal and external use. I also want to be able to controll the server from a windows client within the firewall and also external (I want to be able to do this in terminal mode (ssh) and graphic mode). And I also wan't to reach files (music and movies) on the server for an upcoming media center. =)

Both my machines within the firewall use the same router but notyet same network.
Ofcourse, fixed IP for both my server and windows XP machine would be nice. =)

How do I set up this in the best way and correct?

Best regards/
DeffeDefect:-k

Within the firewall, it should be easy to control the Ubuntu server from a Windows machine.  These are the prerequisites:

Windows Machine:
1. PuTTy (SSH program)
2. RealVNC, UltraVNC, TightVNC or any derivative of VNC.

Ubuntu Server:
1. openssh
```
sudo apt-get install ssh
```
2. x11vnc
```
sudo apt-get install x11vnc
```

... gotta go right now... I'll post more when I get home.

-Dave

---

### Post by DeffeDefect on 2006-12-20
> **dbott67 said:**
> Within the firewall, it should be easy to control the Ubuntu server from a Windows machine.  These are the prerequisites:

Windows Machine:
1. PuTTy (SSH program)
2. RealVNC, UltraVNC, TightVNC or any derivative of VNC.

Ubuntu Server:
1. openssh
```
sudo apt-get install ssh
```
2. x11vnc
```
sudo apt-get install x11vnc
```

... gotta go right now... I'll post more when I get home.

-Dave

Installed above software (use UltraVNC).

Regards/
DeffeD

---

### Post by dbott67 on 2006-12-20
Okay... I'm back.  As I have no way of knowing what your experience with networking is, I will be quite explicit with my instructions and explanations as it may be of some use for someone else who finds this thread.  If you've "been there, done that" then feel free to skip over the boring parts.

**_SSH from the Internal LAN_**

1. After installing ssh on the server, it should automatically be running as a daemon:
```
dbott@thedrake:~$ ps aux | grep sshd
root      4589  0.0  0.0   4764   768 ?        Ss   Dec19   0:00 /usr/sbin/sshd
dbott    25484  0.0  0.0   2880   808 pts/0    R+   20:23   0:00 grep sshd

```

2. Install PuTTY on your XP computer from here: [http://www.putty.nl/download.html](http://www.putty.nl/download.html)

3. Open PuTTY and enter the (internal) IP address of your Ubuntu server and login using your normal Ubuntu user account & password.

**_PORT-FORWARDING_**

Most personal/home cable/DSL NAT routers are pretty good little firewalls.  They permit outbound traffic, but drop unsolicted inbound traffic, meaning that external devices cannot access internal resources unless you permit them to.  In order to do this, most routers have a feature called 'port-forwarding'.  You need to forward the appropriate ports on your router to the internal IP address of your server.

**Ports**

There are 65,536 ports available to internet traffic (think of them as channels on a TV).  The first 1,024 are considered 'well-known' ports and have become de-facto standards for certain types of traffic:
- http traffic uses port 80
- ftp uses port 21
[COLOR="Red"]- ssh uses port 22[/COLOR]
- telnet uses port 23
- e-mail (smtp/pop3/imap) uses ports 25, 110 & 143, respectively
[COLOR="Red"]- vnc uses 5500, 5800 & 5900[/COLOR]
And the list goes on & on...

The key ports for you are 22 (ssh) and 5500, 5800 and 5900 (vnc).  You need to tell your router that whenever it receives traffic on the above ports, that it should forward the traffic to the internal IP address of your Ubuntu server.  I've got a D-Link Router that refers to 'port-forwarding' as **VIRTUAL SERVERS** (see attached screenshot).  There is a good website called [http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm) that has many routers & instructions on how to configure them.

If you take a close look at my first screenshot, you can see the ports I'm forwarding to which specific computer.  This setup allows me to VNC to any of my computers at home (XP, Ubuntu, OSX).  I can also SSH in and connect via FTP to my NAS device.

After you've got your router setup, you need to connect to the **EXTERNAL** IP address that your ISP has assigned you.  As this address can change, you can use free services such as [Dynamic DNS]("http://www.dyndns.com/") to assign a static name (such as deffed.dyndns.org) to your external router interface.  Whenver you need to connect remotely, you can just use your dynamic DNS name instead of trying to find out the IP address of your home connection.

**_VNC_**

Finally, you'll need to install some variant of VNC server on your Ubuntu computer.  Ubuntu includes a remote desktop app (called vino), however, the downside to it is that the computer must be logged in before you can connect.  Installing one of the VNC server variants will allow you to connect before logging in, as well as to the current desktop.  This [thread]("http://www.ubuntuforums.org/showthread.php?p=1627716") has all of the gory details.

Just make sure that all VNC & SSH are installed & configured properly INTERNALLY first.  If you can connect from XP to Ubuntu behind your firewall, then port-forwarding will be fairly simple to setup.

I'm also attaching a few other screenshots from a while ago showing me connecting via VNC from work to home (XP, 2000, Mac, Linux, etc.).

-Dave

---

### Post by Hubris2 on 2006-12-21
I'm doing something similar, but not quite there yet.

I'm using the remote desktop feature in Ubuntu, I've confirmed that terminal 0 works by connecting with VNC directly with a windows laptop on the LAN.

I've installed SSH on the machine, and I'm now trying to connect from work.  I'm using putty, I have local port 5900 forwarded to remote port 5900.  My pc at home is behind a NAT router, with port 22 being forwarded to the correct computer.

When I start Putty I'm prompted for a login, and I successfully get a shell.

When I try start a local VNC client (tightVNC, realVNC or others) and connect to localhost, localhost:0 or localhost::5900 I am repeatedly told "The connection closed unexpectedly".  

Am I missing a step?  I'd assume my SSH connection is valid as I have a shell....is something wrong with my tunnel setup in putty?

Thanks!

---

### Post by dbott67 on 2006-12-21
This is how I've got mine setup (see attached screenshot).  

I've got a tunnel (L:5900 --> 127.0.0.1:5900)
I just connect vncviewer to 127.0.0.1 and I get the login prompt on my Ubuntu box.

-Dave

---

### Post by Hubris2 on 2006-12-21
Hmm....the only thing you're doing differently than me, is you're using the IP for localhost rather than the name.  I did see mention in my searches tonight that there was some security setting that needed to be changed since by default Linux wouldn't allow a 'local' login via TCP.

Since I don't think the router is at fault, I'll do some testing using my laptop running XP.  It can connect successfully with VNC directly, so I'll see if I can establish a SSH connection over the lan and connect through that.

---

### Post by Hubris2 on 2006-12-21
Internally, I can connect via SSH from my laptop to the linux box.  When I setup the tunnel going directly from 127.0.0.1:5900 to 192.168.1.100:5900 it works.  When I configure the tunnel within Putty to use the external hostname I can extablish SSH and login but when I try connect VNC it immediately disconnects (same as I was getting from work).

Was that my problem - the tunnel should just be connecting to the internal IP, since the overall SSH session was already connected from the outside?

---

### Post by dbott67 on 2006-12-21
It's funny, I tried using PuTTY between my laptop (running Dapper) and PC (also running Dapper and both behind the router) and it didn't work.  I tried using PuTTY from my Windows XP PC at work and it worked (see my screenshot above).

Then I found this post:
[http://www.linuxplanet.com/linuxplanet/tutorials/6155/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6155/1/)
On page 2, they suggest using openssh & this command on the remote machine:
```
ssh xx.xxx.xx.xx -L 5900:localhost:5900
```
So, on my laptop (192.168.1.105) I tried to connect to my desktop (192.168.1.106) using this command to establish the SSH tunnel:
```
ssh 192.168.1.106 -L 5900:localhost:5900
```
Followed by this command to connect to the VNC server:
```
vncviewer localhost:0
```
Hey! It works!!! These also work:
```
vncviewer localhost
vncviewer 127.0.0.1
```
But here's the strange part:

My laptop multi-boots between XP, Dapper, 2003 & MCE.  On Dapper, PuTTY doesn't work but openssh does when creating the VNC tunnel.  However, if I boot into Windows PuTTY works as it should using the exact same configuration!  What gives!?!?!? :)

Anyhow, try openssh & see if that works.

-Dave

---

