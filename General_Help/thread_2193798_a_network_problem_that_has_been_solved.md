---
title: "a network problem that has been solved"
date: 2013-12-14
forum: General Help
---

### Post by iebo on 2013-12-14
i was struggling the last few days because  i did stupid mistake  and removed network-manager  :(

been looking everywhere how i can reinstall nm without internet connection i only have wireless not wired 
:guitar:only this answer helped me

				 				 					 						 	[**[COLOR=#000000]unit145[/COLOR]**]("http://ubuntuforums.org/member.php?u=1305972")
[http://ubuntuforums.org/showthread.php?t=1354152&page=3](http://ubuntuforums.org/showthread.php?t=1354152&page=3)

its not possible to reply on that thread because its closed 

i'm not sure where i can post this...but thank u unit145 , thank u a million :P

---

### Post by varunendra on 2013-12-15
Just so you know, you can use the following command to get the exact download links to all the packages (most relevant ones) required to install a package :
```
apt-get install --print-uris <package name>
```
The "--print-uris" options causes apt to print the download links instead of downloading and installing them itself. Of course the package information must already exist in apt-cache (which means if you have to install a package from non-default repositories, then "apt-get update" must have been run at least once after enabling those repositories).

The benefit of this method is that you don't have to worry or even know about the dependencies or their suitable versions, the apt package manager takes care of that.

Once the packages have been downloaded, you can install them with "sudo dpkg -i *" after placing all the mutually dependent packages in the same place.

Oh, and you can also connect wirelessly without NM or another GUI network manager, using the /etc/network/interfaces file : [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo#Adding_it_to_.2BAC8-etc.2BAC8-network.2BAC8-interfaces](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo#Adding_it_to_.2BAC8-etc.2BAC8-network.2BAC8-interfaces)

---

### Post by iebo on 2013-12-15
hey varunendra

thanks for the info ,  u are saying i can use this command when i don't have connection to install packages?

i understand that we are able to connect internet via terminal or using /etc/network/interfaces

but for example  when i try this command  :

dhclient wlan0

i have this error >

No DHCPOFFERS received No working leases

:(

so my only option now is nm , it doesn't work great but it works 

i'm still running ubuntu 10.04

---

### Post by varunendra on 2013-12-15
Yeah, as long as the package info is within apt-cache, it will return the download links which you can use to download them on another computer with a working internet connection.

However, if this cached info is too old (and those packages have been replaced by another version in the online repos), the links won't work (since those packages would be no longer there) and you'd need to update the apt-cache (by running "sudo apt-get update") at least once which would require internet connection. But even in that case, at least you will get the package names of all the dependencies and then you can manually download the updated packages directly from online repos and try installing them in the same way.

By default this cached info contains information of only the default repositories, of course. :)

As for the dhclient error, you can always use a manually assigned IP instead of relying on DHCP offers. That address goes in the same /etc/network/interfaces file and makes it look like this -
```
auto wlan0
[COLOR="#0000CD"]iface wlan0 inet static
address **10.0.0.100**
netmask 255.255.255.0
gateway **10.0.0.1**
dns-nameservers **192.168.3.45 192.168.8.10**[/COLOR]
wireless-essid   MYNETWOTK
wireless-key     FEFEFEFEFE
wireless-channel 11
wireless-mode    managed
```
Of course the address, gateway and dns should be changed as suitable to your local network.

---

### Post by iebo on 2013-12-16
hello , i have installed wicd instead of nm its work ok so far but i'm missing (  pptp vpn ).. 

 the reason i delete nm is that i had some problems after booting its say my wlan  still down . the issue [Ralink]("http://ubuntuforums.org/showthread.php?t=2186830&p=12843141#post12843141") so to fix it i need to reboot over and over  ! 

"sudo ifconfig wlan0 up" or "sudo ifup wlan0" doesn't  solve this problem  

unfortunately this /etc/network/interfaces setting  didn't work with me either and my laptop not able to join the lan 

apt-cache is great tool :) i'm sure this going to help me in future

---

