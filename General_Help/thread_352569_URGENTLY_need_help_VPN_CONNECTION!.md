---
title: "URGENTLY need help VPN CONNECTION!"
date: 2007-02-03
forum: General Help
---

### Post by jbtito03 on 2007-02-03
Okey...

I dont have a lot of time. In 2 hours i have to connect to my server at work thru VPN. I did not use VPN before and as i have no time to fix it by myself i am asking you for help. How to connect to a VPN account which is on a windows server with no special security. My friend connects thru win XP just by adding a connection with user name and password. 

So how to use openVPN when i have been given an adress like vpn.adress.com with a user and pass?!?! 

Pleeeease help...



Cheers


JB

---

### Post by jbtito03 on 2007-02-03
Okey... it is not openvpn BUT pptp?!?!

Anyone?

JB

---

### Post by juicemansam on 2007-02-03
I haven't used VPN either, except for one test attempt, but you can have a look at [PPTP Client](http://pptpclient.sourceforge.net/). Hopefully it's what you need and that it's easy to setup. Good luck!

Edit: apt-get install pptp-linux should get what you need.

---

### Post by kebes on 2007-02-03
This thread describes setting up pptp and the graphical utility "pptpconfig". Follow the instructions and it should be work pretty easily:
[http://www.ubuntuforums.org/showthread.php?t=91249](http://www.ubuntuforums.org/showthread.php?t=91249)

The more detailed version of the instructions is here:
[http://pptpclient.sourceforge.net/howto-debian.phtml#install](http://pptpclient.sourceforge.net/howto-debian.phtml#install)


Hope that helps.

---

### Post by banditti on 2007-02-06
Not my post, but thanks.  This helped me out.

---

### Post by jbtito03 on 2007-02-10
Wel... 

Again me..

Last time it did not work for me..

I got a connection (IP and everything) but i cannot ping out..

Anyone any ide... i got thru the docu and cant find any solution.

Cheers

JB

---

### Post by speedothebrief on 2007-02-12
you may want to check and see if there are any conflicts between subnet addresses. if you are on the same subnet, certain configurations may cause ip resolution problems.

---

### Post by jbtito03 on 2007-02-12
okey... 
one subnet mask is 255.255.255.0 and one is 255.255.255.255

i think that this is okey?!?! or?!?!

Anyway... i got tranfre 8 in and 8 out and than nothing ...  the only thing i get is something with cannot resolve ARG or something...

Cheers

JB

---

### Post by speedothebrief on 2007-02-12
You're looking at the subnet mask, what you really want to check is the actual subnet (which is the bitwise AND of the subnet mask and the subnet). In general this should work for determining your subnet:

lets say, for instance, that you're local IP address for a computer on your home network is:
192.168.0.2

youre local subnet is 192.168.0

so if you get an address of 192.168.0.2 at home and someone has the local address of 192.168.0.2 at work... potentially, there could be a problem.

If this is the case, just HTTP into your router and tell it to assign addresses in a different subnet, i.e. 192.168.1.0-192.168.1.255

This also might not do anything for you at all, so if you ARE on the same subnet, don't get too excited about changing your subnet. I know that my VPN's (which i still haven't successfully connected to using my kubuntu 6.06 AMD64 machine) DNS server has lots of trouble with conflicting subnets from WAN clients and LAN clients.

hope this helps somebody...

---

