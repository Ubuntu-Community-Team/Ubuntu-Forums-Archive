---
title: "Cannot connect to router"
date: 2007-03-18
forum: General Help
---

### Post by Muzer on 2007-03-18
OK, I recently switched from Windows and installed ubuntu, and I went into admin-network, configured the wireless card, correctly (I think), I went into DNS, added the 2 DNS servers, Tried to connect... nothing. Just Firefox cannot display this page or something. So yeah, problem. I tried disabling security, among other things, but all to no avail.

---

### Post by zvacet on 2007-03-18
You did it O.K. but missing last step
```
sudo pppoeconf
```

---

### Post by Muzer on 2007-03-18
Thanks! Will try it now! Oh, and I am quite a linux noob, I'm assuming you type that into the terminal.

---

### Post by Muzer on 2007-03-18
Still no luck. Are wireless cards called ethx? That's the only thing found (eth0). If not, there's something wrong. If they are, there's still something wrong. I get "Sorry, I scanned 1 interface, but the access concentrator of your provider did not respond".

---

### Post by Muzer on 2007-03-18
Still haven't fixed it :( (Sorry for tripple post)

---

### Post by mrmonday on 2007-03-18
Are you able to connect to your wireless network? or is it the internet you can't get to?

---

### Post by jimbob on 2007-03-18
No, eth0 (ethx whatever) is your wired interface card.  You should see something like wlan0 or ath0 etc.  What kind of wireless card is it?

Make sure you have network manager installed.  (sudo apt-get install network-manager)

Use network manager to do the wireless setup, not the network admin on the system admin menu.

Post a copy of the output from ifconfig -a
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Muzer on 2007-03-18
I think I've found the answer, but I'm and my grandma's house at the mo so I can't try it out. Someone said on another forum that with my card I have to install this thing that emulates windows drivers, and then delete (blacklist) the linux driver, as it doesn't work. Thanks, anyway!

---

### Post by fragos on 2007-03-18
Last wifi access I installed in Dapper 6.06 gave the device name eth1 to my wireless.  I to had to blacklist a Broadcom driver and use ndiswrapper with the Windows driver.  I recommend that you add the Network Monitor applet as its icon will show signal strenggth when connected wirelessly.  Also you will need a network manager to set the wifi parameters and select which of the availble signal you wish to use.  IMHO wifi-radar is superior to gname-network-manager.  Synaptic package manager can install wifi-radar for you.  You may only have one network manager installed as two will interfere with each other.

---

### Post by CocoAUS on 2007-03-18
Yeah, it sounds like you need to use ndiswrapper to install your wireless card.  You'll probably also have to change eth1 or whatever to wlan0 in your /etc/iftab file so that your PC will see it as wireless.

Even if you get it installed, though, some routers just don't play nice with Linux.  I can't connect to my home network, but I can connect to other networks around us.

---

