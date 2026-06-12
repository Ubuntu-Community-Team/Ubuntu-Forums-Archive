---
title: "DHCP, eth0 problem"
date: 2005-10-26
forum: General Help
---

### Post by oobe on 2005-10-26
OK, been using Kubuntu for about 6 months now.. switched to Debian a few weeks ago to check it out and play around, been waiting for Breezy and here it is.
During the install it fails to retrieve config from DHCP. Retry, retry, reboot, everything, to no avail. So I leave it and finish the install. Tried setting eth0 to dhcp and auto through the Settings Manager, reboot. Didn't work, now I can't seem to edit anything when I enter the password for admin privileges..

I'm going to format it again anyway - and the fact DHCP will not work during install is certain. Does anyone have a recommended plan of action/configuration after I install next..

Kind Regards,
oobe

---

### Post by oobe on 2005-10-26
After more searching the forums I've found "dhclient eth0" has assigned me an ip. This is obviously a temporary fix, but at least now I can investigate the issue from the problematic computer.

Still have NFI what to do :D

---

### Post by MarcDM on 2005-10-26
Wait don't format. 

The networking configuration in Debian/Ubuntu/Kubuntu? is super simple. 

there's this one file */etc/network/interfaces* 

It has a super simple syntax.
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


```is all you need to get dhcp setup on your first network card. If DHCP doesn't work you can set a static ip by changing the file to :```


auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
    address 192.168.6.4
    netmask 255.255.255.0
    gateway 192.168.6.1
    

```See I've commented out the dhcp line. When we fix the DHCP server, we can comment out the static sections and put back dhcp.

After changing this file, you can do one of the foll to enable the change:
```
 > sudo /etc/init.d/networking restart
```
OR
```
 > sudo ifdown eth0 && sudo ifup eth0
```

Note that the indenting is not important. I just think it looks nice. 

If those don't wor, or you want to try something else, you can use the ip command (installed on Ubuntu by default, available in the iproute2 package on Debian).

to de-configure the network card :
```
    > sudo ip addr flush dev eth0
```
to add an ip address :
```
    > sudo ip addr add 192.168.6.4/24 dev eth0
```
to setup the network card then try DHCP manually, do :
```

 > sudo ip addr flush dev eth0 && sudo ip link set eth0 down
 > sudo ip link set eth0 up
 > sudo /sbin/dhclient eth0

```

I hope this helps your worries.

---

### Post by oobe on 2005-10-26
MarcDM, I really appreciate your help.

I didn't bother editing the config file, just went straight for the jugular and deconfigured and used the set of commands you set out. It worked. I logged out then in again and it was working fine. 

There is still one problem - when I go to network settings it shows eth0 is up and running - which is good - but Id like to be able to view the particulars of eth0. When I try to use Admin mode it just blinks after i enter the password and doesnt let me click on the interface..

---

### Post by oobe on 2005-10-26
Also.. I am going to format since I have been messing around with other things as well. Since I am 99% certain the DHCP will be an issue again, do you recommend doing exactly what you recommended (which I did)

Regards,
oobe

---

### Post by alvonsius on 2005-10-26
[QUOTE=oobe]MarcDM, I really appreciate your help.

I didn't bother editing the config file, just went straight for the jugular and deconfigured and used the set of commands you set out. It worked. I logged out then in again and it was working fine. 

There is still one problem - when I go to network settings it shows eth0 is up and running - which is good - but Id like to be able to view the particulars of eth0. When I try to use Admin mode it just blinks after i enter the password and doesnt let me click on the interface..[/QUOTE]

About the administrator mode, just write ```
sudo kcontrol
``` at console and there you go, the admnistator control panel. Just use it for administration stuff only, for appereance and other personal, use your own control panel.

---

### Post by mattsm8 on 2005-10-27
Thanks alvonsius! I had the same problem and I could fix it with the kcontrol!

Complete procedure for the other googlers out there:

I had the problem that after a fresh install of KUBUNTU Breezy 5.10 the network did not work. It turned out that it was not activated by default upon startup....

You can fix it by opening a console and starting the admin control by typing:
```
sudo kcontrol &
```
Now you should see the admin control window. In the tree view expand "Internet & Network" and select "Network Settings". Now you see the network interfaces. eth0 should be enabled, when I enabled it by pressing the "Enable Interface" button everything worked fine after that. When you enable it make sure to check the box "Activate when the computer starts" so you don't have to go through this routine every time you reboot.

Cheers
mattsm8


[http://glawing.com]("http://glawing.com")

---

### Post by oobe on 2005-10-27
I still seem to be having the same problem even though now I can configure eth0 with admin privileges. I set it to DHCP and start on boot but when I reboot, I am still left without an IP and need to dhclient eth0.

I suspect this could be because I played around with the /etc/network/interfaces file, but I thought the system settings form would override that.

---

### Post by mattsm8 on 2005-10-27
I did not touch any file by hand, I only used kcontrol, so that might have been your problem. I always try it the easy way first. :)

---

### Post by MarcDM on 2005-11-23
[QUOTE=oobe]During the install it fails to retrieve config from DHCP. Retry, retry, reboot, everything, to no avail. So I leave it and finish the install. Tried setting eth0 to dhcp and auto through the Settings Manager, reboot. Didn't work[/QUOTE]

[QUOTE=oobe]I still seem to be having the same problem even though now I can configure eth0 with admin privileges. I set it to DHCP and start on boot but when I reboot, I am still left without an IP and need to dhclient eth0.

I suspect this could be because I played around with the /etc/network/interfaces file, but I thought the system settings form would override that.[/QUOTE]

It does override that but some more info to add to the thread. Please accept my apologies for being absent.

Here goes, there's another file in /etc/dhcp3/dhclient.conf
that controls the behaviour of the DHCP client. By default it has : 
```

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;

```

uncommented. If your dhcp server is set to deny/ignore unknown clients, then you will never get an IP address. Some of them are like this by default. 

To fix this,  remove the host-name field from that list and add a line above that says :
```

send host-name "ubuntuPC";

```

This will cause your PC to announce it's hostname as ubuntuPC to the DHCP server when seeking an IP.


or you can just open the file and add that line to the end of it. Leave the host-name field in the request, if you want the dhcp server to be able to override the hostname.

-----
Hope this helps.:)

---

