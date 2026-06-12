---
title: "Sophos site to site VPN, only partial communication using Ubuntu"
date: 2016-08-15
forum: General Help
---

### Post by espenu on 2016-08-15
I've set up a site to site VPN linking my network and a friends network. We both use Sophos UTM Home, and the VPN uses virtual IP's to communicate.
Example:
My internal IP is 192.168.2.21
My friends IP on his network is 192.168.1.31

If I want to access his PC I would access 192.168.10.31


However, when using Ubuntu (16.04 x64 Desktop) I can't communicate through the VPN. If I use Windows 10 (dual boot from the same PC) then everything works fine.
Using Ubuntu, I can ping PC's on the other network, but that's about as far as it goes.

If I for example try to ssh to his PC, then I can see from packet logging that the PC's start communicating, but around the point where the clients lists different certificates (at least that's what it looks like it's doing) communication stops, and the client never gets any more reply's.
If he has a web page that requires authentication, I can enter his address in my web browser (tested Chrome and Firefox), and I get a request for username and password. As soon as I have entered my credentials and clicked OK, communication stops and the page does not load any further.

In both cases we have tested forwarding ports directly to his PC from WAN. Then using the WAN address, I can connect to his PC with both ssh and web without any issues.

Again, this all works from Windows, so there is something in Ubuntu killing the communication. What on earth could be wrong?

---

### Post by #&amp;thj^% on 2016-08-15
Do not know if you have seen this yet but have a look here: [https://community.sophos.com/kb/en-US/115306](https://community.sophos.com/kb/en-US/115306)
And More Info Here: [https://community.sophos.com/kb/en-US/122771](https://community.sophos.com/kb/en-US/122771)
I use a different paid service so not much more i can add to this.
Good luck and Regards

---

### Post by espenu on 2016-08-15
Well, those sites only describe how to configure site to site VPN in Sophos. My VPN is working (it works fine in Windows), the issue seems to be in Ubuntu for some reason.

---

### Post by SeijiSensei on 2016-08-16
Maybe you should look into OpenVPN.  Here's how to set up a point-to-point link between two networks: [http://openvpn.net/static.html](http://openvpn.net/static.html).

---

