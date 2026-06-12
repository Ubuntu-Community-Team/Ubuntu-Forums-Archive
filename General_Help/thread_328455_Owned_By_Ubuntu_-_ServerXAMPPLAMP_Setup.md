---
title: "Owned By Ubuntu - Server/XAMPP/LAMP Setup"
date: 2006-12-30
forum: General Help
---

### Post by Gamzarme on 2006-12-30
I don't know where to go.

I've done everything I can.

I just installed Ubuntu 5.10 on my old computer (the highest version of Ubuntu that will run on it). Everything works great. I have no IP address for that computer. I want the IP to be static set at 192.168.1.8 (which is not in the range of my DHCP addresses, I've made sure).

I have XAMPP (LAMP) installed on my server in the correct directory and everything is functioning properly as far as I know, though I do not know if Apache is serving up pages due to the fact that accessing the server via remote browser using the IP of the server does not work.

What am I missing?

What do I do next?

---

### Post by Littleweseth on 2006-12-31
Blantantly plagiarising from [http://www.ubuntuforums.org/archive/index.php/t-15057.html](http://www.ubuntuforums.org/archive/index.php/t-15057.html) ;

mendicant
February 14th, 2005, 04:10 AM
Look in /etc/network/interfaces

For a static IP address, you need a stanza like:

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1

So, to set static IP : open up the /etc/network/interfaces file with sudo nano /etc/network/interfaces and change the first three lines to look like the above - you problably want to leave the other three lines alone, as they will have been autodetected for your network.

Re testing your server : you could go to the server itself and browse to [http://localhost](http://localhost) to test apache - use firefox if you have it, or you can install one of the text browsers like lynx, links or elinks. If you want to test php, make a test file in your webroot;

<?php
phpinfo();
?>

save the file with a .php extension and browse to it. If all is working well, you'll get the giant phpinfo() page, telling you everything you want to know about your php install and then some. If PHP isn't working, then you will actually see the contents of the file.

---

### Post by Gamzarme on 2006-12-31
> **Littleweseth said:**
> Blantantly plagiarising from [http://www.ubuntuforums.org/archive/index.php/t-15057.html](http://www.ubuntuforums.org/archive/index.php/t-15057.html) ;

mendicant
February 14th, 2005, 04:10 AM
Look in /etc/network/interfaces

For a static IP address, you need a stanza like:

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1

So, to set static IP : open up the /etc/network/interfaces file with sudo nano /etc/network/interfaces and change the first three lines to look like the above - you problably want to leave the other three lines alone, as they will have been autodetected for your network.

Re testing your server : you could go to the server itself and browse to [http://localhost](http://localhost) to test apache - use firefox if you have it, or you can install one of the text browsers like lynx, links or elinks. If you want to test php, make a test file in your webroot;

<?php
phpinfo();
?>

save the file with a .php extension and browse to it. If all is working well, you'll get the giant phpinfo() page, telling you everything you want to know about your php install and then some. If PHP isn't working, then you will actually see the contents of the file.

Littleweseth, you are awesome, thank you so much. =)

The server is up and secured. I posted your reply (including the part where you plagiarized, =P ) on [another forum]("http://www.apachefriends.org/f/viewtopic.php?p=92356")...credit due where deserved.

-Patrick

---

