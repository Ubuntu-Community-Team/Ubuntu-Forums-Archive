---
title: "Picking up Networks in your area"
date: 2006-11-12
forum: General Help
---

### Post by Heyholetsgogrant on 2006-11-12
Can ubuntu pick up wirless networks in your area automatically? if so how? is their a way to select them from a list?

thanks,

Grant

---

### Post by Ramses de Norre on 2006-11-12
```
sudo iwlist scan eth1
```
Is the way I always search for them, tells you immediately whether they are encrypted or not too.
I assume there will be a gui application for it too, networkmanager or something maybe?

---

### Post by Heyholetsgogrant on 2006-11-12
do you put this in the terminal?

-Grant

---

### Post by Ramses de Norre on 2006-11-12
Yes, and replace "eth1" by the name of your wireless device, I think eth1 is the most common but mine for example is ath0.
You can check this with **iwconfig**.

---

### Post by Heyholetsgogrant on 2006-11-12
darn I quess if your home network is encrypted and the one your switching to is not, you have to enter your passcodes again after you switch back to a encryped network?

-Grant

---

### Post by Ramses de Norre on 2006-11-12
Yes, but you can back up your old /etc/network/interfaces file, that's the file with all networking configs (except for dns).
So you could do ```
sudo cp -p /etc/network/interfaces /etc/network/interfaces.bak
```
then alter everything to connect to another network, and when you want to connect to yours again you do this:
```
sudo ifdown eth1
sudo cp -p /etc/network/interfaces.bak /etc/network/interfaces
sudo ifup eth1
```
replace eth1 again by the real name of the device.

---

### Post by strabes on 2006-11-12
network-manager-gnome is a good gnome wifi app. It lives in your notification area and scans automatically. It's a pretty easy gui.

```

sudo apt-get install network-manager-gnome
nm-applet &

```

---

### Post by plexi50 on 2006-11-12
Use WIFI Radar instead of Network Manager. It works more like the Windoze wifi apps, good scanning, lets you set profiles for each connection, storing the settings. I struggled with Network Manager for a while and it was too clunky, with the Keyring, etc.

---

### Post by Heyholetsgogrant on 2006-11-12
Ill be honest here, im new to ubuntu, what are the steps to get WiFi manager on your comp?

-Grant

---

### Post by Ramses de Norre on 2006-11-12
You mean wifi-radar?
```
sudo aptitude install wifi-radar
```
Or open synaptic, search for the package, select it and aply.

---

