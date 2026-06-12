---
title: "Can't Get Broadcom working"
date: 2006-09-05
forum: General Help
---

### Post by Winston_Smith on 2006-09-05
Ok i have a dell laptop with a broadcom wireless card. I've tryed just about everything i can find to get this working but still no luck. I can't plug my laptop into a hard line as all i have is dail-up, i'm trying to get it up and working so i can use the wireless at the library.
As of right now i'm on a fresh install all i have done is this.
```

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo ndiswrapper -i /home/winston/Desktop/bcmwl5.inf
sudo ndiswrapper -m
sed -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper/bcmwl5/*.conf
sudo modprobe ndiswrapper
```

I have both the bcmwl5.inf and .sys file on my desktop.

I installed ndiswrapper from the cd using package manager. I've follwed all the steps except the installing ndiswrapper via apt-get.

I still can't seem to get the wireless working, every thing else works great.

---

### Post by qamelian on 2006-09-05
Go to System > Administration > Networking and enter your password when prompted. Check on the Connections tab to see if your wireless connection is detected. 
Click on the Properties button and enter any necessary settings, then click the Activate button. You may also need to change the default gateway device in the drop-down at the bottom of the Network Settings dialog.

---

### Post by Winston_Smith on 2006-09-05
nope it's not showing up, all i have is the ethernet and modem.

---

### Post by qamelian on 2006-09-05
> **Winston_Smith said:**
> nope it's not showing up, all i have is the ethernet and modem.
When you run lsmod in a terminal, does it show ndiswrapper as loaded?

---

### Post by Winston_Smith on 2006-09-05
Yep it shows ndiswrapper 177364    0

---

### Post by qamelian on 2006-09-05
> **Winston_Smith said:**
> Yep it shows ndiswrapper 177364    0
Just curious: which Broadcom nic is it? I had mix results using nidiwrapper with the Broadcom 4306 in my Compaq laptop, so I used bcm-fwcutter instead to extract the necessary firmware from the driver. This resulted in a very stable wireless connection for me.

---

### Post by Winston_Smith on 2006-09-05
i have a dell on the back it says 
bcm94309mp

---

### Post by jISh on 2006-09-05
Forgot to alias it.
alias wlan0 ndiswrapper

Add that line to /etc/modprobe.d/ndiswrapper

---

### Post by Winston_Smith on 2006-09-05
Nope it's in the file

---

### Post by qamelian on 2006-09-05
> **Winston_Smith said:**
> i have a dell on the back it says 
bcm94309mp
It's from the same family as mine. I suspected as much when I saw the INF file. 

You may want try the firmware solution using bcm-fwcutter. You can find it at:
[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

---

### Post by jISh on 2006-09-05
Don't forget you have to reboot after doing that.
There's really no reason it shouldn't work, a reboot usually solves the problem.

The network settings manager is garbage IMO, it's better to edit the /etc/network/interfaces file and configure your network from there.

Use mine as a template (I just replaced my IP number with x's):

iface wlan0 inet static
address x.x.x.x
netmask 255.255.255.0
gateway 192.168.0.1
wireless_essid nameofyournetworkhere # ask your library for SSID (network name)
wireless_mode managed
wireless_channel 11 # probably is 11, ask your library

auto wlan0

---

### Post by Andy on 2008-02-28
G'day,  I tried this and similar tutorials but instead of curring my firmware.. I score this ugly message:

```
Sorry, the input file is either wrong or not supported by bcm43xx-fwcutter.
This file has an unknown MD5sum efcde2fb35a3abd64373ba2c854e34d4.
```

Mine is a 4309MP also

---

