---
title: "wireless buggy on eeepc"
date: 2008-05-03
forum: General Help
---

### Post by jorik42 on 2008-05-03
so im having this interesting issue when im connected to the internet.  When my computer goes to screensaver, or sometimes just sits for long enough, my wireless card will "cut out."  to fix it i ususally have to restart the computer, though i suspect that all i need to do is reboot the network-connection program.  i can also resolve the problem temporarily by switching wireless networks.  i dont know if this means anything, but im using ndiswrapper for the network drivers...

so, here are my questions:

1.) is there a way to restart just the network app, and not the whole system when this happens?
2.) why does this happen and how can i keep it from occuring?

thanks alot for any help; 

jorik

---

### Post by terry f on 2008-05-03
I am new to ubuntu but you to restart the conection you may want to try something like this:

it terminal:
ifconfig         <-- this should give you the names you in network card
                      it should be something like wlan0 or some thing.

sudo ifconfig <name of interface> down   <-- terns of the interface
sudo ifconfig <name of interface> up     <-- terns it back on



I don't know if that will help

---

### Post by jorik42 on 2008-05-03
hmm; well, the 

"sudo ifconfig wlan0 down" seems to work, but the corresponding command "...up" doesnt seem to do anything.  i still have to either switch networks and/or manually command it to re-connect.  

as for how i like the eeepc, i love it.  amazing size-wise (fits it cargo pants pockets ^_^  i take it everywhere).  excellent speed after upgrading to 2gigs ram.  i put ubuntu on it; which is thousands of times better than the default xandros OS.  really the only issue im having is this little network thing.  and even thats not that big a deal.

---

### Post by terry f on 2008-05-03
does this help: sudo ifdown eth0 && sudo ifup eth0

---

### Post by ghost_ryder35 on 2008-05-03
check bios to see if it goes into power saving mode when it is been idle for long

---

### Post by Helios1276 on 2008-08-05
An old thread I'm bumping to try and help a friend get his Eeepc online. will post if/iwconfig as soon as I get home and get it online directly (20min)through a modem. So, far as I can tell it doesn't seem to like WAP, preferring WEP(getting Gutsy flashbacks lol). Nosed around the Relevant forums ( Xandros/ EEpc) but found the lack of answers or support frustrating. I'm trying to get him to consider Kiwi Linux or Linux Mint as an alternative. Any Eeepc users out there?

@Mods Was unsure of whether to post in Other OS or to bump here, move at your leisure if necessary.

---

### Post by Helios1276 on 2008-08-05
/home/user> sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

Warning: Driver for device ath0 has been compiled with version 22
of Wireless Extension, while this program supports up to version 20.
Some things may be broken...

ath0      IEEE 802.11g  ESSID:"The Information Super-highway"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

/home/user>  sudo ifconfig
ath0      Link encap:Ethernet  HWaddr 00:15:AF:82:03:F6
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:1F:C6:09:8B:DE
          inet addr:192.168.2.9  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2409 errors:0 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000
          RX bytes:4948507 (4.7 MiB)  TX bytes:0 (0.0 b)
          Memory:fbfc0000-fc000000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:717 errors:0 dropped:0 overruns:0 frame:0
          TX packets:717 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:75230 (73.4 KiB)  TX bytes:75230 (73.4 KiB)

wifi0     Link encap:Ethernet  HWaddr 00:15:AF:82:03:F6
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:81341 errors:0 dropped:0 overruns:0 frame:23484
          TX packets:29308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:20993206 (20.0 MiB)  TX bytes:1773134 (1.6 MiB)
          Interrupt:10 Memory:e0420000-e0430000

---

