---
title: "Wireless managers"
date: 2006-11-04
forum: General Help
---

### Post by unforeseen on 2006-11-04
Hey all... I've been reading a bunch of posts and noticed that there has been some issues with network-manager-gnome as well as a ton of issues with wireless cards.  My wireless connection (dlink wna-2330) seems to work fine without the use of any wireless manager but once it's installed, the connection drops ever few seconds.  I wanted to know what everyone uses to manage wireless connections. What about if you are constantly using different connections and not just one single connection? Are there any stable managers out there?

Which do you prefer? Network-manager-gnome , wifi-radar, iwconfig, any others?? Are there any that do not affect stablility??

---

### Post by Joe_CoT on 2006-11-04
Honestly, since gnome network manager stopped working correctly, i just use the /etc/network/interfaces file.

My interfaces file looks like this:

```

iface ra0 inet dhcp
#wireless-essid RH424jpt8
#wireless-essid njit
wireless-essid dd-wrt

auto ra0
```

When i switch to a different network, i uncomment the new one and comment the old, and then if up down the network. When i need to find a network, that's what "iwlist scan" is for. It's stable, and it's faster than any of the network managers.

---

### Post by unforeseen on 2006-11-04
So I'm guessing there is no GUI that actually works huh? Do any of these utilites actually work under edgy?

---

### Post by fragos on 2006-11-05
I had good luck with wifi-radar.

---

### Post by chriscando on 2006-11-05
I have also had good luck with wifi-radar. I like it better than gnome manager since it updates signal strength in realtime.

---

### Post by Cable on 2006-11-05
I use network-manager and have no problems with it at all.

---

### Post by unforeseen on 2006-11-05
So the people that report issues- is it the source/ version they are using or is it the wireless card?  For instances, I was installing if via synaptic but wonder if the version in automatix is any different?  I'm betting it's not but would like to know what hardware you guys used/ where you installed it from

Thanks

---

### Post by fragos on 2006-11-05
I always try Synaptic first accessing Ubuntu repositories.  I only look elsewhere if Ubuntu doesn't provide what I need.

---

### Post by chriscando on 2006-11-06
> **unforeseen said:**
> So the people that report issues- is it the source/ version they are using or is it the wireless card?

Its probably both, some cards have drivers that are better than others. Some cards work right off the bat with ubuntu. The ones that work best hopefully wont require you to install anything else via synapic or manual install. However this is not the case with Broadcom cards, where you will have to use something like ndiswrapper and a windows driver to get it to work (hopefully).

---

