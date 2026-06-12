---
title: "Ubuntu Server Apt-get issue"
date: 2013-06-11
forum: General Help
---

### Post by Vague Lines on 2013-06-11
Hey everyone, i have searched majority if not all threads on here but nothing has successfully worked. I have gone and installed ubuntu server in virtualbox, changed the /etc/network/interfaces file to allow a static ip address as follows:

```
auto eth0
iface eth0 inet static
address 192.168.1.149
netmask 255.255.255.0
network 192.168.1.149
gateway 192.168.1.254
```

Whenever i run apt-get update i get errors like :

w: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/natty-security/main/binary-i386/Packages) 404 Not Found [IP: 91.189.92.190.80]

And there are multiple other lines simliar to this but they are "restricted", "universe" and "multiverse". The entire purpose is to create a mail server that has apache2, php and squirrelmail.

I can ping [www.google.com]("http://www.google.com") so i am connected to the internet, i just cannot seem to be able to get the packages to update the system. 

Any help will be highly appreciated.

Thanks Alot!!! :)

---

### Post by slickymaster on 2013-06-11
> **Vague Lines said:**
> ... Whenever i run apt-get update i get errors like :

w: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/natty-security/main/binary-i386/Packages) 404 Not Found [IP: 91.189.92.190.80]... 

You're trying to update a Ubuntu release which reached its EOL on October, 2012.
 I would advise you upgrading to or re-installing 12.04 if you want to keep LTS'ing.

---

### Post by Vague Lines on 2013-06-12
Hey, thanks alot for the reply and advice. Although i have gone and installed Ubuntu Server 12.04 and tried running apt-get update and still i am getting errors such as "  W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/precise-security/InRelease" and other various ones related to this error. I have update my /etc/network/interfaces to a static ip address and entered in what i am sure are the correct details.

Please someone give some suggestions .

Thank you very much

---

### Post by slickymaster on 2013-06-12
> **Vague Lines said:**
> Hey, thanks alot for the reply and advice. Although i have gone and installed Ubuntu Server 12.04 and tried running apt-get update and still i am getting errors such as "  W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/precise-security/InRelease" and other various ones related to this error. I have update my /etc/network/interfaces to a static ip address and entered in what i am sure are the correct details.

Please someone give some suggestions .

Thank you very much

You aren't specifying much details to the surrounding circumstances that might explain what's behind your issue.

Your server can be connecting to the network but not reaching outside the network. Can you successfully ping **security.ubuntu.com** or **google.com**, for example? If not you can edit your **/etc/network/interfaces** and set eth0 to DHCP, rather than static and then had your router take care of giving the server a static IP.
You can find out more about IP configurations [here]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html#ip-addressing").

If you can ping outside your network one thing you can do is to edit your **/etc/apt/sources.list** ```
gksudo geany /etc/apt/sources.list
```and change:```
nz.archive
```
to:```
archive
```on each line, save it and close it. Then run:```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by HiImTye on 2013-06-12
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
also check```
dig nz.archive.ubuntu.com
dig @8.8.8.8 nz.archive.ubuntu.com
```
if you can ping google but not receive updates it sounds like either a firewall or dns issue

---

