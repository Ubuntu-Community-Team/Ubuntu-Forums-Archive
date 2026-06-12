---
title: "Local unsure: Internet but none?"
date: 2006-07-10
forum: General Help
---

### Post by Simest on 2006-07-10
[To the admins/mods: I am not sure where this belongs as I know this is not a hardware related issue.]

Sigh, with the lastest in GTK2 coming out recently and gnucash 2 right behind it I decided to take the dive to the latest Ubuntu 6.06. I download an iso to make things easy, burned it, installed it. All was going smooth till I tried to access anything online.

Fine, I check everything physically. Perfect. Switch out the drive, differnt OS everything is working perfect. Check on a dual boot with linux, windows setup (Mandriva 10, XP), perfect. Come back to the Ubuntu 6.06 install. Dead....well almost. I can see activity occuring. I can see the updates, but I can not reach anything online (time out). Im stuck, and Ive not seen anything close to this I think. A few things to note that I am aware that the current advice is to turn off IPv6, all fine and dandy till you know the fact that IPv6 works fine under 5.10 (Im typing it from 5.10), also note nothing changes other then version between 5.10 the other drive and 6.06. Second note I cannot access 6.06 and here at the same time (though hardware information and isp information can be had). 

Help?

---

### Post by Maggot on 2006-07-10
I had that problem a couple times and you think I can remember what it was? :( 

I "think" it had to do with my DNS server entries (/etc/resolv.conf) but I could be wrong.

---

### Post by electroconvulsive on 2006-07-11
OK dude two things you can try.

1. In network configuration panel [COLOR="Red"]SYSTEM>ADMINISTRATION>NETWORKING[/COLOR] go to the  [COLOR="Red"]DNS tab[/COLOR] and add the IP adresses of the DNS server or servers that your ISP uses. This can be found out by seraching from the ISP homepage or if worse comes to worse as it did for me ring your ISP and ask them for the DNS server addresses.

2. For some reason under Dapper (dont even start me on breezy) the modem applet that can be added to a taskbar seems to do a better job of connecting than network configuration panel. Try connecting via that because if I try to connect via the network configuration panel it seems to connect but not authenticate my account on the ISP server.

Good luck. I hope this helps

---

### Post by Simest on 2006-07-11
Thanks guys, I will see if maybe I have a DNS issue then.

---

### Post by Simest on 2006-07-11
Good news! I got the live side of the distro to connect and work without much work. I used the install shortcut to install everything to harddrive. Cross your fingers hope this works.....

---

### Post by Simest on 2006-07-11
Connectivity failure. I am speaking from the Live side now. The DNS information has not changed. I did grab a copy of the ifconfig output:

[CopyPaste]
ifsimest@Beast:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:AD:01:24:83
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2778 errors:72 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:169534 (165.5 KiB)  TX bytes:1790 (1.7 KiB)
          Interrupt:185 Base address:0xe100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:722 (722.0 b)  TX bytes:722 (722.0 b)
[/Copypaste]

Anyone else?

---

### Post by Maggot on 2006-07-11
Ok, what kind of connection you got going? Going through router? Direct connect? How does your computer connect to the Internet I guess is what I'm after.

what does typing this in a terminal give you:

route

edit: Also for verification what is the output of this:

cat /etc/resolv.conf

---

### Post by Simest on 2006-07-11
Limited success with 30 seconds of connection everytime I reset my cable modem. Earthlink direct connection cable, no router.

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
24.110.250.0    *               255.255.255.0   U     0      0        0 eth0
default         user-0c6tug1.ca 0.0.0.0         UG    0      0        0 eth0

search earthlink.net
nameserver 207.69.188.185
nameserver 207.69.188.186
nameserver 207.69.188.187

---

### Post by Simest on 2006-07-11
Limited success with 30 seconds of connection everytime I reset my cable modem. Earthlink direct connection cable, no router.

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
24.110.250.0    *               255.255.255.0   U     0      0        0 eth0
default         user-0c6tug1.ca 0.0.0.0         UG    0      0        0 eth0

search earthlink.net
nameserver 207.69.188.185
nameserver 207.69.188.186
nameserver 207.69.188.187

---

### Post by Maggot on 2006-07-11
> **Simest said:**
> 
default         user-0c6tug1.ca 0.0.0.0         UG    0      0        0 eth0


Hmmmmm.  Your default gateway is user-0c6tug1.ca....not sure what that is. I normally see an IP address.

:-k

edit: can you ping any of your DNS (name) servers?

---

### Post by Simest on 2006-07-11
Same data from the live that works....

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
24.110.250.0    *               255.255.255.0   U     0      0        0 eth0
default         user-0c6tug1.ca 0.0.0.0         UG    0      0        0 eth0

search earthlink.net
nameserver 207.69.188.185
nameserver 207.69.188.186
nameserver 207.69.188.187

---

### Post by Simest on 2006-07-11
My delicate need of sleep is paging but something else is noting that mayhaps this has to do with the changes in the software requesting items on the internet.

---

### Post by Maggot on 2006-07-11
I have no experience with cable modems but one thing that bothers me is it appears you are having DNS issue and your gateway isn't an IP but a 'hostname'.....

---

### Post by Simest on 2006-07-12
> **Maggot said:**
> I have no experience with cable modems but one thing that bothers me is it appears you are having DNS issue and your gateway isn't an IP but a 'hostname'.....

Then why would it be the same for both yet one work (the live) and not the other when it seems the same?

---

### Post by Maggot on 2006-07-12
> **Simest said:**
> Then why would it be the same for both yet one work (the live) and not the other when it seems the same?

Good question. If we knew, we'd know the solution ;)

Somewhere there is a config file thats different in the live CD compared to the install one.

---

### Post by Simest on 2006-07-12
> **Maggot said:**
> Good question. If we knew, we'd know the solution ;)

Somewhere there is a config file thats different in the live CD compared to the install one.

The only real visual difference I see is the updating program......is there any way to compare the two sets of files from the live and the hdd?

---

### Post by Simest on 2006-07-12
Im starting to wonder would the alternate install cd might work? I do want to know my question from my previous post first though.

---

### Post by Simest on 2006-07-12
I am pleased to report success. 6.06!

---

### Post by Maggot on 2006-07-12
> **Simest said:**
> I am pleased to report success. 6.06!

and the solution :confused:

edit: Oh, and \\:D/

---

### Post by Simest on 2006-07-12
No idea what the solution is. I just did an upgrade from a fresh 5.10 install and crossed my fingers. 

Route:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
24.110.204.0    *               255.255.254.0   U     0      0        0 eth0
default         user-0c6tj01.ca 0.0.0.0         UG    0      0        0 eth0

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:80:AD:01:24:83
          inet addr:24.110.205.238  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::280:adff:fe01:2483/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:128947 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:24705 txqueuelen:1000
          RX bytes:94136325 (89.7 MiB)  TX bytes:3707976 (3.5 MiB)
          Interrupt:201 Base address:0xe100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33295 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2713157 (2.5 MiB)  TX bytes:2713157 (2.5 MiB)

cat:
search earthlink.net
nameserver 207.69.188.185
nameserver 207.69.188.186
nameserver 207.69.188.187

---

### Post by Maggot on 2006-07-12
Just like me...not sure what I did...but after several attempts and reboots it just worked [IMG]http://www.mustangmods.com/ims/u/154/1304/61713.gif[/IMG]

---

### Post by Simest on 2006-07-14
Nice. Oh and thanks for the help. :)

---

