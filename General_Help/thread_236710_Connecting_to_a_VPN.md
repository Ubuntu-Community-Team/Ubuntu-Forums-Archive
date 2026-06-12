---
title: "Connecting to a VPN"
date: 2006-08-15
forum: General Help
---

### Post by Rushed Luncheon on 2006-08-15
Hello,

I have used Ubuntu for the last few months, and found it works excellently in almost every situation. However, I recently subscribed to a service called RELAKKS. It is a means to both surf the Internet and use online applications accross an encrypted connection via a Swedish IP address. This basically means I have the utmost in privacy when online thanks to the spectacular Swedish privacy laws.

The website for the service is [https://www.relakks.com/](https://www.relakks.com/)

The website gives a guide for how to set up the connection in Windows XP, and it also gives a guide on how to set up the connection in Mac OS X. Now, I have a working connection on my Macbook, but I want to keep using Ubuntu on my main desktop rather than return to XP. 

Can anyone help me set up the VPN connection to the RELAKKS service in Ubuntu? The VPN connection uses PPTP.

So far I have tried the following things:
[LIST]
[*]install vpnc (but I cannot configure it for PPTP as I do not know how)
[*]googled many terms such as "vpnc pptp" or "vpnc configuration" but to no avail
[*]tried to get Network Manager to support VPN using another thread - this was unsucessful
[/LIST]

I really would like to get this secure, encrypted and private connection working - especially as I am paying 6 euros per month for it ;)

Many thanks,
Ben

PS: If anyone can help me write a vpnc configuration file, please use "ben" as the username and "p455w0rd" as the password, just for demonstration purposes. I expect any other information you need could be garnered from the RELAKKS guides for XP and Mac OS X.

---

### Post by peRosine on 2006-08-15
HOWTO (with help from PTPP Client homepage):

**1: Install PPTP Client:**
```
sudo apt-get install pptp-linux
```

**2: add the following lines to the sources list file, ***/etc/apt/sources.list* :

```
# James Cameron's PPTP GUI packaging
deb http://quozl.netrek.org/pptp/pptpconfig ./
```

**3: Update and install **
```
sudo apt-get update
sudo apt-get install pptpconfig

```

**4: Configure with your account-info:**
```
sudo pptpconfig
```

P.S.: Don't forget to put "All to tunnel" at the routing tab.

**5: It works... you can close pptpconfig.**

---

### Post by Rushed Luncheon on 2006-08-15
Thank you very much for your help.

I followed your instructions to a tee, however, the pptpconfig tunnel does not connect. I receive this sequence in the log over and over again.

> Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/1
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
Using interface ppp0pptpconfig: monitoring interface ppp0
I notice it says modem hangup, but I do not use a modem. This is a VPN using PPTP over my broadband connection.

---

### Post by Geoff2077 on 2006-08-15
Give up mate - no one on these forums has a clue about vpn.Always the same setup information copied from someone else who doesn't know.

I have been trying for weeks to get vpn to work. When I run the setup it tells me I am connected - but there appears to be no way to actually view the folders on the remote server.

Google is not much help either.

Cheers and good luck...

---

### Post by peRosine on 2006-08-16
I wish I knew what was causing this error.

Maybe you should look at your network settings and disable your modem connection and only keep your LAN connection.

I can only tell you that what I described above worked for me, I'm now running the Relakks service. Hope you also get it working.

---

### Post by geraner on 2006-08-16
I get it running.

Use the following configuration in the pptconfig

> 
Name: Relakks
Server: pptp.relakks.com
Domain:
Username: your username you got after registration at [www.relakks.com](www.relakks.com)
Password: your password


But when I'm on the internet, it still shows my ISP's IP Adress when I check it under "http://www.whatismyip.com".

How to get it 100% running?
The connection seems to be ok.

Regards
Geraner

---

### Post by peRosine on 2006-08-16
> 
How to get it 100% running?
The connection seems to be ok.


Put "All to tunnel" at the routing tab. And it should work.

---

### Post by ProjectGod on 2006-08-16
VPN to windows VPN server, been trying a long time. but it doesnt work.

such a shame.

---

### Post by yamasaki on 2006-08-16
i am able to connect to my corporate vpn server using pptpconfig, however

1) you have to start pptpconfig via 'sudo' as it needs roots permissions in order to function properly  (it puts an icon under Applications->Other)

2) i noticed my default route was changed by pptpclient, however, it was set incorrectly, i had to go in there and manually add a new default route using 

`sudo route add default gw xxx.xxx.xxx.xxx`

i just started using pptpclient a few minutes ago, these are the 2 things ive found so far.  i am also connecting to a windows vpn server.  i can ping boxes inside my corporate lan, but it's not working 100% yet.  i'll follow up with some more insight as i get time to try and get this working right.  hopefully more tonight.

Regards.

---

### Post by 1oki on 2006-08-18
> **Geoff2077 said:**
> Give up mate - no one on these forums has a clue about vpn.Always the same setup information copied from someone else who doesn't know.

I have been trying for weeks to get vpn to work. When I run the setup it tells me I am connected - but there appears to be no way to actually view the folders on the remote server.

Google is not much help either.

Cheers and good luck...

I got mine working no problem... I have all tunnel working fine, and I can surf the net. I am pptp'ing to my house because I blocked some websites for users (but I want to be able to use them myself ;) ) So I vpn to my home windows box and am able to browse :) Followed the directions and works beautifully!

---

### Post by 1oki on 2006-08-18
Also... It may sound stupid, but you want to check the little things! Make sure firewalls are either down or allow for passthrough of the pptp port (1723 I belive), and that the router is allowing passthrough of pptp protocal. Also, you are going to want to setup the port forwarding on your router... I know these are simple things and I might be insulting someones intelligence with this post, but the simplest things are usualy the most over looked! good luck all!:rolleyes:

---

### Post by marianom on 2006-08-19
Hi everyone. I see geraner could make it work with 6.06. I'm still stuck in the error that it cannot be install due to a "php-gtk-pcntl" problem (Dependency is not satisfiable: libglade0). This is while installing "pptpconfig"
I logged in the pptpclient mailing list to search for solutions and it was suggested that the package was selfcontained in the site so I downloaded it myself (not through apt) but I still got the same error upon installing.

Do you guys have any suggestion in order I can make it work?
Thanks in advance.

---

### Post by 1oki on 2006-08-21
> **marianom said:**
>  I'm still stuck in the error that it cannot be install due to a "php-gtk-pcntl" problem (Dependency is not satisfiable: libglade0).

did you try to install php-gtk-pcntl or libglade0? :D If not I would try to install them and try to reinstall pptpconfig again!

---

### Post by 1oki on 2006-08-21
Also... I just followed the directions again on another ubuntu box of mine and I had no problems. Though as I was installing I did get this message

"WARNING: The following packages cannot be authenticated!
  php-gtk-pcntl php-pcntl pptpconfig
Install these packages without verification [y/N]? y
"

As you can see I just choose yes and it installed perfectly!

---

### Post by marianom on 2006-08-21
I cannot believe it!!!!! I never get that message. Uffffff.....

Nevertheless, it seems you're a 5.10 user. I'm in 6.06. Maybe it's a version problem. Geraner is a 6.06 user so that's why I asked.

Anyway thanks a lot for your input. Really appreciate it. 
If there's somebody who succesfully made it on 6.06, tips are welcome.

---

### Post by 1oki on 2006-08-21
Nope... Im a 6.06 user... Just havent updated my user profile :)

---

### Post by 1oki on 2006-08-21
Just to show you that it does work,,, here is a screen shot I took while starting up the pptpconfig! I cant connect to my pptp server at home from this location because I am sitting behind a hospital firewall that is blocking all my connections and dont have an outside ssh server setup yet 8)

oh yeah, click on the thumb to get the full picture!

---

### Post by marianom on 2006-08-21
Hey thanks a lot but there was no need for the screenshot: I have no doubt you did it.

Seeing it's possible I just have to figure out how I can do it myself.

---

### Post by 1oki on 2006-08-21
well have you tried installing those individual Dependencies by your self? I asked that before, but you didnt answer... If you didnt, try to. because they are, well, dependencies and the program will not work with out them. I belive my php-gtk-pcntl came when I ran the apt-get install pptpconfig. Im not sure when the libglade0 was installed. libglade0 and php-gtk-pcntl are avalible in repository. So if you want to run an "sudo apt-get install libglade0 php-gtk-pcntl" or do it through synaptic, you should be able to get it.

here is the description for libglad0:

Library to load .glade files at runtime
This library allows you to load user interfaces in your program, which are stored externally.  This allows alteration of the interface without recompilation of the program.

The interfaces can also be edited with GLADE.

heres the description of php-gtk-pcntl:
GTK+ bindings for applications built using php-pcntl
PHP-GTK is an extension for PHP programming language that implements language bindings for the GTK+ toolkit.  It provides an object-oriented interface to GTK+ classes and functions and greatly simplifies writing client side cross-platform GUI applications.  This version is built against the minimal PHP version with process control (php-pcntl) and requires that package to be installed too.


Try installing and see where that gets you.

---

### Post by marianom on 2006-08-21
Yes, actually I tried. 
I downloaded php-gtk-pcntl_1.0.0-2_i386 and pptpconfig_20060410-0_all.
libglade0 is harder since I'm still looking for it.
Do you know where I can get it?

---

### Post by marianom on 2006-08-21
I forgot to mention that while doing 
"sudo apt-get install libglade0 php-gtk-pcntl "
it tells me that libglade0 has no candidate for its installation (I'm doing a literal translation from spanish so maybe the official message in english might be different).
That's why I'm looking for the package myself on the net.

---

### Post by 1oki on 2006-08-21
well I belive the libglade0 is avalible under the universe repository. that is what Im getting in the package search. Mozilla search engines (Ubuntu Packet Search). If for some reasion you dont have universe allowed in the apt-get you have to edit the source list (/etc/apt/sources.list, and delete the # in front of:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

than save it and do an apt-get update and than try the apt-get install " "

If that doesnt work, check this site out:
[http://packages.ubuntu.com/warty/libs/libglade0](http://packages.ubuntu.com/warty/libs/libglade0)
and
[http://packages.ubuntu.com/warty/source/libglade](http://packages.ubuntu.com/warty/source/libglade)

its the ubuntu package search resultes for libglade0. On the bottom there are a number of links for download (its under ther bold DOWNLOAD). The source is here:
[http://archive.ubuntu.com/ubuntu/pool/main/libg/libglade/libglade_0.17.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/libg/libglade/libglade_0.17.orig.tar.gz)

hope it helps

---

### Post by marianom on 2006-08-21
Yes, I've already tried uncommenting the universe repository with no luck. However I did not try the second part of your suggestions. I will follow them to see if it's possible.

Thanks again for your time. I'll let you know how it goes.

---

### Post by 1oki on 2006-08-22
How did it turn out?

---

### Post by Geoff2077 on 2006-08-22
to overcome the missing dependencies for pptpconfig, I found that I had to enable the user supported Universe. This is not enabled by default when you do clean installation of ubuntu.

I come back to my earlier comment though - the pptpconfig tells me I have connected to the office server (ms sbs2000), but I can still find no instruction on how to view the folders on the server.

I am not block by firewall. I can easily connected from a second PC that runs XP. After establishing the vpn connection, all I need to do is Run "\\192.168.16.2" which is the address of the server. An explorer window opens and the folders are accessible.

Anyone know what the trick is for Ubuntu??? 


There are too many things in Ubuntu/Linux that take forever to get working. Until such time as the designers address this, Linux and Ubuntu and the rest remain toys. If it were otherwise, people would be using Linux in the office in far greater numbers. People are not stupid - they are not fooled by the hype around Linux. That' why they pay heaps of money to Bill Gates - because MS concentrate on getting the little things working easily for the majority of users.

I suspect that other software and hardware companies are reluctant to provide much support for Linux based systems for related reasons. A continually moving target. eg what works on ubuntu 5.1 suddenly does not work on 6.01 and so it goes on.

---

### Post by 1oki on 2006-08-23
> **Geoff2077 said:**
> to overcome the missing dependencies for pptpconfig, I found that I had to enable the user supported Universe. This is not enabled by default when you do clean installation of ubuntu.

I come back to my earlier comment though - the pptpconfig tells me I have connected to the office server (ms sbs2000), but I can still find no instruction on how to view the folders on the server.

I am not block by firewall. I can easily connected from a second PC that runs XP. After establishing the vpn connection, all I need to do is Run "\\192.168.16.2" which is the address of the server. An explorer window opens and the folders are accessible.

Anyone know what the trick is for Ubuntu??? 


There are too many things in Ubuntu/Linux that take forever to get working. Until such time as the designers address this, Linux and Ubuntu and the rest remain toys. If it were otherwise, people would be using Linux in the office in far greater numbers. People are not stupid - they are not fooled by the hype around Linux. That' why they pay heaps of money to Bill Gates - because MS concentrate on getting the little things working easily for the majority of users.

I suspect that other software and hardware companies are reluctant to provide much support for Linux based systems for related reasons. A continually moving target. eg what works on ubuntu 5.1 suddenly does not work on 6.01 and so it goes on.



Soooo how much did micro$oft pay you to say all that? lol As far as the amount of people who use linux in the work place. Its far more numberous than you think. I have a work crew of almost 200 people using linux. Its networked and all! The only problem with Linux is that the common people dont understand it, and this is where it gets confusing to someone who has been tainted by the M$ project for the past 20 years. I myself is included in that! But, I am learning more and more every day about linux and feel quite comfortable where I know I can figure things out with time. I also try to spread my findings to others so they dont have to struggle with the same thing I did, hence this forum.

Now, back to the problem at hand. It is to my understanding that you want to be able to browse your Ubuntu box from the windows box you pptp'd into? 
Do you have samba installed? If so did you change the workgroup on your Ubuntu box to match that of your xp box? Now that you mention it... I am trying to get it working myself. I will post back with all the things I have done. :twisted: 

-l

p.s. I agree with you that linux can be hard... didnt you read my signature   \/  ? lol

---

### Post by 1oki on 2006-08-23
okie dokie, figured it out... well you cant browse your network and see the computer for obviouse reasons... but you can map shared drives on your Ubuntu box to windows... better than nothing right?

found it at this thread:

[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=map+share+folder+ubuntu+windows](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=map+share+folder+ubuntu+windows)

you have to create a share folder and actualy right click on that folder in the File Browser and setup the share options for that folder. 

I am still working on the whole browsing thing. I will be back later with a ya or nay on it.

---

### Post by Geoff2077 on 2006-08-24
Hi,
Dont be mislead by my frustration - I am certainly not endeared to MS. I came to Ubuntu with heaps of goodwill and hope and am not going to give up. I appreciate that it is a steep learning curve and I started at base station zero. But until you get the foundations built, there is no point building the house!

I run pptpconfig and it appears that the vpn connection to our SBS2000 server is established. I can ping the server, ie the router that interfaces to the internet. This has been the status of progress for at least 2-3 weeks.

I have not been able to find out either on forums or on google, any guidance on how to take the final step, which is to actually view the folders on the server. As I pointed out, with MS it is also 2 step process for VPN. Establish the connection and then a simple run directive: \\192.168.16.2 which gives me the viewing of folders. It is this last step that is not dealt with anywhere I can find for ubuntu/linux. 

Is there some additional s/w I need to run. What about Samba? I would have thought that nautilus (explorer) would be the way to go but this seems not the case.

The adsl router at the server end is 192.168.1.157 and this acts as DHCP for all PC's on the network. The server itself is 192.168.16.2 and this is the one I want to view folders on. 
 

Cheers
Geoff

---

### Post by Geoff2077 on 2006-08-24
further to my comments on Linux in a working environment..

[http://www.ubuntuforums.org/showthread.php?t=182871&highlight=vpn](http://www.ubuntuforums.org/showthread.php?t=182871&highlight=vpn)

---

### Post by jecos on 2006-08-24
Mandriva wrote a new frontend for vpn connections called Drakvpn, they also have links to other frontends that will help

[http://qa.mandriva.com/twiki/bin/view/Main/DrakVPN](http://qa.mandriva.com/twiki/bin/view/Main/DrakVPN)

---

### Post by marianom on 2006-08-25
> **1oki said:**
> How did it turn out?

Hi, 1oki. Sorry for the late reply but an urgent job kept me away from this issue until today. Following your advice, I was able to download libglade0 from the site and installed it successfully. I've got pptpconfig running and I'm configuring it as I write.

Thanks again for the advices and your time. Take care.

---

### Post by 1oki on 2006-08-28
Geoff I don't believe there is anyway to actively view a ms network from ubuntu... Like you stated before, there are no guides or even anyone that I could find that knows how to do this! The only thing I could suggest is sharing the MS folder and mapping it on ubuntu. 

Samba is the Linux version of the smb protocol utilized by MS. It allows for linux and windows to communicate and share things such as folders, etc. It can also act as a domain controller if you configure it right. [http://us4.samba.org/samba/](http://us4.samba.org/samba/) for more info... don't be afraid of it! Its not that hard to play with. There are plenty of guides and howto's out there!

Just a point of curiosity... why would you like to have the MS network browseable? If its for a corporate environment wouldn't it be easier to just mount the shared folders? Or if its for home, you already know what all the shares are so you could just mount them whenever you want to!

---

### Post by 1oki on 2006-08-28
> **marianom said:**
> Hi, 1oki. Sorry for the late reply but an urgent job kept me away from this issue until today. Following your advice, I was able to download libglade0 from the site and installed it successfully. I've got pptpconfig running and I'm configuring it as I write.

Thanks again for the advices and your time. Take care.

Hope it works for you! :wink:

---

### Post by marianom on 2006-08-28
> **1oki said:**
> Hope it works for you! :wink:

I still have problems but this time it's on the server side. Now I need to talk with xxx-Xxxx-Xxxxx-xxxx-xxx that runs the server and see if we can make it work.](*,) 

Regards.

---

### Post by zooounds on 2006-08-29
When I use Relakks the tunnel works fine but my I cant get any DNS answer so surfing gets really hard ...

Any suggetions?

---

### Post by 1oki on 2006-08-29
hmm I dont use relakks... so I wouldnt know... try PM'ing one of the original guys who started this thread...

---

### Post by Geoff2077 on 2006-08-30
Thanks 10oki. VPN is the only remote access option I have to the office server. I want to be able to access files on the server from home.

reading between your lines - am I somehow going about this the wrong way? Certainly I can vpn from my WinXP box and explore the server files. I do see quite a lot of enquiries to the user forum asking the same question as myself.

Then there are the heaps of questions relating to the cisco server. But I suspect that here, they use some other means to access the server files, after the vpn connection is established.

cheers

I thought Samba was intended for sharing files from my Ubuntu box, ie as server, rather than client.

---

### Post by 1oki on 2006-08-30
well samba is intended for sharing of files between linux and windows, either way you look at it you need it to share... 

I established a vpn to my home xp box, and mapped a folder that i already have shared on the xp box to my ubuntu box. I am able to access all the files on that share and use and edit them as I see fit! They happen to be music files, so i listen to them or transfer them to my ubuntu to burn while at work. Is this something that you are looking to do? If so I can tell you how I did it... its not that hard... I dont see any other way of accessing files from a windows machine. In essence the networking is pretty strait forward... You have to have a shared folder on another machine in order to access those files! its that way with windows and linux... 

Let me know if you want me to show you how to mount the shared folder!

---

### Post by alo_joe on 2006-09-03
Hi,

I have also a problem with pptpconfig. I get connected to the server, but when I ping I get 100% lossed packages. I can not acces the data. Anybody has any idea.

Thanks

Alonso

---

### Post by 1oki on 2006-09-05
what type of tunnel are you running? lan to lan, all tunnel, etc...?

---

### Post by xinel on 2007-05-04
> **zooounds said:**
> When I use Relakks the tunnel works fine but my I cant get any DNS answer so surfing gets really hard ...

Any suggetions?

I have the same problem, I just e-mailed off a message to Relakks asking if they have any idea's. Will report back if they tell me a fix.

---

### Post by nonsense28sal on 2007-05-15
I was able to get Relakks working using the GUI Network manager under Kubuntu Feisty.

First, make sure Knetwork Manager and KVpnc are installed through Synaptic or whatever package manager you prefer.  Once it's installed, right click on the Knetwork manger icon in the system tray.  It looks like the plug of an Ethernet cable. Go to VPN Connections and configure.  Add a new connection.

Choose the following options:

Under Connection:
Connection Name: Relakks
Type: Windows (VPN) PPTP
Gateway: pptp.relakks.com

Under Authentication:
Of the options check only "Refuse EAP".
("Refuse Chap" "Refuse MS Chap" and "Authenticate Peer" should all be unchecked).

Under Compression & Encryption:
ONLY CHECK "Require 128 bit MPPE encryption"

Under PPP Options:

Check:

"Use Peer DNS"
"Exclusive Device Access (UUPC Style lock)"

For the following fields:

MTU 1400
MRU 1416
lcp-echo-failure 10
lcp-echo-interval 10

Under Routing:
Check
"Peer DNS through Tunnel"

That's all I had to do and it works well.  One caveat:  it does not work with my WRT54G2 router.  I have to plug my Linux box directly into my cable modem for it to work properly. Although, this is not just a problem with Linux as I have this same issue on Windows. YMMV

Slight update:

I did a fresh install of Kubuntu Feisty at work today and wanted to see if I could get Relakks working from scratch.

There is a [bug]("https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/74351") in knetworkmanager that requires network-manager-gnome in order to configure VPN.

I also had to install the following packages on the fresh install:

knet, network-manager-dev, network-manager-openvpn, network-manager-pptp, network-manager-vpnc, pptpd, pptp-linux, ipppd

After I installed the packages, I went ahead and rebooted. After that, with the instructions already posted above, I was able to connect to Relakks.

---

### Post by NewbieNik on 2007-05-16
> **Geoff2077 said:**
> Give up mate - no one on these forums has a clue about vpn.Always the same setup information copied from someone else who doesn't know.

I have been trying for weeks to get vpn to work. When I run the setup it tells me I am connected - but there appears to be no way to actually view the folders on the remote server.

Google is not much help either.

Cheers and good luck...

How useful this was!!!
Anyway, us who know nothing about VPNs will try to help.
I am using Edgy and have installed the network-manager-pptp module through synaptic (Includes the pptp-linux kernel). This gives you a VPN configure option under network manger icon on the menu-bar.

The IP set-up is quite simple if you already have the details and as long as the Remote-Access Server gives you permission to use it as a gateway (Which it seems is it&#347; purpose so should&#324;t be an issue) you should be rocking. (Although I did have to reboot my machine, but that&#347; a small price to pay)

---

### Post by 1oki on 2007-05-17
yes, this does work... It was the same exact way I set up my VPN a while back. People just don't want to believe others might know a way to do something that they don't... Oh well! They get left behind and we all advance.

---

### Post by dpsguard on 2007-05-27
Hi All,

I am trying to set up PPTP to a work firewall gateway (Ip address and user / password is the only info I have).

When I create a PPTP, thru GUI Network Manager, VPN Connections, Configure VPN, Add, I supply the required info, it tells me that PPTP connection will be created but when I try to establish VPN, it complains that there was an error in validating connection and that VPN connection was not properly configured and then it kills the network manager icon (and I have to do sudo networkmanager to bring it back and then when I try to verify settings / try some changes, I do not see the entry under VPN Connections to edit. I do see the stale entries when I click network manager icon and I can not remove those entries even. How do I remove the old connection entries? And many times, when I am trying to configure a new VPN connection, after the last step giving me the summary info of the configuration, I do not see that entry appear. 

Any assistance will be greatly appreciated.

---

### Post by Tickle Me Elmo on 2007-06-16
Will this work on Ubuntu 7.04? One of the reasons I didn't start using Ubuntu on my laptop is that I didn't get the connection to Relakks to work. Being able to connect to the Relakks VPN via Gnome is something that I value.

---

### Post by PacDwell on 2007-07-10
> **dpsguard said:**
> Hi All,

I am trying to set up PPTP to a work firewall gateway (Ip address and user / password is the only info I have).

When I create a PPTP, thru GUI Network Manager, VPN Connections, Configure VPN, Add, I supply the required info, it tells me that PPTP connection will be created but when I try to establish VPN, it complains that there was an error in validating connection and that VPN connection was not properly configured and then it kills the network manager icon (and I have to do sudo networkmanager to bring it back and then when I try to verify settings / try some changes, I do not see the entry under VPN Connections to edit. I do see the stale entries when I click network manager icon and I can not remove those entries even. How do I remove the old connection entries? And many times, when I am trying to configure a new VPN connection, after the last step giving me the summary info of the configuration, I do not see that entry appear. 

Any assistance will be greatly appreciated.

I noticed that if I create a VPN with a space in the name it won't list it in the VPN connections, but it will leave the 'stale' entry. Creating it with no space seems to work OK. I don't know how to remove the stale entry though, I'm hoping someone can direct me to the appropriate file.

---

### Post by Torgeir on 2007-07-16
Hello! Have been using 7.04 since April, and Relakks is working close to perfect using NetworkManager 0.6.4. But there are some small problems:

 When using Relakks, I'm not able to access several URL's e.g.: [www.expressen.se](www.expressen.se), [www.vg.no](www.vg.no), [www.thepiratebay.org](www.thepiratebay.org), [www.aftenposten.no](www.aftenposten.no), [www.nrk.no](www.nrk.no). Without Relakks - no problem!!

When I try to ping the adresses, the responses are different
The Pirate Bay: 64 bytes from thepiratebay.org (83.140.176.146): icmp_seq=1 ttl=59 time=246 ms 
                         64 bytes from thepiratebay.org (83.140.176.146): icmp_seq=2 ttl=59 time=242 ms
                         64 bytes from thepiratebay.org (83.140.176.146): icmp_seq=3 ttl=59 time=241 ms


Aftonbladet: () From 192.71.238.14 icmp_seq=2 Packet filtered
                        From 192.71.238.14 icmp_seq=5 Packet filtered
                        From 192.71.238.14 icmp_seq=8 Packet filtered

NRK: PING nrk.no (160.68.205.231) 56(84) bytes of data.

--- nrk.no ping statistics ---
16 packets transmitted, 0 received, 100% packet loss, time 15000ms

 Any idea how to configure this, since I'm stucked behind a proxy in an Arabic country.

FYI: Relakks is working perfect in Windows -> i.e. router should be ok!

:guitar:

Torgeir
- +42 C in the air and +36 in the sea!!

---

### Post by 1oki on 2007-07-16
Whether I agree with it or not does not matter. I personally am not going to help you download things... Clearly wherever you are does not want people downloading torrents from sites such as Pirate bay... and if you really wanted to get around the proxy one could apply themselves a bit and figure it out... Sure this is a help forum, but not a help forum for pirating...That what IRC is for. 

good luck in your endeavor.

---

### Post by Torgeir on 2007-07-17
1oki: FYI: 3 of the URL's are to some of the biggest newspapers in Scandinavia. :confused:

The question is not about downloading - its about a possible error in Ubuntu implementation of the PTPP protocol!

Torgeir
- using Windows if I would like to download something!!:o

---

### Post by 1oki on 2007-07-17
Piratebay ;)

---

### Post by PartisanEntity on 2007-09-11
Someone please clue me in.

I am using Ubuntu (GNOME) on my laptop, I connect to the internet wirelessly using Network Manager to my home wireless router (a Netgear WGR614v5) which is in turn hooked up to my cable modem.

Can I use relakks this way or must I be connecting through ethernet?

p.s. according to the instructions posted quite recently in this thread, one should right-click on the network manager icon to set up a VPN connection, I cannot find this option when I right-click on network manager and I assume this is because I am connected wirelessly. Correct?

---

### Post by nemanaldin on 2007-09-20
hi all
i use ubuntu 7.04
i want connect to vpn and surfing internet anonymosly
i use dial up connection to surfing internet(ppp0)
i can connect to vpn server by kvpnc (i cant connect by network-manager or pptpconfig)
but when i connected i cant use internet and after few minutes i disconnected from vpn
this my settings in kvpnc
[IMG]http://i8.tinypic.com/4zmre40.png[/IMG]
and this is my ppp1(vpn )connectin 
[IMG]http://i3.tinypic.com/6aqpdll.png[/IMG]
i use dial up and my sent packets are 1.1 gb after few minutes!!!! and dont have any recieve 
thanks and sorry for my bad english

---

### Post by nemanaldin on 2007-09-21
nobody can help????!

---

### Post by Junzuki on 2007-09-26
> **PacDwell said:**
> I noticed that if I create a VPN with a space in the name it won't list it in the VPN connections, but it will leave the 'stale' entry. Creating it with no space seems to work OK. I don't know how to remove the stale entry though, I'm hoping someone can direct me to the appropriate file.

Get gconf-editor, start it from a terminal, navigate left pane - System>networking>vpn_connections. You should see all your vpn connections, select the one you want rid of then go to right pane and right click each entry and select "unset key", exit and check nm, they should be gone.

                      \|||/
                      (oo)
Linux --------ooO-(_)-Ooo-------- User

---

### Post by ejstacey on 2007-10-23
> **nemanaldin said:**
> hi all
i use ubuntu 7.04
i want connect to vpn and surfing internet anonymosly
i use dial up connection to surfing internet(ppp0)
i can connect to vpn server by kvpnc (i cant connect by network-manager or pptpconfig)
but when i connected i cant use internet and after few minutes i disconnected from vpn
this my settings in kvpnc
[IMG]http://i8.tinypic.com/4zmre40.png[/IMG]
and this is my ppp1(vpn )connectin 
[IMG]http://i3.tinypic.com/6aqpdll.png[/IMG]
i use dial up and my sent packets are 1.1 gb after few minutes!!!! and dont have any recieve 
thanks and sorry for my bad english
I've seen similar symptoms before.  This was when I was setting up Relakks manually through the /etc/ppp files (which I'm about to attempt again tonight).  It means your routing and or firewall are set up wrong, and you're routing all the packets in a loop to yourself.  It should spam a ton of packets and then disconnect.  Make sure you set up your routing properly.

---

### Post by sfenton on 2007-11-02
There is another service like this called surfbouncer. They use openvpn, so you can load the openvpn client to connect. All you need from their install program is the client.conf file. They cost more, but it may end up working better. [www.surfbouncer.com](www.surfbouncer.com)

---

### Post by zooounds on 2007-11-03
> **sfenton said:**
> There is another service like this called surfbouncer. They use openvpn, so you can load the openvpn client to connect. All you need from their install program is the client.conf file. They cost more, but it may end up working better. [www.surfbouncer.com](www.surfbouncer.com)

Interesting.

Relakks is working on a OpenVPN solution too.

---

### Post by coldstatue on 2008-01-27
nm

---

### Post by farahbod on 2008-03-23
Hi guys,
At last I can create a VPN connection to my work place using pptpconfig.
Thanks for helps in previous pages in this thread.

Still I need to add default route:
route add default gw 192.168.0.1 ppp0

However I do not want to use pptpconfig each time i want to connect.
Is there any way to start pptp connection and set route in an script? I mean:

#!/bin/bash
SOMETHING TO START ppp0
route add default gw 192.168.0.1 ppp0

and setuid that file as root, in order to be useful for others that not have root priviliges.

Could anybody help me with the "SOMETHING TO START ppp0" line?

Thanks in advance

---

### Post by farahbod on 2008-03-23
Now I know how to start the connection and where to store the route command! :)

Start:
pon ConnectionName

And create a file in the /etc/ppp/ip-up.d/ with the name of ConnectionName and the following content:

#!/bin/bash
route add default gw 192.168.0.1

Then do this:
chmod a+x /etc/ppp/ip-up.d/ConnectionName

To connect use this:
System>sudo pon ConnectionName

The problem now is that how could I connect without the need for "sudo"ing?! :confused:
Does any body have any idea? How about you "1oki"?

---

### Post by affected on 2008-03-30
Has anyone managed to get Relakks working on a headless box? I've tried to follow the various command-line how-tos google finds, but I can't figure it out. I've configured the pptp client manually as per several instructions, even got it to connect a couple of times only to immediately disconnect. Now the connection just times out when I try to open the pptp tunnel with the pon command.

---

### Post by 300890 on 2008-04-07
> **nonsense28sal said:**
> I was able to get Relakks working using the GUI Network manager under Kubuntu Feisty.

First, make sure Knetwork Manager and KVpnc are installed through Synaptic or whatever package manager you prefer.  Once it's installed, right click on the Knetwork manger icon in the system tray.  It looks like the plug of an Ethernet cable. Go to VPN Connections and configure.  Add a new connection.

Choose the following options:

Under Connection:
Connection Name: Relakks
Type: Windows (VPN) PPTP
Gateway: pptp.relakks.com

Under Authentication:
Of the options check only "Refuse EAP".
("Refuse Chap" "Refuse MS Chap" and "Authenticate Peer" should all be unchecked).

Under Compression & Encryption:
ONLY CHECK "Require 128 bit MPPE encryption"

Under PPP Options:

Check:

"Use Peer DNS"
"Exclusive Device Access (UUPC Style lock)"

For the following fields:

MTU 1400
MRU 1416
lcp-echo-failure 10
lcp-echo-interval 10

Under Routing:
Check
"Peer DNS through Tunnel"

That's all I had to do and it works well.  One caveat:  it does not work with my WRT54G2 router.  I have to plug my Linux box directly into my cable modem for it to work properly. Although, this is not just a problem with Linux as I have this same issue on Windows. YMMV

Slight update:

I did a fresh install of Kubuntu Feisty at work today and wanted to see if I could get Relakks working from scratch.

There is a [bug]("https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/74351") in knetworkmanager that requires network-manager-gnome in order to configure VPN.

I also had to install the following packages on the fresh install:

knet, network-manager-dev, network-manager-openvpn, network-manager-pptp, network-manager-vpnc, pptpd, pptp-linux, ipppd

After I installed the packages, I went ahead and rebooted. After that, with the instructions already posted above, I was able to connect to Relakks.

Won't work @ school, I think it's a routing problem.

631/tcp  open  ipp
1723/tcp open  pptp

I think those ports should be open in the router as well.

Any suggestions?

---

### Post by Ansible on 2008-04-07
I was unable to get pptp-config to do the job for me.  However, this did work:

[http://customisinglife.blogspot.com/2006/11/vpn-connection-in-edgy.html](http://customisinglife.blogspot.com/2006/11/vpn-connection-in-edgy.html)

The above post covers adding the VPN plugin to nm-applet, which I already use anyway as its the ubuntu default.  The VPN choices are right there in the applet instead of having to fire up pptp-config from the command line with sudo.  

Just in case the above link doesn't work someday, the installation process consisted of going into synaptic and installing  the "network-manager-pptp" package.

Only caveat is that after I added the VPN plugin and putting in my VPN information, it did not show up in the applet "VPN Connections" menu until after a reboot.  This is in ubuntu 7.10.

---

### Post by babulal on 2008-04-08
somebody please reply............. PLZZZZZZZZZ...

[http://ubuntuforums.org/showthread.php?p=4551467](http://ubuntuforums.org/showthread.php?p=4551467)

---

### Post by 1oki on 2008-04-08
If we dont reply than we either have not had that problem, or dont know what you would do.

I can speak for myself and say that I mess with the config files and mess with settings to get things to work correctly. I have not had this problem, so I am assuming it is not normal. Most likely something was botched durring installation or initial config. Maybe upgrading to 7.10 messed things up... idk, but I suggest trying to figure it out for yourself, if no one responds to you with an answer.


Uninstall, and remove all config files, and start from scratch. Or set up a VMWare client and test on that! then use what you learned in the VMWare client and apply it to your system. Thats what I do...

---

