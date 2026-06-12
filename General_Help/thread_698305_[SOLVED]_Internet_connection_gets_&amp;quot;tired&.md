---
title: "[SOLVED] Internet connection gets &amp;quot;tired&amp;quot;?"
date: 2008-02-16
forum: General Help
---

### Post by StOoZ on 2008-02-16
I have a weired issue with the internet connection.
usually I leave my computer on for days, to download stuff.. (in windows)
Now since I moved to linux (ubuntu 7.10) , if I leave it for lets say 15hrs or more then a day, then Im coming back, it doset enters to any site, just says "Looking up google" (google as an example) in the firefox...
and cant connect or download anything, even though the connection is still alive....
any idea what can it be?

---

### Post by SpaceTeddy on 2008-02-16
the problem you descibe sounds like your dns servers are missing... now why ubuntu would "forget" them is beyond me (never does for me, and mine runs for month :)) but maybe it is "just" that... 

next time, when that happens, please check the /etc/resolv.conf, which is your configuration of dns servers.

also, please check if your computer hat to renegotiat dhcp offers and failed (check that in /var/log/syslog - lines will be marked with [dhcpd]) and check the configuration of your network card (run *ifconfig* in a terminal for that)

cannot think of anything else... at the moment :(

---

### Post by StOoZ on 2008-02-17
well , Ive ran a test.
It happened, then I restarted the computer, connected to the internet, and left it as is for 9 hours, and I came back (from work :) ) and it happened.
the connection is still alive,but I cannot access any site.
Im an ADSL user...
:confused:
I cant handle this issue, if it keeps happening I might need to go back to windows, sadly .
:(

---

### Post by StOoZ on 2008-02-17
btw this is my ifconfig at the moment:
could it be something with the MTU?


eth0      Link encap:Ethernet  HWaddr 00:0F:EA:A2:04:DF  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:eaff:fea2:4df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2062450 (1.9 MB)  TX bytes:435980 (425.7 KB)
          Interrupt:19 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:576 (576.0 b)  TX bytes:576 (576.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:84.229.153.225  P-t-P:213.8.255.155  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:2337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2005128 (1.9 MB)  TX bytes:381055 (372.1 KB)

---

### Post by StOoZ on 2008-02-17
it is really important... please.. :(

---

### Post by randy78 on 2008-02-17
> **StOoZ said:**
> it is really important... please.. :(

If you are using ETH0, then an MTU of 1500 is ideal.

I have had this happen as well, but it hasn't been a problem since I switched my DNS servers to OpenDns.

Just visit their site and you'll find instructions on how to change your DNS servers.
[http://www.opendns.com]("http://www.opendns.com")

Let us know if this helps.

---

### Post by Toadmund on 2008-02-17
Well, I have cable internet and usually when I have these problems (like last night) it usually involves a bad connection or a weak connection.
I discovered that one of my connections were loose, I tightened it, but I still had a slow down, I gave the wire a little bend near the connection, I was back up to speed again, I should replace that wire.

In your case I would see if all your jacks are tight into the wall and all the way to your computer.
Loose connections or bad wires are my slow internet cause most of the time. One time I had a problem with bad connections and it was my power bar in which I had my cable lines running through as surge protection, I bypassed the power bar, that was my problem that time.

Check your wires first.

Good luck.

---

### Post by StOoZ on 2008-02-17
Well first of all thanks for the reply.
secondly, I dont think it has anything to do with the physical aspect of the connection, the connection is still ALIVE, the problem is , I cant access to any site or anything , It feels like the connection has "chocked".
it happens always after several hours of connection, incoherently to whether im downloading something or not.

---

### Post by SpaceTeddy on 2008-02-17
ok... slowly... assuming that your hardware works right, i would like you to try the following things... 

firstly, when it chokes, check the /ect/resolv.conf if it still holds any nameservers. (should be lines in there saying nameserver IP)
secondly. try if you can still ping google (ip is  209.85.129.99) by tpying *ping  209.85.129.99* in a terminal. if you get responses, your connection works, but your dns does not !
thirdly, will the internet connection work again if you do a reconnect. i am not sure how dsl connections are handled in standard ubuntu, but i use the commands *poff* and *pon dsl-provider* to disconnect and reconnect to the internet... 

i hope this helps somehow...

---

### Post by StOoZ on 2008-02-18
> **SpaceTeddy said:**
> the problem you descibe sounds like your dns servers are missing... now why ubuntu would "forget" them is beyond me (never does for me, and mine runs for month :)) but maybe it is "just" that... 

next time, when that happens, please check the /etc/resolv.conf, which is your configuration of dns servers.

also, please check if your computer hat to renegotiat dhcp offers and failed (check that in /var/log/syslog - lines will be marked with [dhcpd]) and check the configuration of your network card (run *ifconfig* in a terminal for that)

cannot think of anything else... at the moment :(

well I think you are right, it happened now,so that what I found in the resolv.cong when it happened:
search home
nameserver 10.0.0.138

and now,when everything is ok (after a restart), the file looks like that:
nameserver 192.116.202.222
nameserver 213.8.172.83
search home


any idea how to solve this issue?

---

### Post by SigmundFreud on 2008-02-18
I had a similar problem once, solved it at the time by making resolv.conf read-only.
Whenever I set up a VPN connection resolv.conf would be overwritten, and we don't want that to happen.

---

### Post by StOoZ on 2008-02-18
well i'll give it a try, thanks.
but why does it happen anyway?

and arent the dns ip's are changing from time to time? (I guess)
so if it will be read only, the system couldnt update then, isnt it?

---

### Post by SpaceTeddy on 2008-02-18
how exactly are you connecting to the internet ? the ip the in your resolf.conf is a private use only network which would suggest that you have a dhcp-server running in your network which issues wrong information, or you have a standard configuration which gets reset upon reconnect and "forgets" to write the right dns servers down...

for further debugging, i would like you to run these commands
>  cp /var/log/syslog* /tmp
gunzip /tmp/syslog.*.gz

they will copy your syslog to your temporary folder and unzip them there.if the second command does not work, fix it with *sudo apt-get install gzip*.

Then, i would like you to extract some information from them and paste it here. Use these commands to get the information:
> grep dhclient /tmp/syslog*
grep pppd /tmp/syslog*

the first one will search your system log for dhcp-leases you got from your network, the second will search for any thing related to your dsl connection. in fact, only one of these should give you anything, since they should be exclusive :)
you don't need to worry about deleting anything afterwards, your computer will do that by itself once you reboot the next time.

hopefully, we can fix it with that information !

[EDIT]
makeing the resolv.conf read-only does not work in all cases, since root ignores read/write permissions and just does what it wants to do. That's why it is called root. And even if it worked, fixing your resolf.conf to one set up nameserver is asking for trouble later on, since you will then manually need to reset the resolv.conf if the nameservers of your ISP change or even worse, if you have a laptop, you cannot get any different nameservers at different locations. Setting it to read-only is far too dangerous for my taste... but it is your computer :)

---

### Post by StOoZ on 2008-03-10
sorry for the delay.
here is the report :
> /tmp/syslog:Mar 10 17:10:57 guy-desktop dhclient: DHCPREQUEST on eth0 to 10.0                                            .0.138 port 67
/tmp/syslog:Mar 10 17:10:57 guy-desktop dhclient: DHCPACK from 10.0.0.138
/tmp/syslog:Mar 10 17:10:57 guy-desktop dhclient: bound to 10.0.0.1 -- renewa                                            l in 42744 seconds.
/tmp/syslog.0:Mar 10 07:21:00 guy-desktop dhclient: DHCPDISCOVER on eth0 to 2                                            55.255.255.255 port 67 interval 7
/tmp/syslog.0:Mar 10 07:21:02 guy-desktop dhclient: DHCPOFFER from 10.0.0.138
/tmp/syslog.0:Mar 10 07:21:02 guy-desktop dhclient: DHCPREQUEST on eth0 to 25                                            5.255.255.255 port 67
/tmp/syslog.0:Mar 10 07:21:08 guy-desktop dhclient: DHCPREQUEST on eth0 to 25                                            5.255.255.255 port 67
/tmp/syslog.0:Mar 10 07:21:08 guy-desktop dhclient: DHCPACK from 10.0.0.138
/tmp/syslog.0:Mar 10 07:21:08 guy-desktop dhclient: bound to 10.0.0.1 -- rene                                            wal in 40423 seconds.


I hope this will assist in solving this disturbing problem....

---

### Post by StOoZ on 2008-03-28
After digging it , I found a solution for that problem, just disabled this line:
> iface eth0 inet dhcp
in > /etc/network/interfaces

---

### Post by wolvie09 on 2008-04-01
hi, i am having a similar issue maybe its related. i am running windows xp and ubuntu 7.1 and mozilla is very slow with the internet. but when i run windows xp, the speed is fine and if i run speedtest i get 12mb download and 2mb upload speeds.... not sure whats going on.

i have tried dhcp but it failed to get the ip info. i set to static and im online but its slow from page to page takes about 1 minute to load a page.... again when i boot in windows xp its fine so i know hardware, speed and connections are all good.

could use any help on this. thx
-Mike

---

