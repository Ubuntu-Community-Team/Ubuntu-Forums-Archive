---
title: "wireless f5d7010 works but with annoying issue"
date: 2006-09-27
forum: General Help
---

### Post by neoroses on 2006-09-27
rite lads heres the deal i have sucsessfuly installed the wireless network card belkin f5d7010 on my mums laptop (the last computer in my house to have ubuntu on it - my house is now 100% linux and we have 6 computers!! lol) anyway,..yea, so it works but everytime i turn the laptop on i have to go to  system --> administration --> networking and set it to the default gateway device everytime and deactivate it then reactivate it other wise it wont work!! this field is always blank when i got to set it even though i set it before the computer was turned off? whaaaat is goin on,,,thanks guys :):D

---

### Post by wieman01 on 2006-09-27
Let's make this thing stick. Post contents of:
> /etc/network/interfaces
...and we'll see.

---

### Post by neoroses on 2006-09-28
looks how it shud to me...

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0
        map wlan0

# The primary network interface
iface wlan0 inet dhcp
wireless-essid belkin54g

auto wlan0



thanks :)

---

### Post by wieman01 on 2006-09-28
Mmm... one more question. Are you using DHCP or not? Why would you want to change your gateway if DHCP is enabled? Just a silly thought, I'll go ahead in a minute.

---

### Post by neoroses on 2006-09-28
i dont have to change the gateway as in the ip to my router i just mean i have to set it as the deafault network adapter everytime :( 

thanks for quick reply

++ have tried with static and dhcp

---

### Post by wieman01 on 2006-09-28
Ok, now edit the "interfaces" file and save please. Should look like this:
> auto lo
iface lo inet loopback

#mapping hotplug
#script grep
#map eth0
#map wlan0

auto wlan0
iface wlan0 inet dhcp
wireless-essid belkin54g
Then restart the computer. Does that help?

---

### Post by wieman01 on 2006-09-28
If that does not work, then I may know what the problem is... But I know a solution as well.

---

### Post by neoroses on 2006-09-28
r33t, it didnt work but the card was being more active, by this i mean i was recieving more packets than before but i still had to deactivate then activeate it again... :S, i just deleted everything and pasted in what u put yea?

thanks duuuuuude

---

### Post by wieman01 on 2006-09-28
Ok, after **rebooting** do this and tell me if your card connects:
> sudo /etc/init.d/networking restart
If that works, I can help you.

---

### Post by neoroses on 2006-09-29
dude thanks for your help but i managed to sort it out,,just uninstalled the driver then installed it again and it worked fine :) thanks for everything dude been a great help

---

