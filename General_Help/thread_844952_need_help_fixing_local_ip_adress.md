---
title: "need help fixing local ip adress"
date: 2008-06-30
forum: General Help
---

### Post by hamzaB on 2008-06-30
i'm new to ubuntu since i only installed yesterday and don't know anything about it.anyway i downloaded azureus to handle my torrents and i also configured the router and ubuntu's firewall .i need to know what to do so i can fix the local ip adress so it doesn't change every time i turn off the router.and i appreciate your help.

---

### Post by iaculallad on 2008-06-30
You have to setup your IP address to be static then:

```
gksu gedit /etc/network/interfaces
```

If you can see this line: **iface eth0 inet dhcp** on the /etc/network/interfaces file

Change it to:

**iface eth0 inet static**

Then try changing the other settings within the file to fit your network need:

> address 192.168.0.100
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

address = IP address of your PC
netmask = by default it's /24 or 255.255.255.0
broadcast = by default, that would be the value when you're using the 192.168.0.x subnet. Change it if you're using other private IP subnet (192.168.1.x).
gateway = IP address of your router.

Save your file and restart the network daemon.

```
sudo /etc/init.d/networking restart
```

---

### Post by hamzaB on 2008-06-30
when i put that command it came :
auto lo
iface lo inet loopback
what should i do?

---

### Post by iaculallad on 2008-06-30
Ok. Let's just do it the graphical way:

Navigate to System->Administration->Network. On the "Connection" tab, Click on "Wired Connection" and click on "Properties" button. Uncheck "Enable Roaming Mode" option. Change "Configuration:" to "Static IP Address".
Input all the valid information for IP Address, Subnet Mask, and Gateway Address.

IP Address = 32-bit address you want for your PC (i.e: 192.168.1.2)
Subnet Mask = 255.255.255.0
Gateway = 32-bit address of your router (i.e: 192.168.1.1)

Click on OK then select the "DNS" tab. Click on the "Add" button and include your DNS server. You can also place the IP address of your router in here.

Click on close and restart your network daemon using your terminal.

```
sudo /etc/init.d/networking restart
```

---

### Post by hamzaB on 2008-06-30
thanks a lot man.it worked.

---

