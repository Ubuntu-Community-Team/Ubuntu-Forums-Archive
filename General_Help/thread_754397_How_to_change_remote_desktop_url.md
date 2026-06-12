---
title: "How to change remote desktop url"
date: 2008-04-13
forum: General Help
---

### Post by xVehemencityx on 2008-04-13
Okay, here's the dilemma.  I want to be able to remote connect from one pc to another in my house, but retardedly, I named them both the same thing, so when I type in the name of my pc in vncviewer, it just makes me view the computer I'm on.  I changed the name of my pc, but the remote desktop url didn't change.  How do I change it?

---

### Post by diablo75 on 2008-04-13
I would just use the IP addresses if I were you.  You can always count on them if you set them up statically, and if you set a static port forward route on your router, as well as a DynDNS account (if your router supports it) you'll be able to access your computers while you're away from home with reliable ease.

---

### Post by xVehemencityx on 2008-04-13
> **diablo75 said:**
> I would just use the IP addresses if I were you.  You can always count on them if you set them up statically, and if you set a static port forward route on your router, as well as a DynDNS account (if your router supports it) you'll be able to access your computers while you're away from home with reliable ease.


Whoa.  I call myself a computer nerd, and yet I have no clue what that means.  I guess I could try the IP thing.  Except, I don't need to connect to them when I'm away from home, because I'm literally the only person I know with Linux.

---

### Post by xVehemencityx on 2008-04-13
Nope.  the IP thing doesn't work right now.  I need to figure out how to set them up statically.  Also, how do I set a static port forward, and use DynDNS?  I'm a little bit of a wireless newbie.

---

### Post by xVehemencityx on 2008-04-13
Okay, I made a DynDNS account. Now what?

---

### Post by diablo75 on 2008-04-13
OK.  First, check to see what IP address your router has.  You can do this in terminal by typing in the word "route", pressing Enter, then to the right of the word "default" should be the default gateway (your routers IP).... this will be handy later.

To set a static address up, you need to enter the appropriate network interface's config.  Do this via:

System>Administration>Network

In there, you should see your wireless device listed.  By default, it will have roaming mode enabled.  This is what allows the network management applet at the top to take control of associating and authenticating with a wireless router.  Uncheck the roaming mode box, and then you should be able to select your wireless network, enter your wireless encryption password (if it's WEP, you will likely want to tell it that you're using a Hex password, not an ASCII password).  Then below that, you can type in an IP address.

Set a static IP address similar to the one of your router.  If it's address is 192.168.1.1, make yours 192.168.1.2 or even 192.168.1.12...it's really up to you.  The subnet mask should set itself up by default, and the gateway address is (you guessed it) the IP address of your router.

Setting up a static IP on an Ethernet Interface works in the same way, by disabling Roaming mode, and typing in the addresses you want.

Good luck!

P.S.

If you're familiar with Windows's "ipconfig" command, you can familiarize yourself with Linux's "ifconfig".  Further information can be found by typing "man ifconfig" into the terminal (which will open ifconfig user manual.... you can just close the terminal when your done looking through it).

Good luck!

---

### Post by diablo75 on 2008-04-13
The DynDNS thing needs to be a supported feature of your router.  All you should have to do is enter your routers internal config settings, look around for DynDNS.org in there, and then enter your username and password.  I have a netgear router, which does this quite nicely, even lets me test the login before I save my settings.

What this will do is tell DynDNS the external IP address of your router (external meaning "on the Internet" so to speak, Internal meaning your LAN).

The next step is to set up port fowarding (you don't need this for Internal remote desktop sessions, only for connections that inbound from the Internet).

For more info about port forwarding, visit this link:  [http://portforward.com/help/portforwarding.htm](http://portforward.com/help/portforwarding.htm)

---

### Post by xVehemencityx on 2008-04-13
Okay, well, for that ipaddress, it just says chAdmin.  And, I randomly changed something on my second pc, and I lost connection, and when I changed it back, I still don't have connection.  I've got a bad feeling about this.

---

### Post by xVehemencityx on 2008-04-13
> **xVehemencityx said:**
> Whoa.  I call myself a computer nerd, and yet I have no clue what that means.  I guess I could try the IP thing.  Except, I don't need to connect to them when I'm away from home, because I'm literally the only person I know with Linux.

> **diablo75 said:**
> The DynDNS thing needs to be a supported feature of your router.  All you should have to do is enter your routers internal config settings, look around for DynDNS.org in there, and then enter your username and password.  I have a netgear router, which does this quite nicely, even lets me test the login before I save my settings.

What this will do is tell DynDNS the external IP address of your router (external meaning "on the Internet" so to speak, Internal meaning your LAN).

The next step is to set up port fowarding (you don't need this for Internal remote desktop sessions, only for connections that inbound from the Internet).

For more info about port forwarding, visit this link:  [http://portforward.com/help/portforwarding.htm](http://portforward.com/help/portforwarding.htm)

I'm really sorry for being so stupid, but how do I enter my internal config settings?

---

### Post by diablo75 on 2008-04-13
It's best to change your routers internal settings using a computer thats PHYSICALLY attached to the router via a ethernet cable.

Finder your router in this list:

[http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)

---

### Post by xVehemencityx on 2008-04-13
> **diablo75 said:**
> It's best to change your routers internal settings using a computer thats PHYSICALLY attached to the router via a ethernet cable.

Finder your router in this list:

[http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)

Yeah, I'm on said computer.  How do I do it though?

---

### Post by diablo75 on 2008-04-13
> **xVehemencityx said:**
> Okay, well, for that ipaddress, it just says chAdmin.  And, I randomly changed something on my second pc, and I lost connection, and when I changed it back, I still don't have connection.  I've got a bad feeling about this.

I forgot to mention that after you disable roaming mode and set a static IP address, it's often good to restart the computer entirely.

If this fails, you can just re-enable roaming mode and restart again.  The restarting is for the routers sake, not the computers.

---

### Post by xVehemencityx on 2008-04-13
Okay, well, when I put the IP Address in the address bar, it just waits a minute and times out.  I noticed that when I tried to do this on windows, too.  Is that something my ISP can do?

---

### Post by diablo75 on 2008-04-13
> **xVehemencityx said:**
> Yeah, I'm on said computer.  How do I do it though?

If you go to the link I provided, and find your router, you'll be presented with a big selection of programs.  Find VNC in the list to see a tutorial about how to add a port forward route to your router (but view it for example purposes only, the pictures they show may not match your router exactly, but will be close).

Setting up the DynDNS.org in your router is not related to port forwarding, and whether or not your router supports this feature is still unknown to me (I don't know what kind of router you're using).

---

