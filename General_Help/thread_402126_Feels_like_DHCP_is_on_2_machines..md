---
title: "Feels like DHCP is on 2 machines."
date: 2007-04-05
forum: General Help
---

### Post by bdemers on 2007-04-05
I just put a fresh installation of "Server" onto my home system.  Since I am a newbie, I added Gnome and networkcardconfig as an app inside of Gnome.  I ran the networkapp, electing to have the "Server" address set up by my DHCP service, located on a different machine.  I did not attempt to set "Server" up as a DHCP controller, since I already have one running.
Anyway, after running networkcardconfig I lost my connectivity on other workstations (XP).  If I power off "Server" and repair connection on my workstation, connectivity returns.  The issue is not IP address conflicts.
My guess is that  DHCP is enabled on "Server". Perhaps during the LAMP portion of the initial install DHCP was also put in.  So, how do I check to see if DHCP is running on "Server" and if it is, disable it permanently?

---

### Post by dannyboy79 on 2007-04-05
I am not sure what the lamp server installs but I can help you disable it. please show the output from 

**sudo aptitude show dhcp3-server**

and also

**sudo aptitude show dhcp**

then we can go from there. also, you can see what ports are listening which would tell you if your "new" server installation is listening for new dhcp requests. just do

**sudo netstat -pat**

does it say dhcpin that list. also, how do you know that it's not a ip conflict? did you check the output from 

**ifconfig -a**

and compatre that ip to the other machines?

UPDATE: I just looked at what the lamp install installs and it does NOT setup a dhcp server. so there is something else occuring. I have noticed that you use the term "server" but yet you talk about 2 different boxes, this can be confussing. when you were using the networkcardconfig program or whatever, what ip did you use as your dhcp server? do you have a router in the network? how do you connect to the internet, modem, cable modem, dsl? i don't know what this networkcardconfig thing is, is that just the thing under system, admin, netoworking? are you using a gui or not? is this networkcardconfig a command line applicaiton or do you have xserver-core X11 installed?

---

### Post by bdemers on 2007-04-05
Sorry about the confusion on box names.  There are 2 boxes that are providing services.  One box is IPCop, and it is IPCop that I use for the DHCP service, along with gateway.  IPCop plugs into a router/switch which is being used only as a switch (you work with what you got) and it has DHCP turned off. (For sure, I looked).  The 2nd box is what I am calling "Server" and it current is being configured to be my CMS server.  During the process of setup, I thought to allow the nic to be under DHCP, but maybe I'll just set it to be a fixed.  DHCP doesn't buy me anything for this box anyway.

I ran the commands that you laid out for me and here's what I got back:

*For dhcp3-server* I got not installed

*For dhcp* I saw nothing in the verbage that made me think it was installed.

*Both commands returned a list of conflicts, but I'm guessing that these are not actually detected, but rather 'Don't run together' statements

*netstat -pat* returned only column headings, no data

*ifconfig -a* returned 192.168.1.147 for eth0

Then I went into IPCop and looked at the Assigned table for DHCP and found valid addresses for my 2 workstations and for "Server", "Server" being reported as 192.168.1.147.  The 2 workstations are assigned to .1.100 and .1.102.  The range is .1.100 to .1.150.  The 2 workstations are XP, and "Server" is Ubuntu.  IPCop has address .1.254.  That's it.  No conflicts, and apparently no dual DHCP servers.

This, then, takes me back to the networkcardconfig app, and how it plays with the network. 
I am now of the opinion that relying on this app to set up my nic is not what I really want to do, that I should set the nic up in whatever file(s)  are used for nic control.  I'll set card up for a static IP and this should end my trauma, though its not telling me what the mechanism is that's causing all this to happen.  Maybe I should let the theorist in me lose for once.  

To set up a static IP using the console I would type:

*sudo gedit /etc/network/interfaces

This file should be edited to say:
 
*auto eth0
*iface eth0 inet static
*       address 192.168.1.253
*       netmask 255.255.255.0
*       gateway 192.168.1.254


I would the type:

*sudo gedit /etc/resolv.conf

This file should be edited to say:

*search mydomain.com   (whatever IPCop thinks my domain is)
*nameserver 192.168.1.254


I'll try this, see anything that this newbie forgot?

---

### Post by dannyboy79 on 2007-04-05
ok

192.168.1.254             as IPCop (it's DHCP range is .100 to .150) (this computer has 2 interfaces, maybe eth0 and eth1? where the internet comes in and forwards it to the other interface so that it can make it your computers? what route return?
192.168.1.147             as ubuntu server
.100                           as workstation
.102                           as as workstation

is IPCop setup to be a DNS server???? if not, than this is your problem!! if you can ping [www.gogle.com](www.gogle.com), than this is a dns issue. Also, you don't want to edit resolv.conf manually. If you do setup a static ip then you add your dns servers right below your interface (this is what I do) like this:

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 24.56.172.222 24.56.172.223

let me know how it goes. you now it would be so much easier if you started your network off with easy to read/see numbers. also, what does traceroute 192.168.1.254 from your ubuntu server return?

---

### Post by bdemers on 2007-04-05
I have manually configured the interfaces file to create a static address.  I had no need to touch the resolv file, as it was properly set up when I looked at it.

IPCop does have 2 interfaces.  Eth0 is attached to my cable modem, is dhcp configured and holds the addresses that the isp sends out.  Eth1 is static.  It is the one set to 192.168.1.254.  This address is the DHCP server, DNS server (IPCop sets this up as a proxy), and Gateway.  IPCop will also allow me 2 more interfaces. One to set up a DMZ, where the web server will go when its ready, and a 4th  interface that would go to a wireless.

I have been running the network with the web server and its static addressed card for about an hour and have no issues.  Internet service to the workstations has been uninterrupted during this period.  It's not long enough to tell yet, but that's all I have, since that,s when I made my last change. 

Is there something that Linux sends on the Lan that Windows doesn't like whenever the nic requires a refresh?  IPCop (and therefore DHCP) is also a Ubuntu OS.

---

### Post by dannyboy79 on 2007-04-05
no, not that I know of. so what exactly did you change to make this all of a sudden work? can I ask why you would have a switch in between your modem and you router (i consider IPCop to be your router) you always want your router first. I don't see the point of the  internet traffic coming into a switch, you can't really hook a computer up to it so your're more or less wasting the ports on that switch, unless of course you  use a software firewall but those aren't nerely as safe as hardware firewalls (which is what your IPCop machine is since it;s solely dedicated to filtering packets etc etc. Anyway, i just think it would be better suited further down the line but you must have a good reason for doing this? glad it's working so far

---

### Post by bdemers on 2007-04-05
Well, let's see.  The issue that I was having was my workstations lose connectivity to the internet when I ran networkcardconfig on the webserver.  It also appeared that when I refreshed the nic on the webserver I lost connectivity on the workstations.  Any other time all was ok.  If I left the webserver on all was fine until a refresh occurred.  

So the change I made was to give the nic a static address, removing the need for a dhcp refresh.
Its still a little early, but so far all seems to be right with the world.  I just can't figure out what the mechanism is that would cause my XP computers to lose it during the webservers refresh.  One thing, duh, that I never did do was an ipconfig /all on the XP machines AFTER a connectivity lose. 

Thing is, this was a very predictable event.  Tweak the nic, lose the internet, every time.

---

### Post by bdemers on 2007-04-05
Oh, I forgot.  The router/switch/modem thing.  What I'm using is a Linksys cable/DSL router and 4 port switch combo.  The cable modem portion (WAN) is not being used.  Only the 4 port switch is(LAN w/ built in DHCP turned off).  What I've got is the cable modem going to the red port on the IPCop machine (eth0).  The green port on the IPCop(eth1) goes to the switch.  This is the tie point for the 2 workstations, the webserver and the gateway(IPCop).  The switch is not between the cable modem and IPCop.  I completely agree with you that placing a switch there just doesn't have any value.

---

