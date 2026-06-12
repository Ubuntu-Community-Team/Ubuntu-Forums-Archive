---
title: "Wireless &amp; battery problem"
date: 2005-10-27
forum: General Help
---

### Post by Gambit on 2005-10-27
Hi,

I tried to install kubuntu 5.10 on my laptop, but I have two problems :

- my wireless card (DLink DWL G650 , atheros) is  recognised, but can't stay enabled, if I clic "enable", its stay enabled 2s, and automaticaly disable...
but no problem with my ethernet card

- the daemon for monitoring battery don't work, when I go into options > battery, I get a message "acpi is partially installed, please enable batterry" ??
I tried uninstalling and reinstalling acpi, no changes...



I tried ubuntu 5.10, and I don't have these problems, wireless works and batterry daemon too... but I don't like gnome...


any idea ? thanks

---

### Post by lordjoe on 2005-10-27
I just installed kubuntu 5.10 a few hours ago. I had the same problem with the wireless network configuration - it placed all stars for the WEP key in /etc/network/interfaces. I just edited the file by hand and the KDE network configuration can enable it now. Perhaps someone who knows more about KDE can shed some light on this.

I don't think I can help you with your ACPI issues, sorry.

---

### Post by Gambit on 2005-10-28
Hi,

thanks for your participation, but I'm a real newie on linux..

I found the file, but I don't unnderstand what I have to modify in this file ...


thanks

---

### Post by daller on 2005-10-28
[QUOTE=Gambit]Hi,

thanks for your participation, but I'm a real newie on linux..

I found the file, but I don't unnderstand what I have to modify in this file ...


thanks[/QUOTE]

Go to a konsole and write:

sudo vi /etc/network/interfaces (and press enter)

Press "i" (This turns on the --INSERT-- mode - pretty selfexplanatory)

My wireless part looks like this:

(If the interface is not eth1, please replace with whatever it's named!)

iface eth1 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid any
        wireless-key1 XXXXXXXXXXXXXXXXXXXXXX

You can replace "any" with the network-name (or leave it as "any")

Then type in your WEP-key (if you use WEP)

Now press "esc" (escape) and ":wq" (To save and exit)

Now try to up the card:

sudo ifup eth1

If it doesn't work, please post the content of the file!

---

### Post by Gambit on 2005-10-28
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0
	map ath0
	map wlan0


# The primary network interface

iface eth0 inet static
	address 192.168.0.98
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.0.1


iface ath0 inet dhcp
	# dns-* options are implemented by the resolvconf package, if installed
	wireless-mode managed
	wireless-essid Appart

iface wlan0 inet dhcp
	address 192.168.0.99
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.0.1
	wireless-mode managed
	wireless-essid Appart


```


thanks for spending time for me.

I've tried with my 2 wifi cards, and it seems to work with the "ath0" (dlink G650)
but in the control panel I can't define route so I had to use *route add default gw*
is there a way to store it in this file ?

when using  "wireless-key1 xxxx" is it for Ascii or hexa ?


thanks

---

### Post by lordjoe on 2005-10-28
You can add a gateway with the line "gateway x.x.x.x" for any of your interfaces (in case you were wondering it's documented in the 'interfaces' man page).

Guess the network control isn't very useful, eh?

The wireless key is in hex by default. If you prepend the key with "s:" then it is ascii (ie "wireless-key s:asciikey" versus "wireless-key hexkey"). This is in the iwconfig man page if you were wondering. Also, you can see the details of debian's wireless configuration in /usr/share/doc/wireless-tools/README.Debian.

---

