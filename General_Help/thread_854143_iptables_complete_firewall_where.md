---
title: "iptables complete firewall where?"
date: 2008-07-09
forum: General Help
---

### Post by dapim on 2008-07-09
where i can find a complete iptables firewall?
in ubuntu web site just a basic firewall  i would like to find a complete and realble one

---

### Post by brian_p on 2008-07-09
> **dapim said:**
> where i can find a complete iptables firewall?
in ubuntu web site just a basic firewall  i would like to find a complete and realble one

Google: Linux good firewall

---

### Post by kevdog on 2008-07-09
Im not sure what you mean by complete.  Iptables is configurable, and complete for you might not be complete for the next user.

I have used this script for my basic iptables scipt to set basic priviledges.  Please not however this is just a working skeleton.  


#!/bin/sh
#
#############################################################################
#
# File: iptables.sh
#
# Purpose: To build a basic iptables policy with default log and drop rules.
#          This script was written for the book "Linux Firewalls: Attack
#          Detection and Response" published by No Starch Press.
#
# Copyright (C) 2006-2007 Michael Rash (mbr@cipherdyne.org)
#
# License (GNU Public License):
#
#   This program is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU General Public License for more details.
#
#   You should have received a copy of the GNU General Public License
#   along with this program; if not, write to the Free Software
#   Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307
#   USA
#
#
#############################################################################
#
# $Id: index.html 1740 2008-07-05 15:27:44Z mbr $
#

IPTABLES=/sbin/iptables
MODPROBE=/sbin/modprobe
INT_NET=192.168.10.0/24

### flush existing rules and set chain policy setting to DROP
echo "[+] Flushing existing iptables rules..."
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT DROP
$IPTABLES -P FORWARD DROP

### load connection-tracking modules
#
$MODPROBE ip_conntrack
$MODPROBE iptable_nat
$MODPROBE ip_conntrack_ftp
$MODPROBE ip_nat_ftp

###### INPUT chain ######
#
echo "[+] Setting up INPUT chain..."

### state tracking rules
$IPTABLES -A INPUT -m state --state INVALID -j LOG --log-prefix "DROP INVALID " \
--log-ip-options --log-tcp-options
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### anti-spoofing rules
$IPTABLES -A INPUT -i eth1 -s ! $INT_NET -j LOG --log-prefix "SPOOFED PKT "
$IPTABLES -A INPUT -i eth1 -s ! $INT_NET -j DROP

### ACCEPT rules
$IPTABLES -A INPUT -i eth1 -p tcp -s $INT_NET --dport 22 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT

### default INPUT LOG rule
$IPTABLES -A INPUT -i ! lo -j LOG --log-prefix "DROP " --log-ip-options --log-tcp-options

###### OUTPUT chain ######
#
echo "[+] Setting up OUTPUT chain..."

### state tracking rules
$IPTABLES -A OUTPUT -m state --state INVALID -j LOG --log-prefix "DROP INVALID " \
--log-ip-options --log-tcp-options
$IPTABLES -A OUTPUT -m state --state INVALID -j DROP
$IPTABLES -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### ACCEPT rules for allowing connections out
$IPTABLES -A OUTPUT -p tcp --dport 21 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 22 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 25 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 43 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 4321 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 53 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT

### default OUTPUT LOG rule
$IPTABLES -A OUTPUT -o ! lo -j LOG --log-prefix "DROP " --log-ip-options --log-tcp-options

###### FORWARD chain ######
#
echo "[+] Setting up FORWARD chain..."

### state tracking rules
$IPTABLES -A FORWARD -m state --state INVALID -j LOG --log-prefix "DROP INVALID " \
--log-ip-options --log-tcp-options
$IPTABLES -A FORWARD -m state --state INVALID -j DROP
$IPTABLES -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

### anti-spoofing rules
$IPTABLES -A FORWARD -i eth1 -s ! $INT_NET -j LOG --log-prefix "SPOOFED PKT "
$IPTABLES -A FORWARD -i eth1 -s ! $INT_NET -j DROP

### ACCEPT rules
$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 21 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 22 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 25 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 43 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 4321 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp --dport 53 -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p udp --dport 53 -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p icmp --icmp-type echo-request -j ACCEPT

### default LOG rule
$IPTABLES -A FORWARD -i ! lo -j LOG --log-prefix "DROP " --log-ip-options --log-tcp-options

###### NAT rules ######
#
echo "[+] Setting up NAT rules..."
$IPTABLES -t nat -A PREROUTING -p tcp --dport 80 -i eth0 -j DNAT --to 192.168.10.3:80
$IPTABLES -t nat -A PREROUTING -p tcp --dport 443 -i eth0 -j DNAT --to 192.168.10.3:443
$IPTABLES -t nat -A PREROUTING -p udp --dport 53 -i eth0 -j DNAT --to 192.168.10.4:53
$IPTABLES -t nat -A POSTROUTING -s $INT_NET -o eth0 -j MASQUERADE

###### forwarding ######
#
echo "[+] Enabling IP forwarding..."
echo 1 > /proc/sys/net/ipv4/ip_forward

exit
### EOF ###

---

### Post by ibutho on 2008-07-09
You can configure your own firewall using Shorewall (Shoreline Firewall). Its a good frontend for iptables.

---

### Post by dapim on 2008-07-09
and prevet brute force attack, ddos attack, ping of death ....

---

### Post by kevdog on 2008-07-09
Ping of death would be setup using limit commands, brute force attacks?? can you be more specific -- what service would attempted to be brute forced attacked?

---

### Post by dapim on 2008-07-09
ssh, ftp

---

### Post by kevdog on 2008-07-09
Again for attempting to stop ssh brute force attacks, a variety of methods could be used.  This could include modifications in the iptables to limit the amount of new connection.  There are other methods such as fail2ban which are slightly more dynamic (meaning they can ban specific IP addresses for a certain amount of time then after x seconds they are unbanned -- or can permanently ban).  fail2ban uses a daemon to read the access logs, then if see repeated access attempts will modify iptables accordingly. fail2ban should work with ftp (the website claims it will, but I have never tried since I don't run a ftp server, only ssh).  
[http://www.ducea.com/2006/07/03/using-fail2ban-to-block-brute-force-attacks/](http://www.ducea.com/2006/07/03/using-fail2ban-to-block-brute-force-attacks/)


Iptables can be used exclusively with the recent module like the following:

iptables -A FORWARD -i ethLRZ -p tcp &#8211;dport 22 -m state &#8211;state NEW -m recent &#8211;set &#8211;name SSH
iptables -A FORWARD -i ethLRZ -p tcp &#8211;dport 22 -m state &#8211;state NEW -m recent &#8211;update &#8211;seconds 60 &#8211;hitcount 5 &#8211;rttl &#8211;name SSH -j DROP

These two iptables statements will rate-limit incoming SSH connections to 5 in a one minute window. Regular users will rarely ever trigger this limitation, but being inside iptables makes it react *much* faster than fail2ban.

---

