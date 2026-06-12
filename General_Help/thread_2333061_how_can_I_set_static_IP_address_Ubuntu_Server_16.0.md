---
title: "how can I set static IP address Ubuntu Server 16.04"
date: 2016-08-06
forum: General Help
---

### Post by Lukasz Tarkowski on 2016-08-06
how can I set static IP address Ubuntu Server 16.04?

---

### Post by &amp;KyT$0P# on 2016-08-06
Are you using NetworkManager on this server?

---

### Post by Lukasz Tarkowski on 2016-08-06
yes I think I am I can access ifconfig,   I am using Ubuntu Server the newest one and VirtualBox

---

### Post by Pumba! on 2016-08-06
Hi, you should edit **/etc/network/interfaces **file.

It probably looks like: 

*auto eth0*
*iface eth0 inet dhcp*

That means that it will enable eth0 (Your network card) automatically upon system boot, and that it will connect via dhcp.

You need to change this into something like: 
*auto eth0*
*iface eth0 inet static*
*   address 192.168.1.10*
*   netmask 255.255.255.0*
*   network 192.168.1.0*
*   gateway 192.168.1.1*
[I]   dns-nameservers 8.8.8.8
[/I]
Make sure you put the addresses that are relevant to your situation.

Upon reboot you should be conected to the specified static ip.
I suggest you backup your "interfaces" file before you start, just in case.

---

### Post by Lukasz Tarkowski on 2016-08-06
After I add IP and I type ifconfig it gives me 127.0.0.1 and stays that way, if I change it back to dhcp works normally, I need a static ip,  is there a generator for static ip for Ubuntu Server? Also says networking service failed to start

---

### Post by Lukasz Tarkowski on 2016-08-06
I forgot I don't have network manager,  how do I install on Ubuntu Server?

---

### Post by steeldriver on 2016-08-06
You don't need network manager if you're defining the interface via the /etc/network/interfaces file

What you DO need is to specify an address that's within the correct LAN IP range for your router, but OUTSIDE the router's reserved pool of DHCP addresses

---

### Post by Lukasz Tarkowski on 2016-08-06
now it is working fine still don't see the ip address I chose, hmm

---

### Post by Lukasz Tarkowski on 2016-08-06
Thank you all for help after rebooting the Ubuntu Server I have the IP address now :)

---

### Post by Lukasz Tarkowski on 2016-08-06
Now I have to configure so that I can access the website

---

### Post by Lukasz Tarkowski on 2016-08-06
I can now access my Apache server and says works and shows the template :)

---

### Post by Pumba! on 2016-08-06
Glad it worked out!

---

