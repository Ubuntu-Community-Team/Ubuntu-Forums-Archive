---
title: "Configure DHCP client in LAN for dynamic DNS servers"
date: 2016-10-27
forum: General Help
---

### Post by oldgraf on 2016-10-27
My ISP change the rules...From static IP now must connect with DHCP. But DNS servers from ISP changed from time to time(when geting new lease for example). I have running DHCP server for LAN clients.

have this configs
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp 

# Internal
auto eth1
iface eth1 inet static
    address 192.168.1.1
    netmask 255.255.255.0

NAT is working like
-A PREROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE


In dhcp.conf have 
option domain-name-servers ISP-DNS1-IP,ISP-DNS2-IP;
and clients from LAN works fine. But now this ISP-DNS1-IP and ISP-DNS2-IP are dynamicaly two. 
How can tell clients who is DNS servers
Thanks

---

### Post by SeijiSensei on 2016-10-27
You could use Google's servers at 8.8.8.8 and 8.8.4.4.

---

### Post by oldgraf on 2016-10-28
Thank You
And no other way ?

---

### Post by SeijiSensei on 2016-10-29
Well if your ISP is going to persist in changing its DNS server addresses, I can't think of another option except to use servers outside their network.  Here are some more: [https://www.lifewire.com/free-and-public-dns-servers-2626062](https://www.lifewire.com/free-and-public-dns-servers-2626062)

---

