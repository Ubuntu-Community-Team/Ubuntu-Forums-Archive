---
title: "ICS with Xbox 360 (gutsy)"
date: 2008-01-04
forum: General Help
---

### Post by chrisyuan01 on 2008-01-04
Hey everyone, I am new to Ubuntu, and I ask how I should go about using ICS on my Xbox 360.  The Xbox is connected to my (laptop) computer by ethernet cable, and then my computer connects wirelessly to my router, which is a Linksys WRT54G.  I have installed firestarter, except I do not know how to use it:confused::confused::confused:.  Can anybody help me out of my problem, as I have no other way to access Xbox Live.

EDIT:  Firestarter  only detects two network connections; I know that my wireless internet is eth0, but the other device is unknown, and not running.  Please tell me what this means!  I am very inexperienced with any linux operating systems, so if you could help me, it would be great!

---

### Post by chrisyuan01 on 2008-01-05
Nobody can help?

---

### Post by Mitch on 2008-01-05
I've never used internet connection sharing with Ubuntu.  However, I set this up with Mac OS last week to use Xbox Live. 

> 
I have installed firestarter, except I do not know how to use it.


I see that under edit -> preferences ->Firewall -> network settings there is a check box for connection sharing.  

> 
Firestarter only detects two network connections;


I think this is good.  One interface for your lappy's Ethernet and one for the wireless.  

> 
I know that my wireless internet is eth0, but the other device is unknown, and not running.


On my laptop  eth0 is my Ethernet connection and eth1 is my wireless network.  I believe this is more standard (not sure).  If one of the connections isn't working that sounds like a show stopper so I would focus on troubleshooting that and making sure that interface works in a normal setting (i.e. connect it to a wire and see if it works, or search the forum for a solution for an "unknown" Device in Firestarter).  Sorry if that's not much help.  Just make sure that it's not an Xbox issue tripping you up.  When I did this with OSX there were a lot of settings that needed to be configured on the Xbox 360.  Here is the [[COLOR="Red"]_article_[/COLOR]]("http://www.joystiq.com/2006/07/17/how-to-share-your-macs-internet-connection-with-your-xbox/") that I used.  It has information about configuring the Xbox that I think you will need.  Good luck.

---

### Post by chrisyuan01 on 2008-01-06
- thanks for the help.  Unfortunatly, my Xbox Live is still not up and running, so if nobody else can help, I will have to boot into windows every time I wish to play, and that's a daunting prospect by itself (waiting 6 minutes to boot up and log in).

Hope other people can help!

~Chris

EDIT:  My Wireless connection is eth1, and my ethernet is eth0.  Unfortunatly, Firestarter whines every time I open it that eth0 is not ready.  Any ways to fix this?

---

### Post by 043087m135 on 2008-01-12
Aight, here's how you make firestarter work. It requires a little additional editing of the xbox preferences.

Make sure you have your wireless and ethernet connections bonded via firestarter. If it refuses to start the firewall, it's because your ethernet either isn't up or it doesn't have an IP attached. To start your ethernet (assuming your ethernet connection is eth0, as it is on my system), type ```
sudo ifconfig eth0 up
``` Now you have to assign an IP address to your eth0 connection by typing ```
sudo ifconfig eth0 *ip address*
```. For simplicity, I used 10.0.0.1 as my ethernet adapter's IP address. 

Once your ethernet adapter has an ip, you shouldn't have trouble starting up the firestarter firewall with the connections shared. Make sure that you enable DHCP server for local network under Firestarter's preferences. The default values are fine.

Now the rest of the configuration occurs on the xbox side. Start your xbox and ensure that you set it up correctly. On the xbox's IP address, select Manual. The xbox's IP address doesn't really matter, as long as it is equal to your ethernet's plus 0.0.0.1. In example, if your ethernet is 10.0.0.1, make your xbox's 10.0.0.2. The subnet mask is 255.255.255.0. The Gateway will be your ethernet card's ip address (in this case 10.0.0.1, obviously). 

You'll also have to set up DNS server information for the xbox. Use your wireless router's gateway address - as your DNS server. Mine was 192.168.1.1.

And after this short configuration, viola! My system connected quite well. The only trouble I've experienced is that after restarting the xbox or signing out of xbox live my ethernet card will drop its ip address, which must be re-set by typing ```
sudo ifconfig eth0 10.0.0.1
``` but that can probably be fixed with some really simple script or setting, which i'm not bothering to post. Google it if it bothers you.

---

### Post by chrisyuan01 on 2008-01-18
THANK YOU.  If this works, I will be very grateful.  Thanks!

---

### Post by Joeb454 on 2008-01-18
You may need to bridge the connections...I had to do that once, I've since changed my setup, but I did have a script to do it all for me that I wrote...I'll try and find it

---

### Post by Joeb454 on 2008-01-18
Ok I think this should work...you have 2 network connections right? Wireless and Wired?

This script assumes that they are eth0 and eth1. Also you may need to change the permissions so they are executable.

First open up a terminal and run ```
 sudo apt-get install bridge-utils
``` this will install the necessary components.

Let say you save these 2 scripts in your home folder, you would run them by opening a terminal and running ```
./createbridge.sh
``` and ```
./renewbridge.sh
```

Next you need to run createbridge.sh this will create a network bridge :)

Anytime you log on afterwards, run renewbridge.sh


This used to work for me :)

---

### Post by chrisyuan01 on 2008-01-18
thanks!

---

### Post by Joeb454 on 2008-01-18
No problem :) Did it work?

---

### Post by chrisyuan01 on 2008-01-18
dunno... haven't gotten to it yet =P!

---

### Post by chrisyuan01 on 2008-01-18
I used the guy before you's response, and it worked perfectly!  Now how would I go about getting my NAT to open?

---

### Post by Joeb454 on 2008-01-18
That's actually quite difficult without plugging your Xbox straight into a router :(

---

### Post by chrisyuan01 on 2008-01-19
well, is there a way?  I'll try anything!  :)

---

### Post by chrisyuan01 on 2008-01-21
nobody?

---

### Post by Joeb454 on 2008-01-21
I've been trying it with my Xbox with different things, but not managed to get it to be Open without plugging straight into the router

---

### Post by penguin5 on 2008-04-28
> **043087m135 said:**
>  The only trouble I've experienced is that after restarting the xbox or signing out of xbox live my ethernet card will drop its ip address, which must be re-set by typing ```
sudo ifconfig eth0 10.0.0.1
``` but that can probably be fixed with some really simple script or setting, which i'm not bothering to post. Google it if it bothers you.

Anyone know a script that would allow the ethernet card to not drop its IP address ? 

Thanks in andvance.

---

