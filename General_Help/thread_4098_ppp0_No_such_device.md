---
title: "ppp0: No such device"
date: 2004-11-11
forum: General Help
---

### Post by united on 2004-11-11
notebook - ubuntu 10.4

Normally I use a wireless for internet but this week I ended up at a motel without wireless and had to use the good old modem. I have the modem setup and it will dial the ISP. When the ISP server answers I get the following:

Coundn't find interface ppp0: No such device

I did the modem setup using the network-admin and do have a check in the box that tells it to - 

Activate when the computer starts

I reboot and still get the same results. Can someone help me resolve this issue in as much I do need to connect via the modem every so often.

thanks John

---

### Post by ashley_v on 2004-11-11
do:

'ifconfig -a' from a terminal and see what it displays

If it's not listed than try and bring it up:

'ifconfig ppp0 up' 

?

---

### Post by united on 2004-11-12
When I

ifconfig -a it is not listed
and
ifconfig ppp0 up
returns this
ppp0: ERROR while getting interface flags: No such device

ideas how to resolve this

---

### Post by mr_ed on 2004-11-12
I assume it's actually dialing?

Did you see here?
[http://ubuntuforums.org/showthread.php?t=3223&highlight=modem](http://ubuntuforums.org/showthread.php?t=3223&highlight=modem)

Specifically
[QUOTE=azz]
sudo pppconfig
make sure that you enter all the information and save your setup.

sudo pon provider
(I keep the default connection name)
[/QUOTE]

---

