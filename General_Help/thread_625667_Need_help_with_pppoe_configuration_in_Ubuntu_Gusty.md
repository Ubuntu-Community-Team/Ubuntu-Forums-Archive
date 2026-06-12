---
title: "Need help with pppoe configuration in Ubuntu Gusty Gibbon"
date: 2007-11-28
forum: General Help
---

### Post by sabertooth on 2007-11-28
Hellp people :) ,

Recently i happily switched to Ubuntu and everything worked fine until the time came to configure my **pppoe** connection.First it detected my network adapters (**eth0** and **eth0 avahi**) and then i carried on with the next steps in **sudo pppoeconf**.The internet worked fine, but later i started facing problems such as only one network adapter(eth0 with no info available!) was being detcted on startup and hence the internet would not start.I had to work hard to manually start my connection during next startup with less successful attempts.:(

What is the **"right way"** to configure and connect to the internet with a pppoe connection in ubuntu 7.10?:confused: and yeah, my connection works absolutely fine in Win XP.

---

### Post by Swooter on 2007-11-28
I'm not sure I follow you exactly here.  

Is your set-up still attempting to DHCP off of the upstream device (router)?  Or is it a Static IP address?  Do you connect through a Modem which provides the login/password (if needed)?

I (sometimes) connect using PPPOE and have my eth0 set-up to "Obtain DHCP" automatically (which it does).  I don't need to set anything up diffently when connecting PPPOE or Cable Modem...

Describe your set-up in more detail please.

---

### Post by sabertooth on 2007-11-29
Thnx for the reply.My connection has a Static IP and the config in windows xp shows:

Windows IP Configuration

        Host Name . . . . . . . . . . . . : warehouse
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Mixed
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Realtek RTL8139 Family PCI Fast Ethe
rnet NIC
        Physical Address. . . . . . . . . : 00-01-2E-15-FE-8C
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 169.254.233.65
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :

PPP adapter Connection to akd:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 210.89.53.24
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 210.89.53.24
        DNS Servers . . . . . . . . . . . : 203.115.71.66
                                            203.115.81.38
        NetBIOS over Tcpip. . . . . . . . : Disabled

---

