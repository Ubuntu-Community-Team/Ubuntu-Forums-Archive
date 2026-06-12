---
title: "Problems w/ Seamless setup on virtualbox!"
date: 2007-07-14
forum: General Help
---

### Post by kris2pe on 2007-07-14
I get this error:

Failed to open '/dev/net/tun' for read/write access. Please check the permissions of that node. Either do 'chmod 0666 /dev/net/tun' or change the group of that node and get member of that group. Make sure that these changes are permanently in particular if you are using udev.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

Now this is becoz I used the network option=>  Host interface 

But if I use NAT everything seems to work out fine!
I need this becoz this guide [http://ubuntuforums.org/showthread.php?t=433359&highlight=virtualbox+seamless](http://ubuntuforums.org/showthread.php?t=433359&highlight=virtualbox+seamless)
says that I need to set it as host interface! 
Pls HELP!!!

---

### Post by HermanAB on 2007-07-14
VirtualBox works nice when it works.  Give the free VMware Server a try - slow, but reliable and very easy to use.

---

### Post by kris2pe on 2007-07-14
It works but I can't get it to work seamlessly! 
I think becoz my works on NAT but the guide says I have to use Host interface!
Do you get what I'm trying to say here!!!

---

