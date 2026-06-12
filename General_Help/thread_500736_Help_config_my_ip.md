---
title: "Help config my ip"
date: 2007-07-14
forum: General Help
---

### Post by Wuu on 2007-07-14
i want to set static ip ,but when i do it internet is not working ,but i use the same settings like on windows..

ifconfig in network automatic configuration
[PHP]addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0[/PHP]

is this my network settings? i try to set them in manual (i set the same number) like in ifconfig but its not working! so what i haw to do to set static ip?

i am using router (d-link).. senx

---

### Post by starsky on 2007-07-14
hi there :)

do this 
$ sudo mv /etc/network/interfaces /etc/network/interfaces.backup
(this will backup your old file to /etc/network/interfaces.backup)

$ sudo unlink /etc/network/interfaces

$ sudo gedit /etc/network/interfaces and add the lines below -


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.4
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

save the file.

Post back 

HTH

---

### Post by Wuu on 2007-07-15
i don't understood  :( 
[PHP]
main@main-laptop:~$ sudo unlink /etc/network/interfaces auto lo
unlink: extra operand `auto'
Try `unlink --help' for more information.[/PHP]

---

### Post by Wuu on 2007-07-15
NEWER EWER TRY THIS AT ALL !!!
I CANT RUN UBUNTU AFTER RESTART AT ALL 
and i just run this!
[PHP]$ sudo mv /etc/network/interfaces /etc/network/interfaces.backup
(this will backup your old file to /etc/network/interfaces.backup)

$ sudo unlink /etc/network/interfaces [/PHP]

---

