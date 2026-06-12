---
title: "Cannot Conect to Router with Firefox."
date: 2007-02-09
forum: General Help
---

### Post by Becan186 on 2007-02-09
Hello Everone,
Yes I am another newbee to Linux and Ubuntu 6.06, also Forums for that matter.

I cannot connect to the internet or my router using firefox by typing "http://192.168.1.254" for router or say "http://www.google.com", now I am searching for some help and guidance to get a connection.

I have a devoted HDD with an install of Ubuntu 6.06. This is in a removable HDD tray, I also have a 2nd HDD also in a tray with XP on it, when XP HDD is in the PC it will freely connect to my Router and internet, Therefore shall we presume no hardware problems.

System:
Gigabyte GA-K8N Pro-Sli, with nForce4 Chipset.
Amd 64x2 Dual core processor
Billion ADSL Router BIPAC-7402

Can anybody help me with the next step of action to setup a connection. Also ho can i ping in Ubuntu?

Thanks in advance
Ben

---

### Post by Zimmer on 2007-02-09
Was your router on before you started to boot the OS? 
First step (not technical at all) switch the router on , then boot /restart Ubuntu, and see if your hardware will sort itself that way. I say this from experience.

Ping...  from a terminal, or use  System>Administration>Network Tools

---

### Post by Becan186 on 2007-02-09
Hello Zimmer,
Yes, Router is allways swithched on.
Ben

---

### Post by Becan186 on 2007-02-09
ifconfig says:

eth0   

         Link encap:Ethernet HWaddr 00:14:85:EF1:84
         inet6 addr: fe80::214:85ff:feef:d184/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 b) TX bytes:3888 (3.7 KiB)
         Interrupt:217 Base address:0xe000

lo

        Link encap:Local Loopback
        inet addr:127.0.0.1 Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING MTU:16436 Metric:1
        RX packets:21 errors:0 dropped:0 overruns:0 frame:0
        TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:1456 (1.4 KiB) TX bytes:1456 (1.4 KiB)


Also ping 192.168.1.254
Says
Network is unreachable

---

### Post by bollix47 on 2007-02-09
If you're using a wired ethernet connection try going to

System - Administration - Networking

Make sure there's a wired connection there - hi-lite it and put a checkmark beside it.

Then go to properties and click on "Enable this connection".

---

### Post by Becan186 on 2007-02-09
Checked all of the above and ethernet connection was enabled and seemed correct. The only quiery I have there is how can I tell if it is a wired ethernet connection as opposed to a say wireless (which i do not have on this system).

---

### Post by Bartender on 2007-02-09
If you see a device in Networking, then it's your card.  The Wireless device picture looks different, and as you say you don't have any wireless device anyway.

I don't think this is your problem but let's try it.  Try disabling IPV6 in Firefox.  This is easy
[http://www.linuxforums.org/forum/linux-newbie/63087-firefox-connection-time-out.html](http://www.linuxforums.org/forum/linux-newbie/63087-firefox-connection-time-out.html)

Can you go online now with Firefox but the rest of the system can't, as in for updates?  If so, then you want to disable IPV6 systemwide
[http://neoaddict.wordpress.com/2007/01/27/disable-ipv6-in-ubuntu/](http://neoaddict.wordpress.com/2007/01/27/disable-ipv6-in-ubuntu/)

If disabling IPV6 in Firefox didn't get you online in Firefox, hold on to these directions because you may have to come back to this once you figure out what's holding you up.

---

### Post by Becan186 on 2007-02-09
Disabling IPv6 did not work.

The error message Firefox gives "Sever not found".

I have Firefox running on my xp drive so I'm thinking its not a problem with the Routers fire wall.

Any more ideas?

---

### Post by Becan186 on 2007-02-10
Cracked it!!!!

its simple once you get it right, Hindsight is looking with both eyes open.

I needed to set a static IP address and Primary DNS and remote gatway, not a dhcp connection. Also a DNS server IP Address.

Thankyou all, hope it gets easier in time.
Cheers

---

