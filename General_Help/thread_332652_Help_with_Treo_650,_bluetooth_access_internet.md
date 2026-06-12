---
title: "Help with Treo 650, bluetooth access internet"
date: 2007-01-06
forum: General Help
---

### Post by Elijah on 2007-01-06
I have already have a fully syncing treo+ubuntu thanks to this link:
[http://www.newt.com/debian/treo650.html](http://www.newt.com/debian/treo650.html)

But now I crave to have a working reverse dun setup so I can use the internet connection from my desktop pc to my treo 650, there is a full guide here for gentoo: 
[http://gentoo-wiki.com/HOWTO_Palm_Bluetooth_Reverse_DUN](http://gentoo-wiki.com/HOWTO_Palm_Bluetooth_Reverse_DUN) 


Problem now for me is on the testing part... I simply could not ping 'google.com' or anything... I could however ping my own desktop and sometimes the dns server. Need help! ](*,)

---

### Post by pear on 2007-01-29
I have a similar problem. From my Treo I can ping my router and DNS servers but cannot ping any other external sites or my own desktop. When I try to ping the treo from the server/desktop it knows it is there.

---

### Post by Elijah on 2007-02-10
anyone? I was thinking maybe to share the eth0 connection to my ppp connected treo... ?

---

### Post by Elijah on 2007-03-09
a bit of progress! I managed to ping google, but open using blazer I get nothing but 'Sending...' message... :-(

---

### Post by MoebusNet on 2007-03-24
I just wanted everyone to know about your excellent How-To at [http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html](http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html)

Thank you for helping me to get my Treo 650 to synch via Jpilot!

---

### Post by ederic on 2007-11-11
Hmm, I should try these links. I have been looking forward to browsing the Web on my Treo 650 while lying down on the bed. :p

---

### Post by zybernav on 2008-06-28
Referred to the page

[https://help.ubuntu.com/community/PalmBluetoothHowto](https://help.ubuntu.com/community/PalmBluetoothHowto)

I tried to setup the internet sharing using bluetooth to my laptop. The pitfall I found was:

1. I'm using wireless lan to connect my laptop to internet so I have to change the network card name in this command

sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

(mine is wlan0 instead of eth0)

after changing this everything worked.

2. another pitfall that I found is DNS server in the file /etc/ppp/peers/palm

If you are not sure which address gonna work; you can try using open dns address
208.67.222.222
or
208.67.222.220

Good luck!

---

