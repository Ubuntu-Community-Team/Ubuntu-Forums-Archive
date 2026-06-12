---
title: "New Ubuntu load: Can't access internet through Firefox"
date: 2005-10-29
forum: General Help
---

### Post by ubuntusupernewbie on 2005-10-29
Please help. I recently(today) loaded Ubuntu on my laptop.  I am running DSL from Qwest with MSN for the ISP. DHCP server. 

I can ping the DSL modem and google.com. I can also wget files. 

I get a timeout error in Firefox. "Connecting to www.google.com" and then that is it.  

ifconfig of eth0 seems ok.  the dns server is right.  I don't know what to do!!

There is no firewall.  

sudo apt-get gives me "couldn't stat source package list http://us.ubuntu.com....."

apt-get gives me "could not open lock file /var/lib/apt/lists/lock - open (13 permission denied)

Any ideas?

---

### Post by adwait on 2005-10-29
I guess there must be problems with your proxy settings in firefox. try Edit>Preferences>Web Features (I think)> Connection Settings. Check all the proxy settings.

---

### Post by xequence on 2005-10-29
When I do a fresh install I always have to go to network preferences and choose DHCP, then activate eth0.

---

### Post by Jon_cooper on 2005-10-30
I have a similar problem. I have installed Ubuntu on 2 machines 1 32-bit Hoary and 1 64 bit Breezy, both give me the same problem with Firefox. 
The problem seems really strange as I can click on links and reach pages. I can get here as the start page contains a link to [www.ubuntu.com](www.ubuntu.com) and then I can follow other links. 
However if I try to type in an address such as [www.google.com](www.google.com) in the address bar, no go it just times out. 
If I type in the ip address as a number it will take me to the address. 
Does the same work for you?
I think I will try another browser, but the browser settings seem correct.

---

### Post by NewbieNik on 2005-10-30
[QUOTE=Jon_cooper]I have a similar problem. I have installed Ubuntu on 2 machines 1 32-bit Hoary and 1 64 bit Breezy, both give me the same problem with Firefox. 
The problem seems really strange as I can click on links and reach pages. I can get here as the start page contains a link to [www.ubuntu.com](www.ubuntu.com) and then I can follow other links. 
However if I try to type in an address such as [www.google.com](www.google.com) in the address bar, no go it just times out. 
If I type in the ip address as a number it will take me to the address. 
Does the same work for you?
I think I will try another browser, but the browser settings seem correct.[/QUOTE]


If you can reach the site by the ip address then it is a DNS resolve error. Is your network set to DHCP or have you specified address's?
Check the DNS. Is it built in to the router? If so, can you flush the DNS cache?

---

### Post by Jon_cooper on 2005-10-30
Found the answer by reading lots of other posts:razz: 
It is an IPV6 problem, seems to have something to do with the router.
Turned off ipv6 and everything works fine.
Instructions at [http://www.ubuntuforums.org/showthread.php?t=3713](http://www.ubuntuforums.org/showthread.php?t=3713)
:p

---

### Post by corstar on 2005-10-30
The process for turning off IPV6 is .....

type "about:config" in the address bar
then type "network.dns" and you will see the options shrink to only a few.
double click on the "ipv6 enable" and this will disable the function.

This has fixed firefox every single time for me, I hope it does for you too.

---

