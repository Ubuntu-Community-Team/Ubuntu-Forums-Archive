---
title: "How to get my Wi-Fi to connect automaticaly?"
date: 2006-07-05
forum: General Help
---

### Post by Jonathan Métillon on 2006-07-05
Hi,

I've got a working Wi-Fi device with a Broadcom chipset that uses the [bcm43xx driver.]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") =D> 

But when I start Ubuntu and open my GNOME session, I'm not connected to the Wi-Fi network. :confused: 

Here are the steps I have to do each time I start my computer :

[LIST=1]
[*]Open the Network Monitor
[*]Click "Configure" button
[*]Enter password for administrative tasks
[*]Network settings window opens. I click the "Wireless connection"
[*]I click the "Properties" button
[*]The Interface properties window opens.  The Network Monitor icons that showed no signal now shows full signal. I just click the "Ok" button
[*]I click the "Deactivate" button
[*]I click the "Activate" button
[*]I select "eth1" in the Default gateway device select box (was "eth0")
[*]I click the "Ok" button
[/LIST]

Yipee, I'm online ! :roll: 

I really need to do each of this steps or I won't be able to go online. #-o 

SO, the question is: how can I get Ubuntu to connect me automaticaly to the Wi-Fi network and Internet? :-k 

Thank you a lot for reading me ! :cool:

---

### Post by gotfoo on 2006-07-05
I this doesn't help but I too have found that in Ubuntu if boot into Gnome the wifi doesn to connect automaticly but if I boot into KDE it does.  :confused: 

A few times when I booted into Ubuntu and I went into re-start the wifi the whole system freezes and I have to kill the power.  Then when the system comes back up all of the network settings have been reset.

I also found that the wifi connects automaticly when booting into a pure Kubuntu or Xubuntu System but not in a pure Ubuntu system.  

This seems to a Gnome thing.

---

### Post by Cynical on 2006-07-05
Not true, my hawking usb wireless adapter connects automatically after a fresh dapper install.

---

### Post by Jonathan Métillon on 2006-07-05
[QUOTE=gotfoo]This seems to a Gnome thing.[/QUOTE]

Maybe it is and I'd love to know how to tell GNOME to do the thing.

But shouldn't it be managed in a lower level? Shouldn't it happen when system boots and says something like "Initializing networks"?

---

### Post by hizaguchi on 2006-07-05
Check and make sure that there is an entry for eth1 in your /etc/network/interfaces file.  If not, add one that says something like:
```
auto eth1
iface eth1 inet dhcp
wireless-mode managed
wireless-essid YOUR_NETWORK
wireless-key YOUR_WEP_KEY
```
Where YOUR_NETWORK can just be "any" if you want to connect to any hotspot, and you can leave off the wep key line if you don't use one.  Especially make sure the "auto eth1" line is somewhere in the file, because that is what causes the interface to be activated when you boot.

---

### Post by Jonathan Métillon on 2006-07-06
Thank you Hizaguchi !

I compared my */etc/network/interfaces* and that one, and the sole thing that was missing was:

```
wireless-mode managed
```

But I rebooted and it's not doing better.

In fact it's even worst because I change the essid to *any* and it did not want to connect at all. So I set back the actual SSID.

Any other clue?

---

### Post by hizaguchi on 2006-07-06
Heh, I dunno then.  The id not working on "any" makes some sense because there's one I connect to that requires you to put in the network name explicitly.  Not sure how that works.

The only other thing I can think of is that some wireless cards evidently need time to "associate" before they'll work with the network.  The network config files in Arch Linux had a field called "wifi-wait" where you could put in a short delay between bringing the interface up and having it request an IP address to make sure it was ready.  Not sure how to do that in Ubuntu though.

If you reboot the computer, and when it starts up the wirless isn't working, what happens if you do:
```
sudo ifdown eth1
sudo ifup eth1
```


The ifup line (I think) is what happens when you boot the computer.  It probably won't work.  But then also try:
```
sudo ifconfig eth1 down
sudo ifconfig eth1 up
```
wait a couple seconds and then
```
sudo dhclient eth1
```

If that works, then maybe you just need that delay and we can figure out how to put it in.  Either that or somebody that is way more knowledgable than me could shed some light on this? :)

---

### Post by Jonathan Métillon on 2006-07-11
Thank you for your time Hizaguchi!

Here's the result of the commands, after reboot, before manually connecting:

```

$ sudo ifdown eth1
(nothing happens)
$ sudo ifup eth1
(nothing happens after a long wait)

```

```

$ sudo ifconfig eth1 down
(nothing happens)
$ sudo ifconfig eth1 up
(nothing happens)

```

```

$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:01:e3:0c:ca:7b
Sending on   LPF/eth1/00:01:e3:0c:ca:7b
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
(then I interrupted the application)

```

So, none of these commands did something, I'm still not connected.

Also, please notice that I don't need to use DHCP as I use a static IP address.

How can I monitor what the system is really doing when I execute the ten steps enumerated in my first message?

---

### Post by Jonathan Métillon on 2006-07-13
I don't know if it's due to a recent update, but now I don't need to do the steps 5 & 6 to get connected!

Again, is there a way to monitor what's happening at the system level when I deal with the Network settings ?

---

### Post by Tamihania on 2006-07-13
You may find this thread useful:
[URL="http://ubuntuforums.org/showthread.php?p=1093961#post1093961"]
http://ubuntuforums.org/showthread.php?p=1093961#post1093961[/URL]

if you still want to connect wireless at the boot (try to adjust the advice given by mchs3d to your specs).

I am using the solution having different driver and different iwconfig output.

I hope this will be of a help.

Kind regards,

tami

PS. I explained more thorughly how I did it [here]("http://ubuntuforums.org/showthread.php?p=1219934#post1219934")

---

### Post by Jonathan Métillon on 2006-07-13
That works!

Thank you Tamihania!

---

