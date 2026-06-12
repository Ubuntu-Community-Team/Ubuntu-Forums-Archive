---
title: "Verizon EVDO 720 Minor Issue"
date: 2007-10-02
forum: General Help
---

### Post by darkwave80 on 2007-10-02
Hello,
I have Verizon EVDO 720 USB stick and im using Fiesty 7 Ubuntu.

I have it on 3 computers and it auto-detects and I can dial out just fine.

But after I installed apache on one of the machines and set up as a file server.
It seems to me right after that , when I dial up and connect to Verizon I cant browse.
I do a "ifconfig" and it looks like it is pulling all the right information.

ppp0
Link encap:Point-to_Point protocol
inet addr:XX.XXX.XX.XXX  P-t-P: Different IP Addres Mask 255.255.255.XXX
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1500 METRIC:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 frame:0
coollisions:0  txqueuelen:3
RX bytes:64 (64.0b)   TX bytes:97   (97.0)

I dont ever remember seeings the words in LARGE text above.

But I never really would have had a reason to pay to close attention to the ifconfig.

I have gnome PPP and I even tried to put in the DNS by hand and it still does not ping anything.

would apache have altered files related to that? or did gnome go bad? Ive been using ubuntu for about a month now and ive been trying to learn all I can but it seems to me if it has the same config for the dialer it has always had, it should work the same?

Hopefully its not as big of a issues as Im thinking it is but thanks for any help in advance

---

### Post by dcstar on 2007-10-03
> **darkwave80 said:**
> Hello,
I have Verizon EVDO 720 USB stick and im using Fiesty 7 Ubuntu.

I have it on 3 computers and it auto-detects and I can dial out just fine.

But after I installed apache on one of the machines and set up as a file server.
It seems to me right after that , when I dial up and connect to Verizon I cant browse.
I do a "ifconfig" and it looks like it is pulling all the right information.

ppp0
Link encap:Point-to_Point protocol
inet addr:XX.XXX.XX.XXX  P-t-P: Different IP Addres Mask 255.255.255.XXX
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1500 METRIC:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 frame:0
coollisions:0  txqueuelen:3
RX bytes:64 (64.0b)   TX bytes:97   (97.0)

I dont ever remember seeings the words in LARGE text above.

But I never really would have had a reason to pay to close attention to the ifconfig.

I have gnome PPP and I even tried to put in the DNS by hand and it still does not ping anything.

would apache have altered files related to that? or did gnome go bad? Ive been using ubuntu for about a month now and ive been trying to learn all I can but it seems to me if it has the same config for the dialer it has always had, it should work the same?

Hopefully its not as big of a issues as Im thinking it is but thanks for any help in advance

Check the routing once the link is up with:

```
netstat -rn
```

Possibly something is no longer setting the new default route when your PPP link is established.

---

### Post by darkwave80 on 2007-10-03
Ok when I run netstat -rn

it shows
              
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
XX.174.38.5     0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
192.168.0.0      0.0.0.0          0.0.0.0                 U         0 0          0 eth0
169.254.0.0      0.0.0.0         255.255.0.0          U         0  0         0 eth0     
0.0.0.0            192.168.0.1     0.0.0.0              UG        0  0         0 eth 0


I XX'ed out the real ip address for the PPP..

But i did a netstat -rn on my working ubuntu box and it shows the top line the same.
I dont know which of the other lines for eth0 is the apache box but it works when try
to access files from the XP machine so apache is working fine I just dont know what this means

and if any of these entrys for eth 0 would be breaking the "Default route" to the internet.

hope this information was what you needed to know. what do you think is wrong this this setup and by looking at this what is the "misconfiguration" that would be needed to adjust to make things work again?

thanks for help so far.

---

### Post by dcstar on 2007-10-03
> **darkwave80 said:**
> Ok when I run netstat -rn

it shows
              
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
XX.174.38.5     0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
**192.168.0.0 **     0.0.0.0          0.0.0.0                 U         0 0          0 **eth0**
169.254.0.0      0.0.0.0         255.255.0.0          U         0  0         0 eth0     
0.0.0.0            **192.168.0.1**     0.0.0.0              **UG **       0  0         0 eth 0


I XX'ed out the real ip address for the PPP..
.........

The "UG" (Gateway) entry must point to a working IP endpoint that then takes all of your traffic, in this case it still seems to be pointing to your Ethernet IP address and not your PPP one.

I'm not 100% sure, but in /etc/network/if-up.d there are scripts that are supposed to be run whenever a particular network device is enabled ("Up"), so I would speculate that on the system that doesn't work with the PPP device that these are different to the ones on the systems that do work.

You may want to compare all the /etc/network files in both systems.

You should also probably do a search of the Network sub-forum to see if there are any solutions to this sort of issue.

---

### Post by darkwave80 on 2007-10-03
thanks for fast reply...i guess one good thing about having 2 boxes side by side is having the ability to compare....ill check it out now and hopefully fix it....and post back how I did it ......

---

### Post by darkwave80 on 2007-10-03
Hmm well I bought a 900 page book on ubuntu called ubuntu unleashed and read the chaper on PPP and that didnt help.

But what i did do to get the dialer getting dns was this....

I went into network maganer and disabled the local area network so my apache server dont work now.

but when I dial out I can surf the net.

So what would be the way to have your local area network turned on to share files or see another network while your PPP dialer or high speed internet would have default access to the net...? now that its clear that my lan was the issue whats the first place to reconfig?


thanks

---

### Post by Mordikar on 2008-05-17
I happen to work for VZW in the network support dept. There are drivers and a "vzaccess manager" for linux. Almost no one in tech support knows it exists as it's a fairly new project.

The software supports
SUSE 10.3
Fedora Core 8
Redhat Enterprise 5
and Ubuntu 7.10

not all the latest and greatest but it's better than nothing and a LOT easier than running specialty scripts and having to have windows installed.

unfortunately i can't mention who i am as i'm not allowed to make official statements in public forums as i'm not "a public relations person"

---

### Post by Mach1US on 2008-05-19
> **Mordikar said:**
> I happen to work for VZW in the network support dept. There are drivers and a "vzaccess manager" for linux. Almost no one in tech support knows it exists as it's a fairly new project.

The software supports
SUSE 10.3
Fedora Core 8
Redhat Enterprise 5
and Ubuntu 7.10

not all the latest and greatest but it's better than nothing and a LOT easier than running specialty scripts and having to have windows installed.

unfortunately i can't mention who i am as i'm not allowed to make official statements in public forums as i'm not "a public relations person"

can you give us a link so we can try it , i have had PC5750 from vzw for some time and never have heard about it ???

[http://ubuntuforums.org/showthread.php?t=343989&highlight=evdo](http://ubuntuforums.org/showthread.php?t=343989&highlight=evdo)

---

