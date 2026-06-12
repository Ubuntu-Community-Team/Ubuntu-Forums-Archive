---
title: "Didn't autoconfig networking on install, how to now?"
date: 2005-10-23
forum: General Help
---

### Post by helwitch on 2005-10-23
When I installed kubuntu 5.10, I didn't have a working net connection, so I skipped the network configuration step of the install. I now have a working net connection, how do I run the networking wizard that typically runs during setup? I'm guessing sudo dpkg-reconfigure something. But what? Thanks!

---

### Post by rsankuratri on 2005-10-23
Go to the menu..
                             System -> Administration and select Networking.  

You should see your network card there (typically eth0 Ethernet connection).  Activate that and then click on the properties and select either dhcp (dynamic IP) or if you have static IP enter the IP information.
Once this is done select the eth0 as the Default gateway device.  

Thats it you should be on your way then...:)

---

### Post by helwitch on 2005-10-23
[QUOTE=rsankuratri]Go to the menu..
                             System -> Administration and select Networking. [/QUOTE]
Except I don't seebadmin in system. I see info center, but can't find a way to activate my network card from there. I'm using kubutu 5.10 if I didn't already mention that.
Oh, I see, system settings-networking. thanks!

---

