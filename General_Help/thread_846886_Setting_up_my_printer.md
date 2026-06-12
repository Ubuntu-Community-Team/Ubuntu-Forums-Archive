---
title: "Setting up my printer"
date: 2008-07-01
forum: General Help
---

### Post by rossjman1 on 2008-07-01
Hi I have a HP PhotoSmart C1300 printer. My roommate has it connected to his AirPort (an Apple wireless router) via usb. How would I go about setting it up? I couldn't figure out how to do it in Windows, and my roommates MacBook autodetected it. I googled it (when I was trying to set it up in both Windows and Ubuntu) and I need to know the ip address of the printer, but I don't know how to get that information. If I knew the ip address this would be simple, so basically what I'm asking is how would I get the ip address of my printer?

---

### Post by dcstar on 2008-07-02
> **rossjman1 said:**
> Hi I have a HP PhotoSmart C1300 printer. My roommate has it connected to his AirPort (an Apple wireless router) via usb. How would I go about setting it up? I couldn't figure out how to do it in Windows, and my roommates MacBook autodetected it. I googled it (when I was trying to set it up in both Windows and Ubuntu) and I need to know the ip address of the printer, but I don't know how to get that information. If I knew the ip address this would be simple, so basically what I'm asking is how would I get the ip address of my printer?

If it is connected via USB then the printer doesn't have an IP adress, but the AirPort probably does (as it must act like a print server).

See if you can find out if the AirPort supports IP printing or just Apple only printing.

---

### Post by txcrackers on 2008-07-02
I'm guessing that the printer is making itself available via Zeroconf/Rendezvous/mDNS. Fortunately, being a Linux user, you have lots of options to find the printer... Poke around here:

[http://avahi.org/wiki/AdministrativeAvahiApplication](http://avahi.org/wiki/AdministrativeAvahiApplication)

---

### Post by rossjman1 on 2008-07-02
Thanks for the replies. I took your advice and found this site ([http://stanford-clark.com/printer.html](http://stanford-clark.com/printer.html)) which tells me the address of the airport. But, it still wont print. Here are some screenshots. Tell me if I entered something wrong.

First is a screenshot of the Avahi Discovery app focusing on the _riousbprint._tcp printer that the above website tells me to use.
[IMG]http://img376.imageshack.us/img376/6779/screenshotavahidiscoverxp2.png[/IMG]
Next is a screenshot of the printer configuration utility. I tried setting it up to use the printer.
[IMG]http://img67.imageshack.us/img67/9149/screenshotprinterconfiglp2.png[/IMG]
And finally, another screenshot showing all of the printers detected by Avahi Discovery... eventhough I only have 1! Don't know which to use.
[IMG]http://img354.imageshack.us/img354/8116/screenshotavahidiscoverzd2.png[/IMG]

---

### Post by plucky on 2008-07-02
This just a quick suggestion.Go to

System > Administration > Printing > Server Settings and make sure "Show printers connected to other systems" is ticked.Then try adding another new printer and see if it finds it.

If that doesn't work,open Firefox and in the address bar ```
http://10.0.1.1:10000/
``` to see if you can connect to the print server.


Good Luck

---

### Post by rossjman1 on 2008-07-02
It has been ticked the whole time, and typing that in the address bar in FF doesn't work.

---

### Post by rossjman1 on 2008-07-02
Bump.

---

### Post by rossjman1 on 2008-07-05
bump

---

### Post by rossjman1 on 2008-07-07
please help...

---

### Post by rossjman1 on 2008-07-07
Bump, I really need to get this working for school!

---

### Post by rossjman1 on 2008-07-08
Come on....

---

### Post by rossjman1 on 2008-07-08
bump

---

### Post by bluepowder7 on 2008-07-08
that's a weird IP address.  10.0.1.1  i thought that private networks should be 192.168.x.x or similar?  what's your laptop's IP address?  don't you need to be on the same subnet for this stuff to work?

anyhoo, if it's your printer, and you have a usb port on your pc, and you NEED to use it - yank it out of the router and connect it directly.

---

### Post by rossjman1 on 2008-07-08
Here is the output for ifconfig:
```
jeff@jeff-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:15:e9:72:db:ef  
          inet addr:10.0.1.3  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::215:e9ff:fe72:dbef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8973 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7629 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9937251 (9.4 MB)  TX bytes:1143270 (1.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1712 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85600 (83.5 KB)  TX bytes:85600 (83.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-15-E9-72-DB-EF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69891 errors:0 dropped:0 overruns:0 frame:22463
          TX packets:8894 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:19477071 (18.5 MB)  TX bytes:1544054 (1.4 MB)
          Interrupt:16 

```

---

### Post by rossjman1 on 2008-07-09
Bump. Is it just me or does Apple make their products difficult to use whith other non-apple products? I had a difficult time with this in Windows, too, and my roommates Mac auto detected it.

---

### Post by rossjman1 on 2008-07-11
So impossible then?

---

### Post by rossjman1 on 2008-07-13
What the f, I guess I'm moving my printer back to my room.

---

### Post by bluepowder7 on 2008-07-13
> **rossjman1 said:**
> What the f, I guess I'm moving my printer back to my room.

hey, now you're thinkin' out of the box!  :lolflag:

maybe as a down-the-line plan, get a non-apple router to hook stuff up to?

---

### Post by rossjman1 on 2008-07-13
It's my roommates, he always buys apple stuff. Kinda makes me mad.

---

### Post by bluepowder7 on 2008-07-13
have you thought about setting him on fire?

---

### Post by rossjman1 on 2008-07-13
I aughta pwn his n00b a$$!!!!!11!!!!111oneoneone!

---

### Post by Thievrey Corporation on 2008-09-01
Don't know if this will help, but I would not change the port number:
host name: 10.0.1.1 #AEX IP adress#
Port number: 9100 #default value - no change#
This worked OK for me.

---

### Post by driven1 on 2008-12-05
I just did this last night and it took all of about 5 minutes. Hope this helps someone. info came from [here]("http://stanford-clark.com/printer.html")

> install avahi-discover from Synaptic package manager

run Applications->system tools->Avahi Zeroconf browser

find the _riousbprint._tcp printer

click on it and note the IP address of the Aiport Express

System->Administration->printing.

New Printer->AppSocket/HPJetDirect

type the IP address of the Airport Express as the Host address

Select printer type and model and give it a name.

Job Done!


---

