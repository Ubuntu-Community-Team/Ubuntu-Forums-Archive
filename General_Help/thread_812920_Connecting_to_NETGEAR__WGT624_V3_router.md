---
title: "Connecting to NETGEAR  WGT624 V3 router"
date: 2008-05-30
forum: General Help
---

### Post by Liopleurodon on 2008-05-30
Hello,
two days ago, I downloaded the lastest version of Ubuntu. I have a NETGEAR  WGT624 V3 router, and when I try to connect to it, a popup shows up where I have to typ my router password in, I typ the password and after half a minute, the popup shows again. So I cannot connect to the internet. I'm just started using Ubuntu so I don't know anything how to post logs,...

Already thanks for help.

---

### Post by thefunnyman on 2008-05-30
> **Liopleurodon said:**
> Hello,
two days ago, I downloaded the lastest version of Ubuntu. I have a NETGEAR  WGT624 V3 router, and when I try to connect to it, a popup shows up where I have to typ my router password in, I typ the password and after half a minute, the popup shows again. So I cannot connect to the internet. I'm just started using Ubuntu so I don't know anything how to post logs,...

Already thanks for help.


So, are you using wireless or wired interface? 

if wireless...

Are you trying to connect to local network and browse the internet, or are you trying to physically log into the router?

Also, what type of encryption are you using?

thanks

---

### Post by Liopleurodon on 2008-05-30
> **thefunnyman said:**
> So, are you using wireless or wired interface? 

if wireless...

Are you trying to connect to local network and browse the internet, or are you trying to physically log into the router?

Also, what type of encryption are you using?

thanks

Hello! Thanks for fast response. My router is wireless and I want to browse the internet. I have a WPA-Personal key. I've been thinking of my problem and now I thought that my password is not fully alpha-numeric. (It contains things like "€".) Is it possible that this is the problem?

---

### Post by thefunnyman on 2008-05-30
I have a linksys wmp54g wireless card in my machine at home and I had similar problems connecting to wpa router using ubuntu 8.04.  I eventually had to downgrade to ubuntu 7.10 in order to get it all to work, and even then it was hoaky and weird the way I had to do it.  I'll be honest with you though, this is probably outside the realm of my knowledge currently.  I can offer a couple of links that helped me get my wireless connection up and running.

[http://www.vanutsteen.nl/2008/05/05/autoconnecting-wlan-on-startup-without-gnome-network/](http://www.vanutsteen.nl/2008/05/05/autoconnecting-wlan-on-startup-without-gnome-network/)
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

hope some of this helps.  I've discovered that getting wireless to work with ubuntu, especially 8.04, is hit or miss at best.  I would definitely browse the networking and wireless section of this forum for more help.

---

### Post by ibuclaw on 2008-05-30
Try connecting to it by hard wire.

Then type in:
```
192.168.1.1
```
Into the firefox browser.

Should come up with a login and password box (If you haven't already set it, login account is **admin** and the password access is **password**).

Then you'll have a small javascript browser which you can alter the settings of your Netgear router.
Check for anything that looks like it will block you (ie: Access Control is turned on).

[EDIT]
Also, if you are a Kubuntu user. I think the wireless manager has a checkbox that says "ASCII". Make sure it is checked before you press "OK".

Regards
Iain

---

### Post by Liopleurodon on 2008-05-30
> **thefunnyman said:**
> I have a linksys wmp54g wireless card in my machine at home and I had similar problems connecting to wpa router using ubuntu 8.04.  I eventually had to downgrade to ubuntu 7.10 in order to get it all to work, and even then it was hoaky and weird the way I had to do it.  I'll be honest with you though, this is probably outside the realm of my knowledge currently.  I can offer a couple of links that helped me get my wireless connection up and running.

[http://www.vanutsteen.nl/2008/05/05/autoconnecting-wlan-on-startup-without-gnome-network/](http://www.vanutsteen.nl/2008/05/05/autoconnecting-wlan-on-startup-without-gnome-network/)
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

hope some of this helps.  I've discovered that getting wireless to work with ubuntu, especially 8.04, is hit or miss at best.  I would definitely browse the networking and wireless section of this forum for more help.

Ok, I'll try it. :)

---

