---
title: "DHCP server with Squid3 installed, no win update caching?"
date: 2013-04-24
forum: General Help
---

### Post by Gorlist on 2013-04-24
Hi, last few days ive been trying to setup Ubuntu to act as a local DHCP server for my repair systems. So far its working fine, wlan0 is the gateway to the internet and eth0 runs to a switch as the local network.

Installed squid3, followed a number of guides ([http://ubuntuserverguide.com/2012/05/how-to-install-and-configure-proxy-server-with-squid3-on-ubuntu-server-12-04-lts.html](http://ubuntuserverguide.com/2012/05/how-to-install-and-configure-proxy-server-with-squid3-on-ubuntu-server-12-04-lts.html)) and it just doesn't appear to work. Basically I want it to automaticaly act as a proxy to cache windows updates, specificlly without having to setup or define parameters on the work machines.

```
acl internal_network src 172.22.22.0/24
acl all src 0.0.0.0/0.0.0.0

acl windowsupdate dstdomain windowsupdate.microsoft.com
acl windowsupdate dstdomain .update.microsoft.com
acl windowsupdate dstdomain download.windowsupdate.com
acl windowsupdate dstdomain redir.metaservices.microsoft.com
acl windowsupdate dstdomain images.metaservices.microsoft.com
acl windowsupdate dstdomain c.microsoft.com
acl windowsupdate dstdomain www.download.windowsupdate.com
acl windowsupdate dstdomain wustat.windows.com
acl windowsupdate dstdomain crl.microsoft.com
acl windowsupdate dstdomain sls.microsoft.com
acl windowsupdate dstdomain productactivation.one.microsoft.com
acl windowsupdate dstdomain ntservicepack.microsoft.com

acl CONNECT method CONNECT
acl wuCONNECT dstdomain www.update.microsoft.com
acl wuCONNECT dstdomain sls.microsoft.com

http_access allow CONNECT wuCONNECT internal_network
http_access allow windowsupdate internal_network

http_port 3128 transparent

access_log /var/log/squid3/access.log
always_direct allow all

# ==============================
# OPTIONS WHICH AFFECT THE CACHE SIZE
# ==============================

range_offset_limit -1
maximum_object_size 1024 MB
quick_abort_min -1
cache_dir aufs /home/repair-server/squid3-cache/ 60000 16 256


# ==============================
# Add one of these lines for each of the websites you want to cache.
# ==============================

refresh_pattern -i microsoft.com/.*\.(cab|exe|ms[i|u|f]|asf|wm[v|a]|dat|zip) 4320 80% 43200 reload-into-ims

refresh_pattern -i windowsupdate.com/.*\.(cab|exe|ms[i|u|f]|asf|wm[v|a]|dat|zip) 4320 80% 43200 reload-into-ims

refresh_pattern -i my.windowsupdate.website.com/.*\.(cab|exe|ms[i|u|f]|asf|wm[v|a]|dat|zip) 4320 80% 43200 reload-into-ims

#refresh_pattern -i avg.com/.*\.(bin) 4320 80% 43200 reload-into-ims

refresh_pattern ([^.]+.|)avg.com/.*\.(bin) 4320 100% 43200 reload-into-ims;

# ==============================
# DONT MODIFY THESE LINES
# ==============================

refresh_pattern \^ftp:           1440    20%     10080
refresh_pattern \^gopher:        1440    0%      1440
refresh_pattern -i (/cgi-bin/|\?) 0     0%      0
refresh_pattern .               0       20%     4320
```

Nothing appears in the access.log however squid is running fine. 
My network interface:

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
    wpa-ssid MYWIRELESSROUTER
    wpa-psk MYWPAPASSWORD
    address 192.168.0.39
    netmask 255.255.255.0
    gateway 192.168.0.1
    network 192.168.0.1
    dns-nameservers 192.168.0.1

auto eth0
iface eth0 inet static
    address 172.22.22.1
    netmask 255.255.255.0
    network 172.22.22.0
    broadcast 172.22.22.255
```

Any suggestions or glaring mistakes?

---

### Post by SeijiSensei on 2013-04-24
You probably are just missing the iptables rule that you need to redirect outbound web requests through the proxy.  Try adding this to your iptables ruleset:

```
/sbin/iptables -A PREROUTING -s your.lan.ip.addr/mask -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
```

Replace "your.lan.ip.addr/mask" with the subnet address of the machines connecting to the proxy, e.g., "192.168.1.0/24".

This rule grabs traffic from LAN clients with a destination port 80 (HTTP) and redirects it to localhost:3128 where the proxy is listening.  If you changed the default squid port from 3128 to something else, you need to use that value in the iptables rule.

---

### Post by Gorlist on 2013-04-25
thank you for the reply - added to iptables, still no caching, acces log is empty. just trying some different tweaks at the moment.

---

### Post by dcstar on 2013-04-26
> **Gorlist said:**
> 
Installed squid3, followed a number of guides ([http://ubuntuserverguide.com/2012/05/how-to-install-and-configure-proxy-server-with-squid3-on-ubuntu-server-12-04-lts.html](http://ubuntuserverguide.com/2012/05/how-to-install-and-configure-proxy-server-with-squid3-on-ubuntu-server-12-04-lts.html)) and it just doesn't appear to work. Basically I want it to automaticaly act as a proxy to cache windows updates, specificlly without having to setup or define parameters on the work machines.
............

[http://wiki.squid-cache.org/SquidFaq/WindowsUpdate](http://wiki.squid-cache.org/SquidFaq/WindowsUpdate)

---

