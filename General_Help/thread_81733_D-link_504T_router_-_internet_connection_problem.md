---
title: "D-link 504T router - internet connection problem"
date: 2005-10-25
forum: General Help
---

### Post by andreakrap on 2005-10-25
hi!

I'm 100% newbie so i ask you to forgive me if my question is "stupid". 

I've just installed Ubuntu 5.10 on a laptop, it works fine and it's perfect but i'm not able to connect on internet with my D-link 504T router (which, instead, works fine with my iMac).

I've activated the Ethernet on Eth0.

I've gone on 192.168.1.1 (the ip address of the router) and i can load and manage everything (so i guess the card works fine....)

I've selected DHCP connection but it doesn't work (firefox doesn't load anything but neither give me a timeout message).

Do you have any suggestions? please help :( I need to install apache and php on the laptop but without the connection i'm lost :(

---

### Post by urusaiyatsu on 2005-10-25
I have a G604T and had similar problems after upgrading to 5.10. 

I resovled them by replacing the DNS address in either the Networking window or the resolv.conf file with my ISPs DNS address, replacing the router gateway address (10.1.1.1). Even though the ISP address was in the router there were problems.

I found I had this problem after updating to the latest firmware. Give it a try and if it works, great.

---

### Post by RAOF on 2005-10-25
This is almost certainly an IPv6 issue - apparently the D-link routers don't handle it, and it's enabled in Breezy by default.  You should be able to disable ipv6 by editing the /etc/modprobe.d/aliases and replacing "ipv6" with "off".  Run "sudo gedit /etc/modprobe.d/aliases" from a terminal to edit this file.

These instructions came from [here.]("http://www.ubuntuforums.org/showpost.php?p=422592&postcount=9")

---

### Post by andreakrap on 2005-10-25
i'll try tonight and make you know... thanks so much for the support :D :D :D

---

### Post by andreakrap on 2005-10-25
Great! i've followed the suggestion of RAOF.

RAOF you rule! :) just a little edit of the file you've told me and finally i can surf on internet through my new linuxbox.

Thanks so much!

---

