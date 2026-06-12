---
title: "lan cable internet"
date: 2008-02-22
forum: General Help
---

### Post by dragonwings on 2008-02-22
am using a lan cable internet which i can just plug into my windows xp laptop and it willlgo.

but on my macbook which has ubuntu 7.04 o.s only!! i plug it in and nothing happens, the wirless connection is working fine and my be blocking my lan????? 

anyway i need to get lan conection to work help s.o.s

---

### Post by dieselpower on 2008-02-22
open /etc/network/interfaces and make sure it only has these two lines.

```

auto lo
iface lo inet loopback

```

Log out, and back in, plug in the cable and see if it works. I'm not familiar with the gnome network applet so someone else will have to help you further.

If all else fails you can always "ifconfig eth0 192.168.x.x up" from the term. It won't hurt anything. Just replace x.x with the desired address.

---

### Post by dragonwings on 2008-02-23
no that did not help ,iv reinstalled ubuntu 7.04 to make a resh start any other ideas

---

### Post by Pelham123 on 2008-02-23
Do you use the firestarter firewall? You have to manually swap between wireless and wired interfaces as firestarter does not switch for you - therefore blocking your wired connection.

---

### Post by dragonwings on 2008-02-23
no its a fresh install ubuntu 7.04 thought id go back to the drawing board in case i done somthing i should'nt.

it seems i hav     eth0
                           eth0 :avah

i also have ath0
                  ath0avah
                  lo
                  wifi0

this is all new to me as i  was using dail up until now

---

### Post by Iowan on 2008-02-23
Under System>Administration>Network, click on "Wired connection", then click "Properties". If connection is set for "Local Zeroconf network", change it to "Automatic configuration (DHCP)". Then you'll either need to restart (reboot) machine or restart networking.
If you use a static address, the other option (Static IP address) would be used - and would need to be set up.

---

### Post by dragonwings on 2008-02-23
I have tried that and lots of other combos i even got it pop up and tell me im conected to wired network ,but still no internet of any kind

---

### Post by dragonwings on 2008-02-23
Thanks for all the help guys ,but i have solved the problem ,it was a loose fitting lan socket on my macbook the weird thing is when i plugged it in it still recognised the lan cable .only when i plugged it in today by chance i noticed the sloopyness  in the connection so i put a book under the lan cable to pack it up and bingo im surfing.

---

