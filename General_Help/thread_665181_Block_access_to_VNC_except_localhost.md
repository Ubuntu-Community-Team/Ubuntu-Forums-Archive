---
title: "Block access to VNC except localhost"
date: 2008-01-12
forum: General Help
---

### Post by MrGrey1 on 2008-01-12
Ubuntu 7.10, SSH setup and working with encryption key and tunnelling for VNC.

Problem is that I can still access VNC without having to encrypt/tunnel on the local network. 
hosts.allow= "vnc: localhost"
hosts.deny= "vnc: ALL except localhost"
I have also tried a number of other hosts.deny/allow setups but nothing I have entered has made any difference to VNC. I have even denied ALL and it's made no difference as I can still access VNC by going to the ip address: port#. I extrapolate that the hosts files do not effect VNC at the moment.
How do I get the hosts.deny/allow to apply to VNC?
(I'm using the default Ubuntu VNC program.)
Any help would be greatly appreciated.
Thanks.

---

### Post by Herman on 2008-01-12
Oops, on reading your question again it seems as if it's more complicated than I thought, sorry, answer cancelled. Regards, Herman :)

---

### Post by MrGrey1 on 2008-01-12
I just want to disable all access to the vino-server except from localhost.

I have tried configuring the hosts.deny and hosts.allow files but they have had no effect.

---

### Post by Herman on 2008-01-12
Hello MrGrey1               
I'm not sure, you are doing something far more advanced than anything I've tried yet.  I feel out of my depth here.

SSH uses port 22 by default and VCN seems to use port 5900, so maybe just closing port 5900 would work? 

Take my answer with a large grain of salt. 

As I'm sure you're already well aware, you'll be able to see which ports you have open from another Ubuntu computer in your LAN using your 'System'-->'Adminstration'-->'Network Tools', and use the Port Scan tab.
So you can confirm if it's port 5900 and  verify when it's open and when it's closed that way, just enable vcn and disable it again in the machine that's acting as the vnc server and scan from the other computer each time.

I hope I'm being helpful, but maybe that answer doesn't make any sense at all.
Regards, Herman :)

---

### Post by MrGrey1 on 2008-01-12
Thanks for your time Herman.
I have actually moved ssh to a port that's a little more obscure, up in the 40000 range. Security through obscurity and all that. VNC is still on the default 5900 as I haven't figured out how to change that yet. 
There are a number of tutorials and how tos around that all talk about installing other vnc programs etc and some mention that vnc needs to be started with inetd or xinetd but there are no straight forward instructions on how to get the default VNC client in Ubuntu working properly with hots.allow and hosts.deny. In winblows the hosts allow etc are built into the VNC server and it takes a couple of minutes to configure and secure it properly, I've spent days now trying to figure out Ubuntu's config and it's getting a little tiresome. 
Essentially I don't want to have to install another VNC client as I already have the built in one working with an encrypted key over ssh and don't want the hassle of having to configure another VNC server. I just need to know how to stop access to the vnc server or vino server that comes with Ubuntu from everywhere except from localhost.

---

### Post by Herman on 2008-01-13
Okay, this is really interesting, but networking's my weakest subject. This is a good opportunity for me to learn something.

Okay, so I'm beginning from a simple approach, (mainly because I don't really know what I'm doing).
I have three computers here right beside each other. 
The first one had vncviewer enabled in it.
I have Firestarter installed in that computer, so I don't need to know anything about IPtables or hosts.allow or host.deny. 
I'm going to study that soon, sorry, I'm embarrassed that I haven't learned that yet, but there are so many things to learn all at once.
Using Firestarter might be a good way for me to get the basic idea before I progress to using IPtables properly.

Now, let's pretend I want to use vncviewer, but I only want to allow my third computer to access my first computer through port 5900 and no other port.

I open Firestarter, and I click on the policy tab.
I set the Editing spinbox to 'Inbound traffic policy', then I right-click in the bottom field titled 'Allow service', and click 'add rule'.
Up pops a window titled 'Add new inbound rule'
vnc isn't listed in the drop-down box when I click on the arrow for the 'name' field, so I'll skip that one for now.
I type '5900' in the 'Port' field, and the letters 'VNC' automatically appear in the 'Name' field.
Next, I click the radio buttom for 'When source is', and type the IP address of my third computer, which is the only one I want to allow to use this service.
...and I click the 'Apply policy' button in the toolbar.

Right, so I go to computer number 3, and I try to make a vnc connection to computer number 1... YES! :) No worries!
Okay, I'll close that again for now.

Let's see if I can connect to it from computer number 2. I don't expect so....
No, it can't seem to connect.

If I wanted to disallow any computer in my LAN and only allow traffic from my router, or from my broadband modem if I didn't have a router, I imagine I could have done that by typing the router's IP address into the rule I set up in Firestarter instead of the IP address for my third computer.
I think that's what you're trying to do, isn't it?

Now, let's take a look at my IP tables and my hosts.allow and hosts.deny and see what Firestarter has done there for me.

Well it hasn't touched either the hosts.allow or the hosts.deny files, 

but it has edited my IPtables, It has added these two lines, 
```
Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
[COLOR=Sienna][B]ACCEPT     tcp  --  192.168.0.174        anywhere            tcp dpt:5900 
ACCEPT     udp  --  192.168.0.174        anywhere            udp dpt:5900 [/B][/COLOR]
LSI        0    --  anywhere             anywhere 
```Here's my new IPtables, just in case you need to see where that fits in, Firestater certainly does a lot of work to IPtabels, it looks far too complicated for me,
```
herman@ubutesttwo:~$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  BigPond.bigpond      anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  BigPond.bigpond      anywhere            
ACCEPT     tcp  --  192.168.0.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.0.1          anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  anywhere             192.168.0.255       
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.0.160        BigPond.bigpond     tcp dpt:domain 
ACCEPT     udp  --  192.168.0.160        BigPond.bigpond     udp dpt:domain 
ACCEPT     tcp  --  192.168.0.160        192.168.0.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.0.160        192.168.0.1         udp dpt:domain 
ACCEPT     0    --  anywhere             anywhere            
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
OUTBOUND   0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  192.168.0.174        anywhere            tcp dpt:5900 
ACCEPT     udp  --  192.168.0.174        anywhere            udp dpt:5900 
LSI        0    --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       0    --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere            
```I imagine you can apply the same principles to your situation, hopefully anyway. I suppose you'll just need to substitute your own IP number and port number.

If you know all about IP tables, you're better than me, if you want to cheat like I did, try Firestarter.
If you want to learn IPtables, here are a few of the best links I have found but not studied well enough yet, 
[HOWTO: iptables (part one of three)]("http://forums.debian.net/viewtopic.php?t=16166") Debian User Forums - This one is easy to follow
[HOWTO: Set a custom firewall (iptables) and Tips]("http://ubuntuforums.org/showthread.php?t=159661&highlight=ip+tables") . - By frodon - more comprehensive
[IptablesHowTo]("https://help.ubuntu.com/community/IptablesHowTo") - Ubuntu Community Docs - An introduction to the powerful Linux IPTables firewall, 
[Iptables Tutorial 1.2.2]("http://iptables-tutorial.frozentux.net/iptables-tutorial.html") by Oskar Andreasson. Comprehensive.

Regards, Herman :)

---

### Post by MrGrey1 on 2008-01-13
Thanks for that Herman but not quite what I'm trying to achieve. I don't want to allow any connections from a network ip. I only want access from the local machine which will mean the only way to connect to the vnc is via ssh. I have made progress however. Credit to: [http://www.bani.com.br/2007/04/25/hidden-features-of-vino-remote-desktop-access/](http://www.bani.com.br/2007/04/25/hidden-features-of-vino-remote-desktop-access/)

How to change the default VNC port and set to allow access only from localhost:
Command: gconf-editor
Navigate to Desktop-Gnome-Remote_Access
Set the alternative_port to what ever you want and tick use_alternative_port.
Tick local_only to only allow connection from the local host.

I thought I was home free after discovering this but now I have discovered that if I turn on the local_only switch then I get "the connection closed unexpectedly" when trying to connect. :(
The other switches all seem to work properly... *sigh* from one problem to another.

EDIT::

I have since discovered that turning the switch "local_only" on/off resluts in the localhost port being blocked/unblocked as can be seen from nmap below. This is not what's supposed to happen. This appears to mean that the local_only switch is blocking localhost as well as everything else?

nmap with local_only off:

******@******$ > nmap -p5900 localhost
Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-01-14 00:33 WST
Interesting ports on localhost (127.0.0.1):
PORT     STATE SERVICE
5900/tcp open  vnc
Nmap finished: 1 IP address (1 host up) scanned in 0.273 seconds

nmap with local_only on:

******@******$ > nmap -p5900 localhost
Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-01-14 00:33 WST
Interesting ports on localhost (127.0.0.1):
PORT     STATE  SERVICE
5900/tcp closed vnc
Nmap finished: 1 IP address (1 host up) scanned in 0.108 seconds

EDIT 2:
The problem with "local only" switch has turned out to be that it's blocking all ip4 connections and only allowing the localhost connection on ip6. The issue is that I can't work out how to get vnc in combination with ssh to run on ip6. I'm not sure if it's the vnc part that needs ip6 or the ssh part that needs ip6? I'm betting on it being the vnc at the moment... 

******@******$ > nmap -6 ::1
Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-01-16 22:31 WST
Interesting ports on ip6-localhost (::1):
Not shown: 1696 closed ports
PORT     STATE SERVICE
5900/tcp open  vnc


EDIT 3:
I have now got the vnc/ssh tunneling in to localhost working from another ubuntu box.

ssh -i /path/to_your/masterkey 192.168.*.* -p ***** -L 5900:[::1]:5900

vncviewer loclahost

The trick was to set the tunnel to go to  ipV6 localhost address of [::1]. I haven't been able to get winblows and putty to work as yet and have tried all combinations of tunneling that I can think of. I must be missing something.

---

### Post by MrGrey1 on 2008-07-18
I had the same problem as above in 8.04 using the vnc client and options that are installed by default. I have finally found an alternate solution that works on 8.04

1. Disable Desktop Sharing under System -> Preferences -> Remote Desktop
2. sudo apt-get install x11vnc
3. sudo x11vnc -storepasswd yourpasswordhere /home/USER/.x11vnc.pass
4. sudo gedit /etc/gdm/Init/Default
5. add this line to the bottom above exit: /usr/bin/x11vnc -rfbauth /home/USER/.x11vnc.pass -o /tmp/x11vnc.log -forever -localhost -bg -rfbport 5900
6. sudo gedit /etc/gdm/gdm.conf-custom and add "KillInitClients=false" under section [daemon] so you don’t get your session killed after you log in (without the "")
7. restart

This will enable you to vnc to the login screen and login but only from localhost ie you will have to tunnel using ssh to localhost:5900. If you combine this with encrypted key access to ssh it will give you a secure vnc session from anywhere. If you remove the -localhost tag in step 5 you can connect from any ip. Like wise you can add -192.168.1.1 etc just after localhost to specify only certain ip addresses access. Also of course change the default port from 5900 to what ever.

Thanks to fiskpinnen for this advice
[http://ubuntuforums.org/showthread.php?t=191564&highlight=vnc+gnome&page=8](http://ubuntuforums.org/showthread.php?t=191564&highlight=vnc+gnome&page=8)

---

