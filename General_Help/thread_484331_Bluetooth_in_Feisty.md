---
title: "Bluetooth in Feisty"
date: 2007-06-25
forum: General Help
---

### Post by atlanta800 on 2007-06-25
Alright, I've been searching  the forums and indeed the internet lately for information regarding setting up bluetooth on Linux/Ubuntu/Feisty and I've come across a few problems. I can usually get things working how I want but it usually requires going through many more steps than it should.

First off, my setup.

Fujitsu T4215 TabletPC
Ubuntu 7.04 Feisty amd64
Sony Ericsson w810i
Attached are my:
/etc/default/bluetooth
/etc/bluetooth/hcid.conf
/etc/bluetooth/rfcomm.conf
output of " sudo lsusb -s 4:2 -v" (my bluetooth device)

Under bluetooth preferences my device is "Visible and connectible to other devices" and never invisible as. The class of the device is "Laptop Computer"

The following bluetooth packages are installed:
bluez-cups
bluez-gnome
buez-pin
bluez-utils
gnome-bluetooth
gnome-vfs-obexftp
libbluetooth2
libbtctl4
libgnomebt0
nautilus-sendto
libopenobex1

On to my problems. The first seems to be trivial. When I right click on a file and do a Send To, use obex and select my phone, the file is transferred with all blank spaces replaced with %20 which is extremely annoying.

Secondly, when I go into nautilus and go to "obex://" my phone shows up, but when I click on it nothing happens. However, if I remove my computer from the My Devices area on my phone, and attempt to access my phone again, it asks to pair again, asks to allow access from my computer, and then works. However, it only works once, if I close the window, and then go back to obex:// click on my phone, my phone asks to allow permission from the computer, which I accept, then nautilus complains:
> **Nautilus cannot display "obex://[00:18:13:09:b1:13]".**
Please select another viewer and try again.
Then returns to the behavior of doing nothing when I select my phone.

Another thing, I like to use my phone as a bluetooth remote for Amarok. I have the amarok.hid on my phone. There are only two conditions under which I can connect with the remote:
1) I use this command in the terminal ```
sudo hidd --connect 00:18:13:09:B1:13
``` Then my phone asks to allow connection and thing asks to use remote. This isn't too bad, but I think I should be able to just start things from my phone.
2) I start a filesharing session (which requires removing my computer from my phone's device list and then pairing them again by using the obex:// protocol in nautilus (extremely annoying).

Finally, I cannot send files from my phone to my PC. I run the filesharing app (Applications->Accessories->Bluetooth File Sharing) and and does not matter whether or not my phone is paired with my computer, my phone says "Bluetooth connection failed." Also, when I have them paired, if on my phone I attempt to view the services on my computer it says:
> Service supported:
No local services found.

Just a hunch, but it seems to me like my computer doesn't remember the passkey or accept incoming connections. Any help is appreciated.

---

### Post by atlanta800 on 2007-06-29
*BUMP*
Anyone else even having similar problems?

---

### Post by bryngeo on 2007-07-06
oh yeah, I'm starting to think bluetooth dun with feisty is a myth:(

---

