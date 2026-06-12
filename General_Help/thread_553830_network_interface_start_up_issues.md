---
title: "network interface start up issues"
date: 2007-09-18
forum: General Help
---

### Post by john6six on 2007-09-18
I have installed Feisty 64 bit on my Dell 1521. With the help of this forum and the kind people here, I have my system up and running perfectly for the most part. I have one small issue that I have not been able to work out. When I log in, the laptop tries to connect to the last network interface it was connected to. If this connection is not available, the system hangs for three minutes or so before I can do anything. 

I have tried to change my etc/network/interfaces, by first placing a # in front of the entry that read - auto wlan0 and auto eth0. This worked once, but after connecting to my wireless connection at home, it just added another auto wlan0 entry.

I have also placed the lines:

ifconfig wlan0 down
ifconfig eth0 down

in a startup script. Is there another way to keep my laptop from trying to establish a network connection at start up? Between home, work and the train, I am changing the way I connect constantly and would love the option to choose which connection after the system starts up.

Thanks in advance.

---

### Post by mojoman on 2007-09-18
Just a thought but why don't you try to place those lines in a log out script instead? Could keep it from adding auto on startup. It might be worth a try anyway...

---

### Post by tgalati4 on 2007-09-18
This is a weak area in Linux.  I have a powerbook with Tiger OS X and it handles multiple networks with ease.  I have a Dell Inspiron with Dapper and I have to jump through hoops when changing wireless networks.  I use a gnome application:  wifi radar.

I don't know if Gutsy has a better wireless detection framework.

---

### Post by john6six on 2007-09-18
I will try putting it in a logout script as suggested. Won't be able to try this until I get home tonight, but will follow with the results at that time.

---

### Post by tanchao on 2007-09-18
I had the same!  but I just restarted the computer everything is OK!!

---

### Post by tgalati4 on 2007-09-19
Sometimes the network cards remember settings that don't get cleared with a simple shutdown.  I sometimes have to remove my pcmcia card to reset the wireless to get it to work properly.  I don't know if this is a problem with the pcmcia support, the hardware bus, or the wireless card.  It's an old machine, so I don't sweat it too much.

When I go into standby (and leave overnight asleep) I will get reconnect about 50% of the time.  The times that it fails, I can usually use WiFi Radar and reconnect to my network.  I think I need some sleep statements somewhere in the resume script.

---

