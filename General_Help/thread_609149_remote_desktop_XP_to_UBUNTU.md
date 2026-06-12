---
title: "remote desktop XP to UBUNTU"
date: 2007-11-10
forum: General Help
---

### Post by mchaley on 2007-11-10
Hey, 
I've read up on the other posts, but I dont see a clear cut answer. 
I'm trying to connect TO ubuntu (remote desktop turned on via system, prefs, Remote desktop) FROM an xp pro machine. I tried connecting via computer name and IP from the XP machine. I get the same error every time, cant connect talk to the admin. 

Is it even possible to connect to ubuntu (stock) via XP? 
What progs do I need to make it work?
Thanks

---

### Post by atomkarinca on 2007-11-10
first of all, you should open the port 3800 on the ubuntu machine. then you need a vnc client for the win machine, like [realvnc]("http://www.realvnc.com/") or [tightvnc]("http://www.tightvnc.com/"). finally you need the ip address of the ubuntu machine. if it's not a static ip, you can use [ddclient]("http://www.dyndns.com/support/clients/unix.html"). then you type the ip address or the static address you got and add ":3800" at the end and connect.

---

### Post by mchaley on 2007-11-10
ah, this is what I figured I had to do. Hearing that it was possible to do via XP's remote desktop made me excited :P So it is -not- possible to do it just from xp's remote destkop?

---

### Post by atomkarinca on 2007-11-10
AFAIK windows uses rdp but ubuntu uses vnc. so in order to connect to a vnc machine, you need a vnc client. and vice versa you need a rdp client to connect to a windows machine (thank god we have that already installed). so, no it's not possible just from xp's mstsc, but just a step away.

---

### Post by mchaley on 2007-11-10
It'd be an awesome feature to be able to remote into ubuntu from xp and vise versa :D 
Know if its in the works? 

so, whats the best version of VNC?

I'll also have to look into SSH.
Thanks for the help!

---

### Post by uboxuser1 on 2007-11-10
Hello, 
I've had UBUNTU for a week, and I think its an awesome OS. I have an old laptop (XP) which I want to be able to use to Remotly connect to the Ubuntu computer graphically like WINDOWS RDP. I have TightVNC on my laptop and I  can connect to Ubuntu...except with one littel problem. OK its a big problem. I have to be logged in to Ubuntu first to be able  to connect from my xp laptop. This totally kills the purpose because it means I have to go and log on locally everytime on the ubuntu so that I can go back to my laptop and remotly connect. Does anyone have a solution to this. I have heard  and tried many theories but it has not worked.

Thanks

---

### Post by mchaley on 2007-11-10
what is the best vnc client?

---

### Post by uboxuser1 on 2007-11-10
tightvnc i think ..do u know the answer 2 my question mchley???

---

### Post by mchaley on 2007-11-10
no, I've not fiddled with it. I will mess with it and see what I come up with

---

### Post by mchaley on 2007-11-10
before I mess with it, I'd like to figure out what the best VNC prog is. :D

---

### Post by weblordpepe on 2007-11-10
While VNC is good, it can't match the speed of RDP. Basically what you want to do is use NX.

X, X11, Xorg, whatever you call it - is actually network aware. Your display doesn't have to be on the same box as the running application. The only problem is that there is too much traffic going over the wire and its slow.

Thats where NX comes in. There's a open-source implimentation but its ****, so use the freeware one from [http://www.no-machine.com](http://www.no-machine.com)

Basically how it works is you have a second, special X server running on your remote machine. Your NX client on the local machine connects to SSH on the remote machine, and tunnels into the remote special X server. The special X server talks over SSH to your NX client, using the NX protocol - an extremely optimized X communication protocol.

You use the NX client on Windows/mac/linux/whatever and put in the IP address of your remote machine, just like normal. The only ports open to the outside world is your regular SSH port.

I have shortcuts set up to launch either the whole desktop, or just single applications. For example, I can load up Thunderbird from a machine on the other side of the world, and it displays in the task bar of my laptop, as if it was a local program.

It's extremely slim-lined FAST even on dial-up. VNC has nothing on NX, because VNC is a simple framebuffer protocol & you won't get anywhere. I would recommend ditching VNC completely & going with NX. NX is even faster than RDP/remote desktop. I have a how-to guide posted at:

[URL="http://www.geekzone.co.nz/forums.asp?ForumId=46&TopicId=12780"]Accessing your X-windows (Gnome, graphically intense programs) over the internet - a solution using NX and No-machine:
http://www.geekzone.co.nz/forums.asp?ForumId=46&TopicId=12780[/URL]

---

### Post by mchaley on 2007-11-10
So NX not only runs on all OS's, but it uses SSH automatically?

---

### Post by weblordpepe on 2007-11-10
Thats right. I've run it as a server on Ubuntu and Windows.
And used it as a client on Ubuntu and Windows.

It's basically a special X server that is coded to work over SSH, using the NX language to your NX client, which is actually an X server anyway.

NX is basically like super-optimized & compressed X traffic.

---

### Post by mchaley on 2007-11-10
seems to me like I should use NX over xp's remote desktop even from xp to xp machines. How much of a demand is the software?

---

### Post by weblordpepe on 2007-11-10
Not sure. Next to nothing. 
I think if XP is the server, then it uses RDP protocol under the hood. But if linux or mac is the server, then it uses NX.
It tunnels over SSH by itself anyway so the only ports you need open publicly is the SSH port. Gotta love that.

---

### Post by mchaley on 2007-11-10
what about server2k3 or server 2k8? RDP? If I get the server for windows and use the client... it should use NX, right? I'll have to put the server and client on all of my windows/nix machines, eh?

---

### Post by mchaley on 2007-11-10
also that link didnt work, i've not googled it yet :P

---

### Post by weblordpepe on 2007-11-10
Oooh.
It looks like there's not actually software to download for a server on Windows. From the looks of things, it just uses whatever RDP server tools exist on the Windows server.

[http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)

---

### Post by jshurst on 2007-11-10
I second nx from nomachine.  It is one of the first things to be installed when I'm getting a new system up and running.  Just install the client, server, and node packages on the Ubuntu machine you want to connect to (don't forget to do a sudo aptitude install ssh if you don't already have that installed) and then install the client on your XP machine and you're good to go.

Really awesome software.

J

---

### Post by weblordpepe on 2007-11-11
Agreed. It's so damn fast, though. That's the thing. It's not like VNC, which is just a simple screen-grabbing protocol. It's X, but optimized X. It's similar to RDP kinda sorta in its functionality/speed. Very fast.

---

### Post by kd7swh on 2007-11-11
I think tightVNC is the best vnc progy for windoze too, but I use SSH most of the time. PuTTy is by far the best windoze SSH client. 

Some users even use VNC through SSH because SSH has better encryption.

---

### Post by mchaley on 2007-11-11
i'm confused as to what exactly I need per computer. Ok, I can break them up like this:
windows server
windows work station
Linux server
linux work station


right now I'm looking to go from a windows work station to a (ubuntu) work station. 

later aps will be accessing servers though. 


also, what are server, node, and client?

Thanks for the help!

---

### Post by weblordpepe on 2007-11-11
Download the free forever version

[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

That's the server.

And the client can be found on the main page. I'm not too sure what a node is though with regards to this.

Client is just what it sounds like - the client.

And that should be about it. You'll need SSH installed and knowing linux you'll probably be missing some random library that noones heard of :P

---

### Post by atomkarinca on 2007-11-11
this is a very fast way indeed. but the problem is you can't connect to an existing session. so, it doesn't do anything for me.

---

### Post by mchaley on 2007-11-11
> **atomkarinca said:**
> this is a very fast way indeed. but the problem is you can't connect to an existing session. so, it doesn't do anything for me.

??

How do i install SSH?
client NX connects to server NX, right? I'll have to start messing with it.

---

### Post by weblordpepe on 2007-11-11
type in the terminal:
**sudo apt-get install sshd**

---

### Post by mchaley on 2007-11-11
E: Couldn't find package sshd


also, do I have to install some sort of SSH on the windows machines?

---

### Post by atomkarinca on 2007-11-12
try this one:

```
sudo apt-get install ssh openssh-server
```

for the ubuntu machine. also you will need to install the nx server on the ubuntu machine and nx client on the win machine.

---

### Post by mchaley on 2007-11-12
that one seemed to work

---

### Post by mchaley on 2007-11-12
when installing server onto ubuntu:
error: dependency is not satisfiable:nxclient

do I need nxclient first? o.O 

   	
Note: Installation of NX Server for Linux requires the download and installation of three packages: client, node and server. The client is needed because it ships libraries used by the node. The node is needed because it ships tools needed by the server. Furthermore, the SSH server daemon (SSHD) needs to be up and running on each of the NX Node machines since NX relies on the mechanism provided by the SSH subsystem for handling user authentication. 

ANSWER= YES :D

its a pitty the server doesnt go on windows machines, it seems like a much more secure method of RD.

---

### Post by mchaley on 2007-11-12
WOW
talk about hard to use!
So... what we have. I put all 3 on ubuntu including server. 
apps>internet>nx client  There is no server icon to get into. I played around with server.cfg, but I cant save settings (permissions probably). 

I also put client on XP... start-progs-nx client - (only icon is uninstall). 

?!
1). how do I modify the server via ubuntu?
2). how the heck do I use the client in XP? 

I'll keep messing with it, but if you have any tips they'd be great! 
Thanks

---

### Post by mchaley on 2007-11-12
2). I'm an idiot... I installed the wrong thing :D

---

### Post by mchaley on 2007-11-12
my biggest question right now is how to configure the server? 
Do I REALLY have to go through the 10,000 lines of code per server.cfg and node.cfg?

---

### Post by mchaley on 2007-11-12
meh, still no luck

how much of a benefit is this over VNC?

---

### Post by atomkarinca on 2007-11-13
> **mchaley said:**
> meh, still no luck
 
how much of a benefit is this over VNC?
 
if you've installed the server of nx and ssh on the ubuntu machine then you should be good to go. start the client from the windows machine and enter your ip, the default port for ssh is 22. if you have any problems let me know (i'm not on my ubuntu machine right now, i can double-check these when i get home)
 
>  
how much of a benefit is this over VNC?

 
vnc is slower than nx because it transfers still images. but as i mentioned, the prior use of vnc for me is being able to log in to an existing session and nx doesn't have that option. so it depends on what you are expecting from the connection.

---

### Post by weblordpepe on 2007-11-14
I did some good stuff with NX. I had NX on my desktop for ages, but wanted linux on my laptop too but without installing anything.

Using NX, my laptop had its own username, desktop, files, its own session - all running on the laptop with sound & openGL graphics. Just by using the NX client for XP, and NX server on Windows.

---

### Post by ImNeat on 2007-11-14
What setup do you guys recommend for me to connect Linux -> Windows?

I have experience with FreeNX for Linux -> Linux, but I see no server/node FreeNX packages for Windows.

Will FreeNX client on Linux connect to RDP server on Windows?

---

### Post by atomkarinca on 2007-11-15
you can use applications > internet > terminal server client or install krdc to connect to the windows rdp server.

---

### Post by ImNeat on 2007-11-15
> **atomkarinca said:**
> you can use applications > internet > terminal server client or install krdc to connect to the windows rdp server.

Ah tsclient does work fairly well. Only issue seems to be that sound from the server won't play on the local client. Thanks for the suggestion.

Would there be any advantages of krdc or nxclient over tsclient?

---

### Post by ImNeat on 2007-11-15
Is it possible to change the port tsclient (rdesktop) uses? Does it have a config file like SSH has?

---

### Post by weblordpepe on 2007-11-15
you just put the port number after the ip address. For example:
**192.168.1.20:3389**

---

### Post by ImNeat on 2007-11-15
Hrm not having much luck using custom ports. I tried port 6664 without success.

10.10.10.7:6664
---
Router set to forward 6664 to 10.10.10.7
---
Edited Vista registry so it listens for RDP on 6664.

Not sure where the connection is being refused.


Also, anyone have any experience with gSTM?  It is a graphical tool to help SSH tunnel other connections including RDP.  I'm not sure what to set the host to though. Also, do I need to have sshd running in Vista?  Will need more research...

---

### Post by kd7swh on 2007-11-16
make sure you don't have a firewall in the way

---

### Post by ImNeat on 2007-11-17
Everything else seems to be configured fine because it works fine on the default port

---

### Post by daflame on 2007-11-18
If anyone is interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If anyone needs other dist packages, please let me know and I'll start a VM to build one.

---

### Post by weblordpepe on 2007-11-18
Thats a releif. I'm glad somebody has gotten freeNX working. I gave up.

---

### Post by mchaley on 2007-11-18
Next question :P 
I got !m working, but only for a day or so. Now I connect and it just shows a black screen. I shadowed my ubuntu machine but cant connect without getting a black screen. 
any ideas?

---

### Post by mchaley on 2007-11-18
just tried to log in with a new un/pw... got this:

NX> 203 NXSSH running with pid: 29968
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 10.4.52.218 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.0.0-74 - LFE
NX> 105 Hello NXCLIENT - Version 3.0.0
NX> 134 Accepted protocol: 3.0.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: mchaley3
NX> 102 Password: *********
NX> 536 ERROR: Reached the maximum number of allowed users on this server.
NX> 999 Bye.
NX> 280 Exiting on signal: 15

---

### Post by weblordpepe on 2007-11-19
Previous sessions running already perhaps. I know that theres some silly bug somewhere, where it will have a blank screen but show a dialog box after a wee while.

It's because its trying to show that 'keyboard configuration is different from the one gnome knows about. use gnomes or the new layout?' window box. You could possibly even just hit enter.

---

### Post by mchaley on 2007-11-19
Yeah, I rebooted it and it works fine now. I'll bet a previous session was already running. Is there any way to end sessions? I looked around in managers but I didnt see anything. Someone was talking about FreeNX being able to handle multiple sessions... would that be better do you think?

Thanks!

---

### Post by mchaley on 2007-11-19
Also, how can I check to make sure SSH is being used? Security is a BIG issue for me.

---

### Post by mchaley on 2007-11-19
Right now I'm connected on a LAN:

10.4.xxx.xxx:1020

---

### Post by weblordpepe on 2007-11-20
Umm...well you should only actually be able to connect via ssh. At least on a lan. I can't recall trying on a localhost connection.

But you can tell because the nx client spawns an ssh client. And you could see the SSH traffic on the lan.

---

### Post by vol_freak on 2007-11-20
How about this scneario, would this be possible with nx?

I want to connect via a windows xp client at work to my laptop but through my centos machine running my ssh server.

So windows xp running nx client >> to home network through ssh sever on centos machine >> to laptop inside home network running ubuntu. 

Any thoughts on this?

---

### Post by BradwJensen on 2007-11-21
Ok, sorry i haven't read through all the pages here cause i have little time.. But seriously why does one have to install anything on the XP machine to remote desktop with Linux???????  This sounds so OLD and just plain HORRIBLE..

One reason why i said that is because anytime i ever need to get to my Home Linux computer is if i left a file on it and i'm at SCHOOL or a FRIENDS house where it's either _not possible_ to install a program like that on on the XP computer or its _just pointless_ in that all i really need is that one or few file(s).

**Honestly, the people who make Ubuntu need to fix this issue**.. Lots of times when people need things from their Linux systems -- they're in a position where downloading and installing an application for something that should be so quick and simple is just not the right way to go..  I highly doubt many peoples Work places and Schools would really be into you installing something on one of their computers just to get something important from your computer at home..   Or what if i just wanted to demonstrate to a friend or someone at like a library what Ubuntu Linux is all about without taking too much time?  yeah, i think i proved my point, no?

They need to get it to work with MS's Remote Desktop feature thats built in.

---

### Post by weblordpepe on 2007-11-21
Blame Microsoft for not supporting X-windows. It's not Canonical's fault. You can help by writing a RDP daemon for Xorg.

---

### Post by BradwJensen on 2007-11-21
> **weblordpepe said:**
> Blame Microsoft for not supporting X-windows. It's not Canonical's fault. You can help by writing a RDP daemon for Xorg.


I'm not blaming anyone, I'm just stating that the only ones with any chance of doing anything would be the Ubuntu peeps, so they should.

If I knew how to program, which i don't yet - i would be doing tons of it for Linux..

---

### Post by daflame on 2007-11-22
> **weblordpepe said:**
> Thats a releif. I'm glad somebody has gotten freeNX working. I gave up.

Yeah, let me tell you.  I had to employ the best of my programming expertise to make it work.  I think I should send Fabian (the maker) a copy.  I am opening a forum for all the lost souls in ubuntu needing a working package.  Mind you I still have a couple minor bugs to work out.  I will post it soon.

---

### Post by daflame on 2007-11-22
> **mchaley said:**
> Yeah, I rebooted it and it works fine now. I'll bet a previous session was already running. Is there any way to end sessions? I looked around in managers but I didnt see anything. Someone was talking about FreeNX being able to handle multiple sessions... would that be better do you think?

Thanks!

Your best bet is FreeNX it has unlimited connections.  I have working packages if you want them.  I will be setting up a forum to post soon.  I'm just testing for demand right now to make my time worth it.  As for a way to delete sessions.  At a command prompt at the server you can run:
```
sudo /usr/NX/bin/nxserver --help
```
to show the list of options.  One of them is to terminate sessions.  With FreeNX just:
```
sudo nxserver --help
```
will work.

---

### Post by vol_freak on 2007-11-22
> **vol_freak said:**
> How about this scneario, would this be possible with nx?

I want to connect via a windows xp client at work to my laptop but through my centos machine running my ssh server.

So windows xp running nx client >> to home network through ssh sever on centos machine >> to laptop inside home network running ubuntu. 

Any thoughts on this?

To answer my own question, nxclient has the ability to connect through a proxy in the configuration so it does work and it's very simple. 


thanks

---

### Post by daflame on 2007-11-22
> **BradwJensen said:**
> I'm not blaming anyone, I'm just stating that the only ones with any chance of doing anything would be the Ubuntu peeps, so they should.

If I knew how to program, which i don't yet - i would be doing tons of it for Linux..

I could be wrong about this, but I thought there was a web and java based NX Client as well?  Am I wrong?  I installed the web companion (on the server) one time and was pleasantly surprised to have an nx desktop in no time.

---

### Post by daflame on 2007-11-22
I opened a forum with the packages linked in...  I'm still not going to have AMD64 packages until tomorrow though.  Feel free to make whatever suggestions you like as I am still not sure of the package dependencies since I have them all already installed.

Click [here]("http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx") to see the post.  Please contribute to the refinement of the installation.

---

### Post by weblordpepe on 2007-11-23
> **daflame said:**
> Yeah, let me tell you.  I had to employ the best of my programming expertise to make it work.  I think I should send Fabian (the maker) a copy.  I am opening a forum for all the lost souls in ubuntu needing a working package.  Mind you I still have a couple minor bugs to work out.  I will post it soon.

Good stuff!!! FreeNX has the potential (since it isnt commercial) to replace VNC as the default 'remote desktop' service.

VNC is embarassing compared to RDP/remote desktop. It really is. But alas, I can't code for beans.

---

### Post by Godsgimp on 2007-11-30
> **BradwJensen said:**
> Ok, sorry i haven't read through all the pages here cause i have little time.. But seriously why does one have to install anything on the XP machine to remote desktop with Linux???????  This sounds so OLD and just plain HORRIBLE..

One reason why i said that is because anytime i ever need to get to my Home Linux computer is if i left a file on it and i'm at SCHOOL or a FRIENDS house where it's either _not possible_ to install a program like that on on the XP computer or its _just pointless_ in that all i really need is that one or few file(s).

**Honestly, the people who make Ubuntu need to fix this issue**.. Lots of times when people need things from their Linux systems -- they're in a position where downloading and installing an application for something that should be so quick and simple is just not the right way to go..  I highly doubt many peoples Work places and Schools would really be into you installing something on one of their computers just to get something important from your computer at home..   Or what if i just wanted to demonstrate to a friend or someone at like a library what Ubuntu Linux is all about without taking too much time?  yeah, i think i proved my point, no?

They need to get it to work with MS's Remote Desktop feature thats built in.

Buy yourself a nice sized usb card. 4gigs would be real nice. Install Ubuntu on that and then when you are at school or something you can run your install on any pc and remote desktop to your home pc. Also it should also mount the windows of the machine you are using as a shared drive. 

I'm pretty new at Ubuntu so I could be wrong, but i'm pretty sure that would answer your needs.

---

### Post by daflame on 2007-11-30
> **Godsgimp said:**
> Buy yourself a nice sized usb card. 4gigs would be real nice. Install Ubuntu on that and then when you are at school or something you can run your install on any pc and remote desktop to your home pc. Also it should also mount the windows of the machine you are using as a shared drive. 

I'm pretty new at Ubuntu so I could be wrong, but i'm pretty sure that would answer your needs.

On top of that you can get a version of linux that will boot from within windows, if you don't have the liberty of rebooting the machine or setting the option of booting off of USB, and use the flash stick as the storage.

---

### Post by mchaley on 2007-12-03
what version?

---

### Post by daflame on 2007-12-04
> **mchaley said:**
> what version?

Just take a look at this link:
[http://www.colinux.org/](http://www.colinux.org/)

I find that kind of flexibility in an OS unheard of.  Let me know of another OS that can run co-operatively with a fundamentally different OS (Windows) so easily.

They even have Ubuntu root images, though they are a little old mind you.

There are Ubuntu instructions here:
[http://ubuntuforums.org/showthread.php?t=81444](http://ubuntuforums.org/showthread.php?t=81444)

Here is another site with a way to use QEmu (but this is emulation and not as fast):
[http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/](http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/)

Check out thiis post as well:
[http://roth.textdriven.com/other/colinux/](http://roth.textdriven.com/other/colinux/)

Then, if you get all that to work try and setup an NX access point as well.

---

### Post by weblordpepe on 2007-12-06
Holy cow!!
Sow you can get Ubuntu to run inside windows from a USB key??

EDIT:
Holy cow you can too!! Thats so bizzare!!

---

### Post by BradwJensen on 2007-12-06
> **weblordpepe said:**
> Holy cow!!
Sow you can get Ubuntu to run inside windows from a USB key??

EDIT:
Holy cow you can too!! Thats so bizzare!!


Haha, yeah, i didn't know that til that comment too... I just did it with LinuxMint and it seems to run way faster than on a hard drive.

I'm gonna try Ubuntu next :-P

---

### Post by weblordpepe on 2007-12-08
It would aye. Flash is way faster than a hard drive. All these solid-state drives coming out are yummy.

---

### Post by daflame on 2007-12-09
> **weblordpepe said:**
> It would aye. Flash is way faster than a hard drive. All these solid-state drives coming out are yummy.

Yes, in access times it certainly is.  Where a hard drive can take a random number of milliseconds per access depending on where the head is, but flash is even keel on nanoseconds.  However, you need to make sure you have a recent flash drive.  Mine maxes out at 3MB/s...  8-(

---

