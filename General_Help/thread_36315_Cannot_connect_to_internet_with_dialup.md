---
title: "Cannot connect to internet with dialup"
date: 2005-05-22
forum: General Help
---

### Post by klclsc on 2005-05-22
Using live CD I am able to setup modem and dial out, connection is completed, but browser will not open any web pages. I seems like the browser does not see the dialup connection. My ISP uses dynamic DNS but I don't see any to make that choice in Ubuntu - any ideas?

---

### Post by britbrian on 2005-05-23
klclsc

You can open a terminal, do 'sudo pppconfig' to set up /etc/ppp/peers/provider as explained step by step in this wiki:- [http://www.ubuntulinux.org/wiki/DialupModemHowto](http://www.ubuntulinux.org/wiki/DialupModemHowto).
kppp or the Gnome phone icon should activate/deactivate ppp  as before.
My external modem only connected at 1/4 speed until I did pppconfig.

I also had to edit the file /etc/ppp/peers/kppp-options and change 'auth' to 'noauth'

Further help at    [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)  and if your modem is a winmodem there are many posts here:  [http://www.ubuntuforums.org/search.php?searchid=797745](http://www.ubuntuforums.org/search.php?searchid=797745)

good luck

---

