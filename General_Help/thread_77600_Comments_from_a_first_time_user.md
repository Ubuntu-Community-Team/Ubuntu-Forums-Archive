---
title: "Comments from a first time user"
date: 2005-10-17
forum: General Help
---

### Post by jorgencederberg on 2005-10-17
Hi everybody,

i just wanted to share my experiences from installing Kubuntu 5.10 this weekend. I have very limited knowlegde of using linux (or should that be Linux). But, I have the desire to learn it! My main hope was that it was almost as easy as Windows XP to setup, but I know that is a lot to hope for ;). I should mention, that I'm not a PC-newbie and have a degree in engineering, although never worked very much on any linux-system.

To summon up the main problems for a newbie like me:
[LIST]
[*]The fonts look really awful. How do I install new fonts?
[*]Where should I install things?
[*]Lacking support for easy wifi setup.
[*]How do I setup WPA-PSK? Can someone provide links to documentation on how to do that.
[*]I need more documentation, than what is installed by default.
[/LIST]

Great things:
[LIST]
[*]Very nice ripper and audio player.
[*]Easy to install Firefox and add it to the menus.
[*]Seems a tad faster to run than the previous Windows XP installation.
[/LIST]

Following, is a somewhat long description of what I did. The target machine was a rather old Compaq laptop, Presario 1450, equipped with 128 MB of ram and a D-link DWL-G650 wireless network adapter.

I popped in the CD and booted. Selecting english language and a danish keyboard layout. Apperently that was a mistake. The keys seemed be reordered randomly, but I did manage to type in an username and a (simple) password.

It could not recognize my wireless network adapter and it thought that I wanted to use Firewire as network connection(?). 

After the installation, it started up nicely and prompted me for the password. But with no internet its not much fun, so I thought lets try to figure out how to setup the network adapter.

I tried the network settings, connection settings, Kwifimanager, reading the man-pages for 'interfaces' all with out luck... The documentation is really not very good for a complete linux beginner.

Ofcourse I have another PC (who doesn't have multiple PC's), running Windows XP. So I spent 3-4 hours searching for info on how to setup the /etc/network/interfaces file. Finally I did manage to set it up, but only without encryption! I haven't had time to find out how to enable WPA-PSK.

After that, I downloaded and installed the tar.gz version of Firefox and ended up installing it in /home/user/programs/firefox. Where should I have installed it if it should have been more linux-like?

The browser just worked out of the box, and installing flash was a piece of cake! But, the fonts are almost unreadable. Blurry and definitely unsharp. I tried changing to Bitstream Vera, but that didn't help. I could not install msstcorefonts, I tried using ```
sudo apt-get install msttcorefonts
```, but it failed. It seems I have the same problem as in this [thread]("http://ubuntuforums.org/showthread.php?t=1261&page=3").

A great thing was AmaroK and the audio ripper. It worked nicely, looks great and is easy to use!

Alas I did manage to get the system to crash. This happend while ripping audio, playing audio and starting the browser at the same time. But, this could also be my laptop, as it has been tweaked with a new processor...


Regards
Jorgen Cederberg
-- Still very linux-newbie...

---

### Post by Pablo_Escobar on 2005-10-17
About msstcorefonts - did You add multiverse in /etc/apt/sources.list ?

They're right there :)

---

### Post by hollows2 on 2005-10-17
Try this rather good FAQ ( its for the previous release of Kubuntu but most still applies) - [http://kudos.berlios.de/kf/kf.html](http://kudos.berlios.de/kf/kf.html). 

In addition the Ubuntu unofficial FAQ has a lot of useful info as well - [http://ubuntuguide.org/](http://ubuntuguide.org/)

hope this helps

Steve

P.S - Having trouble with installing a printer try here - [http://www.linuxprinting.org/](http://www.linuxprinting.org/)

---

### Post by jorgencederberg on 2005-10-17
[QUOTE=Pablo_Escobar]About msstcorefonts - did You add multiverse in /etc/apt/sources.list ?

They're right there :)[/QUOTE]

Thank you. I managed to figure it out. The /etc/apt/sources.list can actuallt be edited from "Adept Manager". From the Adept menu select 'Manage Respositories" and then "Enable" the relevant lines. But ufortunately this isn't enough as the lines containing multiverse are wrong. So manually edited it via Kate.

A quircky thing in repository manager, is that you have to press the apply button, before the changes are activated, which is not very intuitively as the apply button is always active. I thought that clicking "Fetch updates" was enough.

One problem with adding multiverse as package repository is that my machine is very slow on filtering the package list....:???: 

Thanks again
Jorgen Cederberg
-- now with readable fonts... ;)

---

### Post by jorgencederberg on 2005-10-17
[QUOTE=hollows2]Try this rather good FAQ ( its for the previous release of Kubuntu but most still applies) - [http://kudos.berlios.de/kf/kf.html](http://kudos.berlios.de/kf/kf.html). 

In addition the Ubuntu unofficial FAQ has a lot of useful info as well - [http://ubuntuguide.org/](http://ubuntuguide.org/)

hope this helps

Steve

P.S - Having trouble with installing a printer try here - [http://www.linuxprinting.org/](http://www.linuxprinting.org/)[/QUOTE]

Hi Steve,

it sure does help. Thanks for the links.

Regards
Jorgen

---

### Post by jorgencederberg on 2005-10-20
Hi Jorgen

perhaps I'm just writing to myself. On the other hand, if people search, they may find this response which could be helpful to them.

I managed to get my wireless network working with encryption. Actually its more of a principle than a nessecity. Where I live now, I can only see one other (unprotected) network, and we don't have people passing by trying to connect to every wifi-network they see... 

Anyway, I got it running, and I'm happy to  be using Kubuntu, as the driver, [madwifi]("http://madwifi.sourceforge.net/dokuwiki/doku.php?id=start"), for my D-Link DWL-G650 was installed as I installed Kubuntu. 

I used wpa_supplicant for encryption and the only thing I could'nt get to work was DHCP! Turned out, that I forgot that I myself had turned of this option in the access point (DWL-2100) setting... :oops:. Ofcourse I then needed to setup a static IP-adresss, but that's a piece of cake now.

/etc/network/interfaces:
```

# The loopback network interface
auto lo
iface lo inet loopback

# Wireless network interface
auto ath0
iface ath0 inet static
	wireless_ssid cnet
	address 192.168.1.13
	netmask 255.255.255.0
	gateway 192.168.1.1
	pre-up /usr/sbin/wpa_supplicant -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf -Bw
	post-down killall -q wpa_supplicant

```

and 

/etc/wpa_supplicant.conf:
```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

network={
	ssid="cnet"
	proto=WPA
	key_mgmt=WPA-PSK
	pairwise=CCMP TKIP
	group=CCMP TKIP WEP104 WEP40
	#psk=some random numbers
}

```

Thats all. Pretty simple, when you know what to do.

Regards
Jorgen

---

