---
title: "DNS gets removed on restart ( tried everything!!!!)"
date: 2006-09-29
forum: General Help
---

### Post by grizzly on 2006-09-29
Going mad over dns here, it keeps resetting at every restart! 

I have tried pratically everything :( , but it still won't work..
Stuff I have tried to correct this:
1. removed resolvconf , but Internet doesn't works without it.
2. chattr +i : this gives a inode error
3. chmod -w -w -w resolv.conf - this fails!
4. removed that resolvconf/run/enable-updates file on some suggestion)
5. done stuff in my dhclient.conf file and I hve a feeling something must be wrong here.: here it is:-
> #send host-name "andare.fugue.com";
     15 #send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
     16 #send dhcp-lease-time 3600;
     17 #supersede domain-name "fugue.com home.vix.com";
     18 prepend domain-name-servers 127.0.0.1;
     19 prepend domain-name-servers 202.56.230.5;
     20 request subnet-mask, broadcast-address, time-offset, routers,
     21         domain-name, host-name;
     22         netbios-name-servers; netbios-scope;
     23 require subnet-mask, domain-name-servers;
     24 #timeout 60;
     25 #retry 60;
     26 #reboot 10;
     27 #select-timeout 5;
     28 #initial-interval 2;
     29 #script "/etc/dhcp3/dhclient-script";
     30 #media "-link0 -link1 -link2", "link0 link1";
     31 #reject 192.33.137.209;


Specs: Lan based 64kbps connection , static ip/dns , no router , no firewall.

Other problems ( may help to find cause) 
1. downloads from IRC don't work ( undernet ;) )
2. normal http downloads keeps getting stuck. i.e they require repeated  pause/resume to get complete.

Other than this, my browsing speed is normal, irc chats are also normal..

Help please

---

### Post by wieman01 on 2006-09-29
Have you tried using static IP and setting your DNS manually? You'll have to change this file:
> /etc/network/interfaces

---

### Post by Buffalo Soldier on 2006-09-29
```
prepend domain-name-servers 127.0.0.1;
prepend domain-name-servers 202.56.230.5;
```

Just curious, why are there two lines of **prepend domain-name-servers**? Furthermore the first line ( prepend domain-name-servers 127.0.0.1; ) refers to your loopback/localhost or something. Try deleting that line and use the second line ( prepend domain-name-servers 202.56.230.5; )only.

```
#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
prepend domain-name-servers 202.56.230.5;
request subnet-mask, broadcast-address, time-offset, routers,
domain-name, host-name;
netbios-name-servers; netbios-scope;
require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;
```

---

### Post by dcstar on 2006-09-29
> **grizzly said:**
> Going mad over dns here, it keeps resetting at every restart! 
......

If you are using DHCP, then there is **ANOTHER** DHCP server on your network, so there isn't much point altering your Ubuntu box as it cannot be a DHCP server to itself.

Find the other DHCP server and fix the problem there, or use Static IP settings as suggested and remove the Ubuntu DHCP client ASAP.

---

### Post by grizzly on 2006-09-29
> [/QUOJust curious, why are there two lines of prepend domain-name-servers?TE] Oh I was just playing/testing everything.. I have already tried the situation you suggest

[QUOTEHave you tried using static IP and setting your DNS manually?]
like this ?
> 
auto eth0
      7 iface eth0 inet static
      8 address 172.16.100.xxx
      9 netmask 255.255.0.0
     10 gateway 172.16.xxx.x
     11 nameserver 202.56.230.x

---

### Post by grizzly on 2006-09-29
> If you are using DHCP, then there is ANOTHER DHCP server on your network, Sorry I have absolutely no idea about this other DHCP. 
My Internet is like this: one guys takes a nice big lease line and then kind of 'distributes' this to single home PC's

---

### Post by hanzomon4 on 2006-09-29
I've had the same problem, here's how I fixed it...
> **hanzomon4 said:**
> I fixed it.. here's how

First the only setting I had to reset after a reboot was the DNS. The config file where the DNS settings are stored is in /etc/resolv.conf. 
For some reasons getting my settings to stick using the Network configuration tool would not work, so I tried editing /etc/resolv.conf by hand.
That did not work because Ubuntu uses a dynamic DNS configuration. This will overwrite the etc/resolv.conf file at boot-up.
The solution is to add your settings to /etc/resolvconf/resolv.conf.d/base like this.
```
 sudo gedit /etc/resolvconf/resolv.conf.d/base
```
```
nameserver   192.X.X.X
```
Replace the "192.X.X.X" with your DNS number.

Okay my work here is done.

---

### Post by grizzly on 2006-09-29
Thanks hanzo That worked!!  :KS  
only thing is the boot-process got stuck at "configuring network interfaces", I had to hit ctrl+c to continue.. but its still worked seamlessly..
I guess that was sue to my now completely screwed dhclient settings.. 

thanks again

---

