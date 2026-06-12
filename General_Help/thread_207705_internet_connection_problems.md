---
title: "internet connection problems"
date: 2006-07-02
forum: General Help
---

### Post by firebird45331 on 2006-07-02
I'm relatively new to linux.  I have a broadband cable connection.  I've posted it in the newbie section and been doing a butt load of searches.  I'm finding several others with the same problem I am, but no solution seems to take care of it.  When I was using Breezy I didn't have a problem it set up and would connect without any problems.  When I ran the live cd I didn't have any problems, but then when I install Dapper and try to view a page or do anything concerning the internet it just sits there and eventually an error comes up.  I checked the administration setting for my network and it said my ethernet was enabled.  I just did a dual boot installation so I can switch back and forth between good ole reliable XP and Dapper.  I really like Dapper and would enjoy using it, but unfortunately I'm getting irritated.

---

### Post by mips on 2006-07-02
Ok so we know your internet does not work but besides that you haven't really told us anything ?

What diagnostic procedures have you tried, what links have you followed etc etc etc.

The information is you supply is probably directly proportional to the response you will receive ;)

---

### Post by firebird45331 on 2006-07-02
actually I don't know.  I didn't keep track of all the links I went to.  I booted off the live cd looked at all the properties then went back to my hard installation and they seemed the same.  Like I said I'm new to Linux so I'm kinda in the dark.  At one point I even installed Breezy and then upgraded and the results were all the same.  It's almost like there's a firewall blocking my access.

---

### Post by mips on 2006-07-02
What hardware are you using, modem/router model etc ???
How is the above hardware configured ??? Physical diagram, with connection types (USB/Ethernet etc) and IP addresses etc always help.

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

---

### Post by RRS on 2006-07-02
[QUOTE=mips]
1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
[/QUOTE]
Since the connection works with the live cd include the results of the above from both the live cd and your installed system for comparison.

---

### Post by firebird45331 on 2006-07-02
ok...that's a lot of handwritten notes is there a way to clip and paste between linux and XP.  At the end I did get sick of hand writing all that down and saved it to a text file atleast.

---

### Post by mips on 2006-07-02
Save it on memory stick or floppy. Alternatively save it to the hard drive and if you are using ext2/3 partitions open it from windows using the EXT2IFS driver.

---

### Post by firebird45331 on 2006-07-02
ok for ifconfig eth0 I got:

eth0 Link encap:ethernet hwaddr 00.:08:A1:24:2b:68

inet addr:bcast:mask:

inet6 addr:fe80::208:a1ff:fe24:2b68/64 scope: link

up broadcast multicast mtu:1500 metric:1

Rx packets: 462 errors:6 dropped:0 overruns:0 frame:0

Tx packets:23 errors:2 dropped:0 overrruns:1 carrier:1 collisions:0 Txqueuelen:1000

Rx bytes: 38533(37.6KiB)
Tx bytes: 2840(2.7Kib)

interrupt 201 base address:0xe800

riyte -n Kernel IP routing table

destination       Gateway      Genmask        flags met  ref  use   Iface
cat /etc/resolv.conf

search woh.rr.com
name server 
cat /etc/network/interfaces

auto lo
iface lo inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
auto wLan0
iface wlan0 inet dhcp

when I typed lspci |grep eth I didn't get a response

my windows IP config /all

Host name shadow_0yjz0d7j
primary dns suffix
node type  unknown
ip routing enabled no
wins proxy enabled no
dns suffix search list woh.rr.com

ethernet adapter local area cannection
connection specific DNS woh.rr.com

description cnet pro200wl PCI fast ethernet adapter

physical address 00-08-A1-24-2B-68
DHCP enabled  yes
autoconfig enabled  yes
ip address  subnet mask default gateway 24.164.88.1
dhcp server dns servers   
monte@monte-desktop:~$ cat /etc/dhcp3/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject #alias {
#  interface "eth0";
#  fixed-address #  option subnet-mask 
#lease {
#  interface "eth0";
#  fixed-address #  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask #  option broadcast-address ;
#  option routers #  option domain-name-servers 
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
I hope that helps  looking back it would've been easier to clip and paste to the linux word processor  and save it as a text document and clip and paste from notepad.  Live and learn I guess.  that would've beat handwritting all that crap out.

---

### Post by mips on 2006-07-02
Please edit your above post an mask out the ip addresses starting with 24.164.xxx.xxx for security reasons.

Type the command **lspci**

I suspect you have a   **Davicom Semiconductor, Inc. 21xxx DEC-Tulip compatible 10/100 Ethernet**  or similair type chipset on the cnet LAN card.

If this is the case then start searching these forums for **Tulip** and look at the suggestions. There is also a howto in the howtos section of the forum.

If the card is not onboard also try moving it to a different PCI slot, [http://www.users.bigpond.com/vkelim/SuSE_notes/node21.html](http://www.users.bigpond.com/vkelim/SuSE_notes/node21.html)

[http://ubuntuforums.org/showthread.php?t=54886](http://ubuntuforums.org/showthread.php?t=54886)

---

### Post by firebird45331 on 2006-07-02
that looks familiar I'll check again to make sure.  My computer is a dell 8200 dimension, I believe it's all integrated.

---

### Post by firebird45331 on 2006-07-02
yep that's the chipset I have,why would breezy work with it, but dapper wouldn't?

---

### Post by firebird45331 on 2006-07-02
Ok nifty here's my first post using Dapper.  I'm happy now.  here's what I did

sudo rmmod tulip
         rmmod dmfe
         modprobe dmfe

         /etc/init.d/networking stop
         /etc/init.d/networking start

the start command resulted in a lot of stuff going up my screen faster than I could read it a lot of it was saying device not found.  Then I went to my firefox and everything loaded normally.  Now I'm happy.  I'll reboot and see if the changes stay.  anyone care to explain what those commands did?
Thanks so much for the help

---

### Post by mips on 2006-07-02
[QUOTE=firebird45331]

sudo rmmod tulip
         rmmod dmfe
         modprobe dmfe

         /etc/init.d/networking stop
         /etc/init.d/networking start
[/QUOTE]

first two lines remove the tulip & dmfe modules(drivers in win speak). Third kinda loads the module. Last two lines stops & starts networking.

I doubt those changes would be permanent.You might have to rename the tulip module so it does not load or have a startup script.

---

### Post by Face1 on 2006-08-04
Where would I put those commands to be loaded on startup?  I could make a script to run them, but I don't know how to make sure that script is always run on startup. Would I add it as an S script in rc2.d?

---

### Post by johnbl on 2006-08-04
> **Face1 said:**
> Where would I put those commands to be loaded on startup?  I could make a script to run them, but I don't know how to make sure that script is always run on startup. Would I add it as an S script in rc2.d?

Did you get a reply to this?
Have a similar problem with a system that refuses point blank to talk to its broadband modem..

John

---

### Post by mips on 2006-08-04
It's 3am here, I'll respond later unless someone else helps you. Do a search for init.d

---

