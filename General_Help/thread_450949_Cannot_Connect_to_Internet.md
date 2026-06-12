---
title: "Cannot Connect to Internet"
date: 2007-05-21
forum: General Help
---

### Post by chirojpo on 2007-05-21
Hi all,

I have Ubuntu 7.04 installed on an old Compaq Presario 700 laptop, but I cannot connect to the internet.  I have cable internet (through Comcast) and am going through their router.  Please help.  Thanks.

---

### Post by jerrylamos on 2007-05-21
Well, I don't have much info, here's a couple things to check.  With 7.04, there should be a little icon on the top line over toward the right that looks like a monitor with another one behind it. That's the Network manager.

Does it have a red mark on it?  If so, click on it, then click on wired connection.  With any kind of luck there should be a little whirly icon and after a while it might connect.  If so, try Firefox.  If not, post anything you see here.

If that doesn't do it, then click on Applications, Accessories, Terminal which should give you a command line.  Then do:
sudo dhclient
which will ask you for your regular password.  Do note if you connect this way, the Network Manger Icon may still have a red mark on it, since it doesn't know you did a dhclient.

Try Firefox again.  If still doesn't work, switch back to the Terminal session and do:
ifconfig  

which should give you something like this:
eth0      Link encap:Ethernet  HWaddr 00:40:05:55:80:47  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:5ff:fe55:8047/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:6 txqueuelen:1000 
          RX bytes:13959717 (13.3 MiB)  TX bytes:1423778 (1.3 MiB)
          Interrupt:11 Base address:0xe400 

The item of interest is the inet addr.  If you have one, in theory you should be able to connect.  If you don't, post the first 4 lines or so.

Patience, we're working blind with you.

---

### Post by chirojpo on 2007-05-22
Okay, here is what happens.  I plug the ethernet cable in and the network manager says "connected to a wired network."  Then I click on firefox and the Ubuntu homepage opens.  Then I click on any other link (even the ones on the Ubuntu page) and it says "Server not found."  Any ideas now?  No other pages can be accessed.

---

