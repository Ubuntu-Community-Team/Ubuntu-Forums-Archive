---
title: "Static IP will not Stay, nor work"
date: 2020-06-18
forum: General Help
---

### Post by uclalinux on 2020-06-18
Hello, 

I am a long time Ubuntu user however I cannot fix this issue on 20.04

I go to change my wire eth0 and 1 from Dynamic to Static; I set my IP, and Netmask, and click okay. 

It tries to find an ip and than does not work, and reverts to dynamic. 

I already have other items on the switch working on my new subnets. 


Am I missing something???

I've tried the following;

[https://linuxconfig.org/how-to-configure-static-ip-address-on-ubuntu-20-04-focal-fossa-desktop-server](https://linuxconfig.org/how-to-configure-static-ip-address-on-ubuntu-20-04-focal-fossa-desktop-server)
[https://www.osradar.com/set-a-static-ip-address-ubuntu-20-04/](https://www.osradar.com/set-a-static-ip-address-ubuntu-20-04/)
[https://www.linuxtechi.com/assign-static-ip-address-ubuntu-20-04-lts/#:~:text=Assign%20Static%20IP%20Address%20on%20Ubuntu%2020.04%20LTS%20Desktop&text=Login%20to%20your%20desktop%20environment,and%20then%20choose%20wired%20settings.&text=In%20the%20next%20window%2C%20Choose,gateway%20and%20DNS%20Server%20IP](https://www.linuxtechi.com/assign-static-ip-address-ubuntu-20-04-lts/#:~:text=Assign%20Static%20IP%20Address%20on%20Ubuntu%2020.04%20LTS%20Desktop&text=Login%20to%20your%20desktop%20environment,and%20then%20choose%20wired%20settings.&text=In%20the%20next%20window%2C%20Choose,gateway%20and%20DNS%20Server%20IP)

---

### Post by TheFu on 2020-06-18
I have no idea how to do it with a GUI. Sorry.  [https://help.ubuntu.com/stable/ubuntu-help/net-manual.html.en](https://help.ubuntu.com/stable/ubuntu-help/net-manual.html.en) is the Ubuntu Desktop Guide. The required settings are:  IP, netmask, at least 1 DNS server and default gateway. Entering just the IP and netmask is NOT sufficient.

The static IP cannot be inside the DHCP range provided by the DHCP server. Verify that and all network config settings.

Some DHCP servers can "reserve" IPs for clients and hand those out. That is handy for portable systems. They want
[LIST]
[*]the NIC MAC
[*]the hostname
[*]the IP address
[/LIST]
The DHCP will return the IP, netmask, any DNS servers and default gateway. Effectively, the IP will be static on that subnet, but not static on every other network the device visits.  Home routers are often the DHCP server for a simple network. The setup of dhcp reservations using dd-wrt can be a little ugly.

The links show what you were supposed to do, not what actually happened. For example, if the NIC device name is different on your system, which is highly likely, then that will need to be changed.  Assuming enp0s3 or eth0 probably is a bad idea. None of my ethernet devices have names like that. One uses ens3, another uses enx000ec6c76411.  They change based on the driver and MAC.  If the instructions in the links don't work, it is probably the wrong device OR if you are trying the netplan method, the indentation isn't correct OR both.

---

### Post by uclalinux on 2020-06-18
Solved.  Reinstalled OS 20.04

---

