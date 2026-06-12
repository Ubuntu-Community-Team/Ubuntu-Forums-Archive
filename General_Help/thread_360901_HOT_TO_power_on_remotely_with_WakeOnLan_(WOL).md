---
title: "HOT TO: power on remotely with WakeOnLan (WOL)"
date: 2007-02-13
forum: General Help
---

### Post by majoridiot on 2007-02-13
the thread title says "HOW TO:", but like a lot of things linux, it's more of a 
how-i-got-it-to-work-in-my-case...

i set up my mythbackend to automatically shut down on idle and wake up to record by 
itself (the topic of another thread) and that left me with the need to wake it up (power it 
on) from my remote frontend... because i'm too lazy to walk into the other room to 
physically push the button. ;)

my backend motherboard advertises a WakeOnLan function, which can (in theory) turn on 
the box remotely by network command.

for a quick primer on WOL, including links in case you run into problems, i suggest starting
here:

[http://en.wikipedia.org/wiki/Wake-on-LAN](http://en.wikipedia.org/wiki/Wake-on-LAN)

**to begin**, you need to make sure that you have a WOL function on your mobo.  i found 
mine in the "power management" menu of BIOS setup.  it was called "LAN/Ring Power On"... 
although different mobos and BIOSes refer to it as possibly WakeOnLAN, WOL, Resume on NIC,
etc.  once you find it, enable it.  

if your network controller (NIC) is integrated into the mobo, chances are you are good to 
go.  if you have a network card, you should check to see if you need to use an additional 
cable between the mobo and the NIC. see the wikipedia link for more info. 

**next**, i grabbed a couple of packages needed for the following steps. (do not worry if you 
do these apt-gets and you already have the packages but do not know it- it will not harm 
anything.)

```
# sudo apt-get install ethtool         ## on backend box
# sudo apt-get install wakeonlan     ## on frontend box
```

***ethtool*** is a very robust command-line for fiddling with the intricate bits of the NIC, and we 
need to do that.

***wakeonlan*** is a simple command line for generating the "magic number" for WOL and 
transmitting it via UDP.

**next**, i made sure my NIC *actually is* WOL capable-

```
# sudo ethtool eth0

Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 31
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pg **<<<========"g" means it uses "magic packets"**
        Wake-on: g
        Current message level: 0x000000c5 (197)
        Link detected: yes
```

my wake-on support shows pg... other valid returns are pug, pumbg, bg, etc.  the part 
we're most concerned with is that it has a "g" somwhere in there as that means we can 
wake it with "magic packets".

**next** we tell the NIC to enable WOL (actually turn it on in the NIC):

```
# sudo ethtool -s eth0 wol g
```

since this setting will (likely) be reset when the computer powers down, i set it up to enable
with every boot:

```
# sudo gedit /etc/rc.local
```

and then add this on a line by itself anywhere before "exit 0"

```
ethtool -s eth0 wol g
```

my /etc/rc.local was empty other than the "exit 0", so the final edit looked like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ethtool -s eth0 wol g

exit 0
```

**the last thing** i needed was the MAC address of the backend for the "magic number".  to discover it:

```
# ifconfig

eth0      Link encap:Ethernet  **HWaddr 00:16:EC:4C:45:56**
          **inet addr:192.168.1.100**  **Bcast:192.168.1.255**  Mask:255.255.255.0
          inet6 addr: fe80::216:ecff:fe4c:4556/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:469929 (458.9 KiB)  TX bytes:12037247 (11.4 MiB)
          Interrupt:5 Base address:0xd000
```

my mac is 00:16:EC:4C:45:56 -- but note the two other bolds, as you might need them.

that's the last piece of info needed; it's time to shut off the backend and see if we can
wake it.  it is **mandatory** on most, if not all mobos, that you shutdown with a software 
command (either in a terminal, a script or by telling it to "shut down" from the logon/logoff
in your GUI) and **not** by holding the power button 3-5 seconds.  

i'm in an ssh terminal, so i did:

```
# sudo shutdown -h -P now
``` 

once it was powered off, i was delighted to find out that waking it from my frontend 
machine was as simple as issuing this command in a terminal:

```
# wakeonlan -i 192.168.1.100 00:16:EC:4C:45:56
```

where ***-i*** is the ip address and **00:16:EC:4C:45:56** is the MAC adress of my backend 
machine as discovered by the ***ifconfig***.

notice that this command does *not* require sudo, which makes it great for setting up 
on a toolbar launcher (like i did) or for plugging into mythfrontend setup to have it wake 
the backend.

if the ***wakeonlan*** command above doesn't work for you, you can try using the subnet broadcast 
address or the limited broadcast address (255.255.255.255).  note that if you use these options,
the "magic number" will be sent to every machine on the subnet.  you can also try broadcasting 
to a different port- the default is 9, but if you are having trouble waking it, you might try 7.  

using the info from above (your results will vary, of course), variations could include:

```

# wakeonlan -i 192.168.1.255 00:16:EC:4C:45:56          # broadcasts to the subnet broadcast address

# wakeonlan -i 192.168.1.255 -p 7 00:16:EC:4C:45:56    # broadcasts to the subnet broadcast address on port 7

# wakeonlan 00:16:EC:4C:45:56                                     # broadcasts to the limited broadcast address

# wakeonlan 00:16:EC:4C:45:56 -p 7                              # broadcasts to the limited broadcast address on port 7

etc...
```

for complete info on these commands:

```
# man ethtool
# man wakeonlan
```

Good Luck! :D

**EDIT:** just a quick note to add that continued testing shows that after a period of time in a powered-down state, 
the backend  doesn't seem to respond to the magic packet if sent to the ip address... but wakes immediately on 
broadcast to the subnet broadcast (in my case 192.168.1.255).

---

### Post by Redeyes_Gambit on 2007-03-23
Just a couple of suggestions/questions/observations :D

1. Shouldn't your shutdown line read: 

```

sudo shutdown -h -P now

```

so the machine actually powers itself off? The uppercase "P" makes the machine power-down where as the -h just makes the machine halt.

2. Before editing /etc/rc.local I would suggest:

```

sudo cp /etc/rc.local /etc/rc.local.bkp

```

first. That way if a noobly user (such as we have all been at one time or another :) ) accidentally bounces the edit they can just:

```

sudo cp /etc/rc.local.bkp /etc/rc.local

```

to restore the original file. 

Also, when using gedit one of THE FIRST things you want to do for editing code is turn off text-wrapping. I can't tell you how many times I messed up my /etc/apt/source.lst file because gedit text-wrapped the commands (DOH!) You can turn off text-wrapping by going to edit>preferences in gedit, then under the "view" tab there is a check-box for disabling text-wrapping.

4. In regard to why sending the magic packet to the specific IP address failed, could that be due to DHCP per chance? DHCP, for those who don't know, dynamically assigns IP addresses to all the machines on a network. It is usually set up in either your DSL modem, router, wireless access point, or server (if you're in a big company or a power-user :) .) 

DHCP has the advantage of auto-magically setting up and rotating IP addresses for all the machines so they talk and play nicely, but it can sometimes make network path-specific commands or services more difficult because everything is always changing. Just figured that little FYI might help somebody.

5. Thanks for the guide! The Ubuntu community is at least 50% of what makes Ubuntu so awesome! Keep it up!

---

### Post by majoridiot on 2007-03-28
just a heads up here...

i spent a bit of time trying to wake up two asus boards that just absolutley refused to comply.  after
digging a bit, it turns out that there are a series of bugs in the *forcedeth* driver that bugger up the
whole "magic number" scenario.  this bug is confirmed with no workaround found (by me, unfortunately)
in the .54 version with edgy.

to see if this is a problem for you:

```
$ sudo ethtool -i eth0
driver: forcedeth
version: 0.54
firmware-version: 
bus-info: 0000:00:14.0
```

if your driver isn't forcedeth, then nevermind.

if it's .54 like mine above, then good luck.

if, for some reason, you have a newer forcedeth, ~.56-58-ish (i'm a stickler for these details!), 
and WOL isn't working, try *reversing* your mac address.  this has been confirmed to work in
some situations. 

e.g.- if your mac address is 01:02:03:04:05:06, reverse it to 06:05:04:03:02:01 in your wakeonlan
call.

on the positive side, the forcedeth included out of the box with a fully updated feisty works ***perfectly.***

:)

---

### Post by StewD on 2007-04-24
Hi,

Excellent instructions, they work beautifully....however.....I really want to get WOL working from a SUSPEND state, rather than the SHUTDOWN state shown here.

I've seen a hint that the problem is a "-i" being used when the machine is suspended [//http://stewart.psych.warwick.ac.uk/linux/wol/]("//http://stewart.psych.warwick.ac.uk/linux/wol/"). The text on this link indicates how to change this for "halting" but not for suspending.

Does anyone know what script is run when the suspend option is selected? (Also for hibernate).

Cheers,

Stewart

---

### Post by majoridiot on 2007-04-24
glad you found this useful! :D

check your BIOS settings for the suspend state- i know that my mobos will let you choose the  state you want.
you might try setting that to either S1, S3 or both... possibly even S4 and then shutting down with:

```
$ sudo shutdown -h now 
```

which will call for a halt without explicitly stating the halt action is a poweroff.

the state you need is based on the actual BIOS support, which in many cases is based on MS compatibility, so it 
can be sketchy... depending.  you will probably need to play around with the various states and test which is 
the most reliable for you and your mobo.

---

### Post by sefs on 2007-04-24
Great tutorial.

Now how do we get it to work over the internet.  That would be superb!

---

### Post by majoridiot on 2007-04-24
> **sefs said:**
> Great tutorial.

Now how do we get it to work over the internet.  That would be superb!

you know, i really hate posts like this one... because they tend to make me curious to the point of distraction. :razz:

depending on your hardware and connection, you **can** wake over the internet.  if you have a direct connection
(no router) then it should wake just by sending the packet to your internet ip adress.  if you are behind a router,
then it gets somewhat more complicated, as routers aren't set up to do broadcast messages very well- but
switches and hubs are.

i did get my testbox to wake via the internet (command sent from amsterdam woke my box in the US)- even going
through my linksys WRT54G... which was a pain.  that model router isn't config'd by default for this sort of operation,
but i was able to configure it.  in router setup:

configure the local subnet mask for the LAN to be 255.255.255.128 (it was 255.255.255.0 by default)

port forward an arcane, unused port (i used 42420 to test) to forward TCP and UDP to 192.168.1.127- which
will broadcast anything sent to that port to all comps on the subnet.  when the sleeping box sees its magic
number, it will wake up.

the command for the internet wake is:

```
$ wakeonlan -p <the port you forwarded> -i <your internet address> <MAC to wake>
```

if you want an easy web-based page to remotely test the wake, go here:

[http://www.depicus.com/wake-on-lan/woli.aspx](http://www.depicus.com/wake-on-lan/woli.aspx)

***Note: on this page, the "correct" subnet mask to use in my linksys setup was 255.255.255.255***

for a more complete test, i set both my testbox and my mythbackend for WOL and woke each individually.
another test then awoke both with a single wakeonlan command from amsterdam- they both booted within moments of hitting enter.

again, this was for the linksys WRT54G, so your mileage may vary... but it is doable. :D

---

### Post by sefs on 2007-04-24
Now thats what i am talking about right there.

I have the wrt54gl so i dont see why this should not work for me too.

---

### Post by majoridiot on 2007-04-24
> **sefs said:**
> Now thats what i am talking about right there.

I have the wrt54gl so i dont see why this should not work for me too.

it should... set it up as i described :D

---

### Post by joeashcraft on 2007-05-14
Has anyone tried this with the *crappy* 2Wire Home Portal? I can't figure out if it's the NICs problem or the router's problem, but it doesn't work for me, sadly. I have my server set to be the DMZ client so port forwarding shouldn't be a problem.

---

### Post by kamatschka on 2007-05-22
HI!


I have a Linksys WRT54GS router and I'm using a Linksys WMP54GS with Broadcom Chipset in my Computer...
I'm using a DFI Lanparty NF4 UT Ultra-D Mainboard and the 2 WOL settings in the Bios are enabled!

I've installed Feisty Fawn and the Wlan is working though! 

So.. I want to use WOL over Wlan (eth2)...


when I want to see the settings over ethtool following is shown after runnin the command "sudo ethtool eth2"   :

```
Settings for eth2:
        Link detected: yes
```

and after running:

```
sudo ethtool -s eth0 wol g
```

it shows me this:

```
Cannot get current wake-on-lan settings: Operation not supported
  not setting wol
```

So..  has anyone a solution to get WOL with ethtool working on My wlanCard "Linksys WMP54GS"..?!


I am thankful for every Hint/Help to get this thing working!


greetz kamatschka

---

### Post by 241comp on 2007-05-25
> **kamatschka said:**
> HI!

So..  has anyone a solution to get WOL with ethtool working on My wlanCard "Linksys WMP54GS"..?!



According to LinkSys, the WMP54GS does not support WOL.

---

### Post by t.lauckner on 2007-07-07
Hello,

thank you for helping me getting WOL to work. But currently my notebook only wakes up when running in suspend-to-mem mode, e.g. after prompting
```
echo mem > /sys/power/state
```
That's a good start, but I'd like to boot my machine up after shutdown, e.g. after running "shutdown -h now" or alike. Is it at least theoretically possible that this will work?

My hardware specs:
```

Dell Inspiron 9400
LAN: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

$ sudo ethtool eth0
Settings for eth0:
(...)
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x000000ff (255)
        Link detected: yes

```
My current BIOS Settings:
```

LAN-PXE: on
WAKE-ON-USB: off

```

---

### Post by ingo on 2008-01-28
> **kamatschka said:**
> HI!


I have a Linksys WRT54GS router and I'm using a Linksys WMP54GS with Broadcom Chipset in my Computer...
I'm using a DFI Lanparty NF4 UT Ultra-D Mainboard and the 2 WOL settings in the Bios are enabled!

I've installed Feisty Fawn and the Wlan is working though! 

So.. I want to use WOL over Wlan (eth2)...


when I want to see the settings over ethtool following is shown after runnin the command "sudo ethtool eth2"   :

```
Settings for eth2:
        Link detected: yes
```and after running:

```
sudo ethtool -s eth0 wol g
```it shows me this:

```
Cannot get current wake-on-lan settings: Operation not supported
  not setting wol
```So..  has anyone a solution to get WOL with ethtool working on My wlanCard "Linksys WMP54GS"..?!


I am thankful for every Hint/Help to get this thing working!


greetz kamatschkaMight be a little late now but if you want it to wake up eth2 then you have to change  ```
sudo ethtool -s eth0 wol g
```to ```
sudo ethtool -s eth2 wol g
```I am still battling with mine...

---

### Post by ingo on 2008-01-28
I'm nearly there, I can feel it...

Still need to know how I configure which port ethtool should use - or am I missing something basic here???

Also unsure of the local subnet mask and how to configure it although this is not crucial yet. 

I want to know the port, the port, the port!!!

Cheers in advance

---

