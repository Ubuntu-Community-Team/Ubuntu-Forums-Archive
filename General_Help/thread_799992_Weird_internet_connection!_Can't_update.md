---
title: "Weird internet connection! Can't update"
date: 2008-05-19
forum: General Help
---

### Post by bferd on 2008-05-19
Hi I installed hardy on two of our computers about a week ago. Everything was fine until yesterday when I couldn't view some of the web pages that I wanted to. Some pages work fine and others don't. All that shows in the browser window is DNS Error. For example google.ca loads fine but when I click on the images link DNS Error comes up. Most of the other links work like Maps, Calendar, etc. But if I do a search for something, most of the resulting links give DNS Error unless I click the "cached" link then the page comes up (something is right screwed up)

Update manager gives errors as well. 

See ScreenShot

The Internet works fine on my gusty box (the one I'm working on now) just not the two hardy machines.

Oh ya! The same thing happens in firefox, opera, and seamonkey.

Any ideas

---

### Post by bferd on 2008-05-19
Anybody?

---

### Post by bferd on 2008-05-19
I need this fixed and I need to know where to start.

---

### Post by bferd on 2008-06-05
I've tried reinstalling which worked until yesterday. Yesterday I did the updates and installed samba.

Can anybody help me figure this out? I really like Hardy for the features it has and I don't really want to go back to Gusty.

---

### Post by renfrew on 2008-06-05
You don't really say much about your configuration other than you've got two computers. are you running a home network through a router with the computers networked through it?

I couldn't see all of the output from the ifconfig, can you try pasting it here?

---

### Post by bferd on 2008-06-05
Here it is:

brad@BJS:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2f:14:46:6f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:11:2f:14:3c:a9  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3505948 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2057084 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:717348109 (684.1 MB)  TX bytes:167199271 (159.4 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8300 (8.1 KB)  TX bytes:8300 (8.1 KB)

brad@BJS:~$

---

### Post by renfrew on 2008-06-06
Ok, I can't see anything wrong with the ifconfig output...

I should have asked for your hosts file , can you 'cat /etc/hosts' and paste it here.

You might want to try pinging out directly from your router and the affected system too, not sure what router you've got but you should be able to ping an external host from one of your routers status pages.

I'm trying to diagnose this remotely thru the forum, we could end up going back and forth here a bit.  If you find I'm  not giving much help you might want to try the #ubuntu channel on irc.freenode.net... at least it's in realtime

---

### Post by bferd on 2008-06-06
brad@BJS:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 BJS.SCHROTHNET BJS

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.0.102 wins
brad@BJS:~$

---

### Post by bferd on 2008-06-06
Thanks for your help I figured it out (by accident) although I can't explain it.

My storage server is running Gusty, and my router was set to auto assign an IP address (192.168.0.120) via the mac address. My other computer (with the connection problems) is running Hardy. Today I turned Hardy computer on with Gusty server still off and everything worked fine, internet and updates. When I turned on the Gusty server and mounted My smb shares in the Hardy computer everything was screwed up again.
I disabled the auto assign function on my router and set the Gusty server a static IP and everything seems to work OK except I cant see the Gusty server in the Network Servers window.

What a strange effect this caused. Google working and a few other sites but most sites not working, some packages downloading from the update server and some not.

If I knew more about this kind of thing I would investigate what was actually happening.:)

---

