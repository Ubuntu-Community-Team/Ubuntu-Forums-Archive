---
title: "Multiple ADSL Modems/Routers?"
date: 2008-04-13
forum: General Help
---

### Post by intense.ego on 2008-04-13
I have an ADSL 2+ connection in my home and, at the moment, all i have is the ADSL modem/router I was given free by the ISP (its terrible, BTW). Almost every room in the house has a telephone plug and I prefere wired over wireless (because its faster), but I would still like to have wireless. Is the following set up possible? I'm not sure whether more than one modem/router can connect to the internet at one time.

The default modem/wifi router in one room, with wifi on, but also connect wired to a computer.

Two of these [http://www.ebuyer.com/product/132455](http://www.ebuyer.com/product/132455) in different rooms, each of them connected wired to a computer. (no wifi, they don't have that ability anyway)

And one of these [http://www.ebuyer.com/product/113934](http://www.ebuyer.com/product/113934) in another room, giving off a wifi signal, and also connected to a computer.

---

### Post by diablo75 on 2008-04-13
You can only use one DSL modem per account with your ISP because each modem has a specific MAC address assigned to it that the ISP uses to send data to the modem.  So you can't use the phone jacks in the other rooms for more modems.  But what you could do is connect your DSL modem to a switch or another plain old router, and run CAT5 hard lines to the other computers you want wired.

But for simplicity sake, I would go wireless with strong WPA encryption.  It takes far less time to setup.  I've been using Wireless G for a while now, a huge improvement over Wireless B, and if you want cutting edge, Wireless N is the way to go (it's the first consumer wireless technology that I know of that supports full duplex communication... look up the stats on it.  The bandwidth on Wireless N is incredible to say the least).

---

### Post by intense.ego on 2008-04-14
thank you. is there any specific way to set up a new modem/router, or will just pluggin it in without the old one suffice?

Also, would it be possilble to set up the old router as an access point to improve wireless signal?

---

### Post by intense.ego on 2008-04-14
anyone?

---

### Post by intense.ego on 2008-04-14
*bump*

---

### Post by diablo75 on 2008-04-14
> **intense.ego said:**
> thank you. is there any specific way to set up a new modem/router, or will just pluggin it in without the old one suffice?

Also, would it be possilble to set up the old router as an access point to improve wireless signal?

You can simply use a plain old ethernet cable to run from your DSL modem to the uplink port on another router (the uplink port is where a cable or DSL modem would normally connect).  And that's all you should have to do.

You could set up the router to act as a second wireless access point, but you will want to avoid using the same radio frequency as any other wireless access points you have set up.  The rule of thumb is to pick either channels 1, 6 or 11.  Don't pick the others in between or you'll get signal overlap and decreased performance.  So set one router to run on channel 1, the other on 6 or 11 and you'll be in good shape.

I am not very experienced about setting up large WLAN's, but to keep things simple, you should assign different ESSID's to each wireless access point.  Good luck!

---

### Post by louieb on 2008-04-14
I know Netgear had a wireless extender   You could set up something like this.
Line in>modem>wireless router> to computers via wire or wire less and to the wireless extender. 

Out of the wireless extender  you can hook up more computers via wire or wireless.  

Hope this makes some scene. 
[http://search.ebay.com/wireless-extender_W0QQfnuZ1QQfsooZ2QQfsopZ32QQrprZ8QQxpufuZx](http://search.ebay.com/wireless-extender_W0QQfnuZ1QQfsooZ2QQfsopZ32QQrprZ8QQxpufuZx)

---

### Post by fragos on 2008-04-14
Any wireless router will work out of the box unless your ISP blocks all but one MAC address. Hardwire your main PC to the router and connect the router uplink to the ADSL modem. The router will use NAT and DCHP to assign any wired or wireless connected device a local IP. The router will have a fixed local IP which you can use in a brower to to perform router admin. The only thing that may be required is to clone your PC MAC address in the router. Most have a function to do this for you. Before messing with security insure that your wired and wireless devices can connect to the internet. The routers firewall and NAT addressing will protect your network from access through the internet. If you don't have wireless security enabled, anyone in radio distance, less than 300ft, can access the internet. Access to the connected PC's is protected somewhat by the connected PC's. I leave my wireless open for others but power down my computer and the router when not in use. My other wireless devices are powered down when not in use. It takes a hacker to break in assuming the machine and router are running in the 1st place. Adding wireless security is up to you. Mine is open because I have on occasion accessed others open links and its only fair to leave mine open as well. Each to their own.

---

### Post by intense.ego on 2008-04-15
Would it be possible to set up the other router as a wireless extende without connecting via ethernet. Can't the router pick up the wifi signal from the first router and just pass it on?

---

### Post by diablo75 on 2008-04-15
> **intense.ego said:**
> Would it be possible to set up the other router as a wireless extende without connecting via ethernet. Can't the router pick up the wifi signal from the first router and just pass it on?

Well, I don't know if you could do it with a router.  You could with an Wireless Access Point, setting it to "Bridge Mode".  Then tell it to authenticate with the first wireless router.  How far apart are these computers?  More than say.... 200 or 300 yards?

---

### Post by intense.ego on 2008-04-15
> **diablo75 said:**
> Well, I don't know if you could do it with a router.  You could with an Wireless Access Point, setting it to "Bridge Mode".  Then tell it to authenticate with the first wireless router.  How far apart are these computers?  More than say.... 200 or 300 yards?

Definitely less than 200-300 yards. The one is on the bottom floor of my 4 floor house here in London, and the other is on the top floor.

---

### Post by intense.ego on 2008-04-16
anyone?

---

### Post by fragos on 2008-04-16
> **intense.ego said:**
> Would it be possible to set up the other router as a wireless extende without connecting via ethernet. Can't the router pick up the wifi signal from the first router and just pass it on?

If you want to extend your signal farther, buy an optional antenna and that will create a stronger signal. They're also cheaper than a 2nd router. Check the antenna connecter on your device many are the same. If you're into DIY you can even make a directional antenna that focuses the signal.

---

