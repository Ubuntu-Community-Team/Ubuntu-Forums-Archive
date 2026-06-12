---
title: "Can't connect to wired network."
date: 2008-05-20
forum: General Help
---

### Post by The-Bleh-Bleh on 2008-05-20
I'm new to Linux and liking it.  I recently wired the house for a network, which so far has the following setup (the computer I'm using is directly connected to the router):


Modem
[COLOR="White"]. .. [/COLOR]|
[COLOR="White"]. .. [/COLOR]|
 Router----------Switch
[COLOR="White"]. . . . . . . . . . . . . . [/COLOR]|
[COLOR="White"]. . . . . . . . . . . . . . [/COLOR]|
[COLOR="White"]. . . . . . . . . . . .[/COLOR]Ubuntu desktop


Now, the router seems to have a perfect connection to the switch, the switches indicator light for that port is always flickering.  

But the desktop, which has Ubuntu 8.04 on it can't connect to anything.  There is an indicator light for the desktop, and it's lit up on the switch.  But it's a solid light, it rarely flickers.

So, this could be 3 problems:
- Ubuntu won't recognize the network.
- Wiring from switch to the desktop is messed up.  (Would this be possible even though there is an indicator light that's on for this connection?)
- The switch for some reason isn't making the connection from the router to the desktop. (I don't see why it wouldn't)


So, any guesses for what's wrong here?  When I click "connection information" on the desktop, it it's just all 000.000.0.0 sort of things.  But... the indicator light is on the switch.  I just don't get it, what could be wrong?  Ubuntu's fault, the wiring, or the brand new switch?  Thanks for any help, I would love to get Ubuntu running.

---

### Post by Gunman1982 on 2008-05-20
Is the router providing dhcp?
How many network cards are in your linux machine?
Did you try to set a static IP on the linux machine and ping the router?

Can you check what the command 'sudo ifconfig' returns? (Should show atleast two devices ethx and lo)

---

### Post by alxlabs on 2008-05-20
Well there are more than one possible reasons, I would not mind to know few more things to say something more certain...

1. Do you expect adresses to be assigned via DHCP by router? If yes, then is router configured for DHCP?
2. Do you have any other machine working on your network and connected to swicth?
3. Does your desktop 2 see neetwork if connected straight to router?
4. Can you ping the router? Other machines on the network? Are there other machines on your network?

Also pls. run from terminal "ifconfig" then "route -n" and post results here

---

### Post by The-Bleh-Bleh on 2008-05-20
Thanks for the interest!

> **Gunman1982 said:**
> Is the router providing dhcp?
**Yes, the computer I'm using is connected to dhcp**

How many network cards are in your linux machine?
**I would guess 1, but... are there sometimes more than 1 on a computer, and would that be a problem?**

Did you try to set a static IP on the linux machine and ping the router?
**I didn't try setting up a static IP, but I can't ping the router without a static IP.**

Can you check what the command 'sudo ifconfig' returns? (Should show atleast two devices ethx and lo)
**I'll be a few minutes, I'll have to start it up, and it will take me a bit**



> **alxlabs said:**
> 
1. Do you expect adresses to be assigned via DHCP by router? If yes, then is router configured for DHCP?
**Yes, the XP computer I'm using is connected directly to the router, and it's using DHCP.**

2. Do you have any other machine working on your network and connected to swicth?
**Just one that's connected to the router directly, which works.**

3. Does your desktop 2 see neetwork if connected straight to router?
**I haven't tried, since I would have to bring it all the way over here.  But I will try that first.**

4. Can you ping the router? Other machines on the network? Are there other machines on your network?
**Nope, I get no response.**

Also pls. run from terminal "ifconfig" then "route -n" and post results here
**Okay, I'll try that**

I'll be right back, I'll try the ifconfig info and get back to you.

---

### Post by ubuscout on 2008-05-20
> **The-Bleh-Bleh said:**
> 
...
But desktop 2, which has Ubuntu 8.04 on it can't connect to anything.  There is an indicator light for Desktop 2, and it's lit up on the switch.  But it's a solid light, it rarely flickers.

...so do u mean there is also a desktop "1"  working fine.. ?

[QUOTE=][I]
So, this could be 3 problems:
- Ubuntu won't recognize the network.
- Wiring from switch to desktop 2 is messed up.  (Would this be possible even though there is an indicator light that's on for this connection?)[/I][/QUOTE]

usually if light indicator is on (green led example) the link is up...  except if switch light with different color (otherwise orange could mean collision for some model of switch...)

[QUOTE=][I]
- The switch for some reason isn't making the connection from the router to the desktop. (I don't see why it wouldn't)

So, any guesses for what's wrong here?  When I click "connection information" on desktop 2, it it's just all 000.000.0.0 sort of things.  But... the indicator light is on the switch.  I just don't get it, what could be wrong?  Ubuntu's fault, the wiring, or the brand new switch?  Thanks for any help, I would love to get Ubuntu running.[/I][/QUOTE]

...here maybe could useful if u put your config...  by  "ifconfig -a"  for example...  and the router and switch conf   ...

---

### Post by The-Bleh-Bleh on 2008-05-20
Well here's what I got:

sudo ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:16:ec:30:e1:4d  
          inet6 addr: fe80::216:ecff:fe30:e14d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5543 (5.4 KB)
          Interrupt:19 Base address:0xc000 

eth0:avahi Link encap:Ethernet  HWaddr 00:16:ec:30:e1:4d  
          inet addr:169.254.7.132  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65392 (63.8 KB)  TX bytes:65392 (63.8 KB)

```


route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

```



> **ubuscout said:**
> ...so do u mean there is also a desktop "1"  working fine.. ?
Sorry, I was messing around with wording.  Desktop 2 = Ubuntu computer.
The Desktop I'm using is connected directly to the router and works fine, while the Ubuntu desktop is connected to the switch, and doesn't work.

---

### Post by alxlabs on 2008-05-20
From what I see - DHCP did not work, none of the addresses got assigned.

If your another machine connected straight to router can see the network, then problem is either swicth or cable (it could be wrong type) or Ubuntu machine configuration. If you did not mess up with your network configurtaion (I would assume you haven't done so) then most likely problem is switch itself or cable. The best test is to connect your Ubunutu machine exactly top the same place as your another working desktop, using SAME cable as for the working XP machine.

---

### Post by The-Bleh-Bleh on 2008-05-20
Thanks a ton for the help, I'll try connecting the computer directly to the router, and get back to you with results.

---

### Post by ubuscout on 2008-05-20
...ok, straightforward could be choice a static ip for your wired connection in ubuntu by network manager ...keepin' in mind same subnet and different ip of course and dns with ip router...  and try simple to ping the ip router first, and after let's see...

---

### Post by The-Bleh-Bleh on 2008-05-20
But I can't even ping the router.  I just tried connecting Ubuntu directly to a the router... I can't even get a ping.  Does this mean Ubuntu isn't dealing with my network card correctly?

If it doesn't make sense it's doing this, I could try lugging the computer all the way to where the one I'm using now is and use the exact same wire to the router to be sure.  It's just heavy.

---

### Post by alxlabs on 2008-05-20
Have you tried to use the cable from the working setup?

PS You won't be able to ping anything unless you have a valid ip adress assigned. It can be done thru the dhcp but once this does not work - you can do it manually (don't forget the subnet mask) just make sure that you pick an address from the same network.

---

### Post by alxlabs on 2008-05-20
One more thing - post here content of your /etc/network/interfaces file as well as output of the follwing command "lspci -vvn"

---

### Post by alxlabs on 2008-05-20
sorry, lspci -vv

---

### Post by The-Bleh-Bleh on 2008-05-20
Thanks alxlabs.  I figured I would be able to ping the router even without an IP.  All I had to do was give myself a static IP and it worked.  Many thanks!  Ubuntu is up and runnin'!

---

### Post by The-Bleh-Bleh on 2008-05-20
Duplicate post, sorry.

---

### Post by Cap'n Skyler on 2008-05-20
> **The-Bleh-Bleh said:**
> Thanks a ton for the help, I'll try connecting the computer directly to the router, and get back to you with results.

if it is a cabling issue,double check and make sure your ethernet cables are the kind with molded on ends.i have had the kind you make(not molded ends) have the wires break (at the plug and cable joint).also the retaining clips do break and let the plug slip out just enuff to break the connection and still appear to be plugged in like it is supposed to.never skimp on quality cables.

best of luck

Moofs:guitar:

---

### Post by The-Bleh-Bleh on 2008-05-20
> **Cap'n Skyler said:**
> if it is a cabling issue,double check and make sure your ethernet cables are the kind with molded on ends.i have had the kind you make(not molded ends) have the wires break (at the plug and cable joint).also the retaining clips do break and let the plug slip out just enuff to break the connection and still appear to be plugged in like it is supposed to.never skimp on quality cables.

best of luck

Moofs:guitar:

I actually have been crimping my own cables.  So doing it yourself means the cables are worse quality?

---

