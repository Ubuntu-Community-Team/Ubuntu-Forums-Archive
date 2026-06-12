---
title: "Where to find network adapter config files"
date: 2008-04-26
forum: General Help
---

### Post by sofasurfer on 2008-04-26
I want to look at the files to see what is happening in there in regards to my network adapter. Since I have not received any help with my problem I will take it step by step and try to learn why bad things happen and what to do about it.

I have a Linksys WUSB54GC which installs and connects flawlessly after a tiny bit of configuration at system>administration>network.
The problem is that every time I want to connect I must first go to the network config window and retype my encryption key.

It seems to me that this key, when typed, must be entered into a file. And there is not doubt a reason for this key to be corrupted or deleted.

So, where is this key kept after I type it?

Thanks.

---

### Post by alan34 on 2008-04-26
The key is in /etc/network and is call interfaces

to look enter in a terminal (Applications -Accessories - Terminal)

more /etc/network/interfaces

to backup

sudo cp /etc/network/interfaces /etc/network/interfaces.backup

to edit

gksudo gedit /etc/network/intefaces

I think you are looking for

wireless-key XXXXXXXXXXX

---

### Post by sofasurfer on 2008-04-26
Here is my /etc/network/interfaces file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wpa-psk 1650b64a63636d4459883f10c6587a1a74c6fcb561a5674a63cd86d573a91162
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid belkin54g

auto wlan0


When I go to system>administration>network and enter my network password or encryption key, which is the wap-psk, I enter xxxxxxxx (8 x's). 1650b64a63636d4459883f10c6587a1a74c6fcb561a5674a63cd86d573a91162, mentioned above is apparently what the computer converts it to in hexadecimal or whatever its called.

Does any of this information help us to figure out why I need to enter my key every time I want to connect.

When I first set up my Belkin router I think I had the choice of entering a alpha-numeric password (which is then converted to hex) or entering an actual hex code. I chose to enter the password. Could it have made a differance if I entered the hex code instead?

As seem above, my key is still in the file. So why is the computer no seeing this when I want to connect?

I'm reading the manual tonight to see if there is a configuration setting that I am doing wrong.

It seems that there was a "broadcast" setting somewhere. Could this be the problem.
Thanks for any help.

---

### Post by alan34 on 2008-04-27
I do not use WPA encryption ( I use WEP ) but found this HOWTO that should help you
its about a third of the way down. Gives you sample interface files just backup your
original file and try some. Good Luck

[http://ubuntuforums.org/showthread.php?t=202834&highlight=enter+wpa](http://ubuntuforums.org/showthread.php?t=202834&highlight=enter+wpa)

---

### Post by sofasurfer on 2008-04-27
This thread solve by thread:
[http://ubuntuforums.org/showthread.php?t=731361](http://ubuntuforums.org/showthread.php?t=731361)

---

