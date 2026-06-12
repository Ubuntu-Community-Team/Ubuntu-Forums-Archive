---
title: "i need some iptables help. i think."
date: 2008-01-07
forum: General Help
---

### Post by girtart3d on 2008-01-07
ok so i asked a similar question before. but. something wont let me connect to anything p2p related. so uh. i saw someone said to allow the port in 'iptables' ...or something. can anyone explain this? and how i go about doing this.

---

### Post by p_quarles on 2008-01-07
Have you already configured iptables at all? Most people configure it using tools such as Firestarter or Guarddog, so if you've used any kind of "firewall" software, that may be the issue.

If not, it's more likely your router that you'll need to configure.

---

### Post by girtart3d on 2008-01-07
well i added the port to the allow list. but i still cant connect. and im sure my modem doesnt have any firewalls because it works on my windows os.

---

### Post by capink on 2008-01-07
You can go as the above poster mentioned and configre it using any of the gui frontends available. Or if you want to go the command line route, do the following:

1. Create a firewall script called firewall.sh in /etc/init.d:

```
sudo touch /etc/init.d/firewall
```

2. Copy the text below into /etc/init.d/firewall and save it after modifiying the port numbers to your liking. It is highlighted below in red color:

```
#!/bin/bash


start_firewall ()
{
# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules and chains

iptables -F
 iptables -X

# first set the default behaviour => accept connections
 iptables -P INPUT ACCEPT
 iptables -P OUTPUT ACCEPT

# Allow unlimited traffic from loopback (lo) device
 iptables -A INPUT -i lo -j ACCEPT
 iptables -A OUTPUT -o lo -j ACCEPT

# Setup connection oriented access
 iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow DHCP
# iptables -A INPUT -p udp -m udp -s 0/0 --sport 67:68 -d 0/0 --dport 67:68  -j ACCEPT
# iptables -A INPUT -p udp -m udp -s 0/0 --sport 67:68 -d 0/0 --dport 67:68  -j ACCEPT

# Allow DNS
# iptables -A INPUT -p udp  --sport 53 -j ACCEPT
# iptables -A INPUT -p tcp  --sport 53 -j ACCEPT


# Open Bittorrent tcp ports

 /sbin/iptables -I INPUT 1 -i eth0 -p tcp --tcp-flags SYN,RST,ACK SYN --dport [COLOR="#ff0000"]6881:6889[/COLOR] -m state --state NEW -j ACCEPT 
 /sbin/iptables -I INPUT 1 -i eth0 -p udp --dport [COLOR="#ff0000"]6881:6889[/COLOR] -m state --state NEW -j ACCEPT



# Open Bittorrent udp ports for "listing" (azureus dht)
 iptables -A INPUT -p udp --dport [COLOR="Red"]6881:6889[/COLOR] -j ACCEPT




# Allow amule
# /sbin/iptables -I INPUT 1 -i eth0 -p tcp --tcp-flags SYN,RST,ACK SYN --dport 4662 -m state --state NEW -j ACCEPT 
# /sbin/iptables -I INPUT 1 -i eth0 -p udp --dport 4662 -m state --state NEW -j ACCEPT
# iptables -A INPUT -p udp -m udp --dport 4662 -j ACCEPT

# DROP everything and Log it
 iptables -A INPUT -j LOG
 iptables -A INPUT -j DROP

# End message
echo " [End iptables rules setting]"
}

stop_firewall ()
{
#
# Set the default policy
#
 iptables -P INPUT ACCEPT
 iptables -P FORWARD ACCEPT
 iptables -P OUTPUT ACCEPT

#
# Set the default policy for the NAT table
#
 iptables -t nat -P PREROUTING ACCEPT
 iptables -t nat -P POSTROUTING ACCEPT
 iptables -t nat -P OUTPUT ACCEPT

#
# Delete all rules
#
 iptables -F
 iptables -t nat -F

#
# Delete all chains
#

 iptables -X
 iptables -t nat -X

# End message
echo " [End of flush]"
}


RETVAL=0

# To start the firewall
start() {
  echo -n "Iptables rules creation: "
  start_firewall
  RETVAL=0
}

# To stop the firewall
stop() {
  echo -n "Removing all iptables rules: "
  stop_firewall
  RETVAL=0
}

case $1 in
  start)
    start
    ;;
  stop)
    stop
    ;;
  restart)
    stop
    start
    ;;
  status)
    /sbin/iptables -L
    /sbin/iptables -t nat -L
    RETVAL=0
    ;;
  *)
    echo "Usage: firewall {start|stop|restart|status}"
    RETVAL=1
esac

exit
```


Note: If you are using modem, replace all eth0 references to ppp0 or the approriate value.


3. Make firewall excutable:

```
sudo chmod a+x /etc/init.d/firewall
```


4. Make a link for it in your startup folder:

```
sudo ln -s /etc/init.d/firewall /etc/rc2.d/S99firewall
```



Edit: To call the script without having to reboot type:

```
sudo /etc/init.d/firewall start
```

---

### Post by girtart3d on 2008-01-07
wow thanks alot for trying. but i dont think that did anything either. amule still wont connect. nor limewire.

---

### Post by p_quarles on 2008-01-07
Well, let's see if it is iptables. Post the output of this:
```
sudo iptables -L -v
```
That'll give a list of all currently enforced rules, regardless of what tool you used to set them up.

---

### Post by capink on 2008-01-07
The script above has a field for amule. But it is commented (i.e inactive). Have you uncommented it?

To allow amule uncomment the three line blew "# Allow amule" by removing the preceding "#". And replace the port number 4662 with the number you want to use.

---

### Post by girtart3d on 2008-01-07
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 
    0     0 ACCEPT     tcp  --  any    any     dslrouter            anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN
   52  5495 ACCEPT     udp  --  any    any     dslrouter            anywhere    
    0     0 ACCEPT     tcp  --  any    any     dslrouter            anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN
    0     0 ACCEPT     udp  --  any    any     dslrouter            anywhere    
    0     0 ACCEPT     0    --  lo     any     anywhere             anywhere    
  142  5112 ACCEPT     icmp --  any    any     anywhere             anywhere            limit: avg 10/sec burst 5
    0     0 DROP       0    --  eth0   any     anywhere             255.255.255.255
    0     0 DROP       0    --  any    any     anywhere             255.255.255.255
    0     0 DROP       0    --  any    any     BASE-ADDRESS.MCAST.NET/8  anywhere
    0     0 DROP       0    --  any    any     anywhere             BASE-ADDRESS.MCAST.NET/8
    0     0 DROP       0    --  any    any     255.255.255.255      anywhere    
    0     0 DROP       0    --  any    any     anywhere             localhost   
    0     0 DROP       0    --  any    any     anywhere             anywhere            state INVALID
    0     0 LSI        0    -f  any    any     anywhere             anywhere            limit: avg 10/min burst 5
11129   14M INBOUND    0    --  eth0   any     anywhere             anywhere    
    0     0 LOG_FILTER  0    --  any    any     anywhere             anywhere   
    0     0 LOG        0    --  any    any     anywhere             anywhere            LOG level info prefix `Unknown Input'

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            limit: avg 10/sec burst 5
    0     0 LOG_FILTER  0    --  any    any     anywhere             anywhere   
    0     0 LOG        0    --  any    any     anywhere             anywhere            LOG level info prefix `Unknown Forward'

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 
    0     0 ACCEPT     tcp  --  any    any     gir                  dslrouter           tcp dpt:domain
   52  3453 ACCEPT     udp  --  any    any     gir                  dslrouter           udp dpt:domain
    0     0 ACCEPT     tcp  --  any    any     gir                  dslrouter           tcp dpt:domain
    0     0 ACCEPT     udp  --  any    any     gir                  dslrouter           udp dpt:domain
    0     0 ACCEPT     0    --  any    lo      anywhere             anywhere    
    0     0 DROP       0    --  any    any     BASE-ADDRESS.MCAST.NET/8  anywhere
    0     0 DROP       0    --  any    any     anywhere             BASE-ADDRESS.MCAST.NET/8
    0     0 DROP       0    --  any    any     255.255.255.255      anywhere    
    0     0 DROP       0    --  any    any     anywhere             localhost   
    0     0 DROP       0    --  any    any     anywhere             anywhere            state INVALID
 8069  765K OUTBOUND   0    --  any    eth0    anywhere             anywhere    
    0     0 LOG_FILTER  0    --  any    any     anywhere             anywhere   
    0     0 LOG        0    --  any    any     anywhere             anywhere            LOG level info prefix `Unknown Output'

Chain INBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination 
11123   14M ACCEPT     tcp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED
    2   152 ACCEPT     udp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:4662
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:4662
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:4672
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:4672
    4   966 LSI        0    --  any    any     anywhere             anywhere    

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination 

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination 
    4   966 LOG_FILTER  0    --  any    any     anywhere             anywhere   
    0     0 LOG        tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
    0     0 DROP       tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN
    0     0 LOG        tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
    0     0 DROP       tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
    0     0 LOG        icmp --  any    any     anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
    0     0 DROP       icmp --  any    any     anywhere             anywhere            icmp echo-request
    4   966 LOG        0    --  any    any     anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
    4   966 DROP       0    --  any    any     anywhere             anywhere    

Chain LSO (0 references)
 pkts bytes target     prot opt in     out     source               destination 
    0     0 LOG_FILTER  0    --  any    any     anywhere             anywhere   
    0     0 LOG        0    --  any    any     anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
    0     0 REJECT     0    --  any    any     anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination 
  142  5112 ACCEPT     icmp --  any    any     anywhere             anywhere    
 7605  745K ACCEPT     tcp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED
  322 15022 ACCEPT     0    --  any    any     anywhere             anywhere 

ok thats what i got.

---

### Post by nowshining on 2008-01-07
hi, ur problem is simple, what port are u using in limewire, u'll need to go into the settings and tell us what port or pick one, and u'll also need to allow UDP otherwise it won't work I think.

What script are u using, are u using arno-iptables-firewall?

---

### Post by nowshining on 2008-01-07
oh and also u may have to change the default port as some ISPs thward / block certain ports cutting off p2p traffic.

---

### Post by girtart3d on 2008-01-07
actually i dont have limewire anymore. i got frustrated earlier and uninstalled it , thinking it might have been a bad install. and now i cant install it back because this thing called 'cnr' where i downloaded it from before, says i have it but i really dont.  the only things i have now is amule and ktorrent.

---

### Post by p_quarles on 2008-01-07
> **girtart3d said:**
> actually i dont have limewire anymore. i got frustrated earlier and uninstalled it , thinking it might have been a bad install. and now i cant install it back because this thing called 'cnr' where i downloaded it from before, says i have it but i really dont.  the only things i have now is amule and ktorrent.
Let's see if capink's idea works for amule. Instead of running the entire script again, run the parts that specifically refer to amule:
```
sudo iptables -I INPUT 1 -i eth0 -p tcp --tcp-flags SYN,RST,ACK SYN --dport 4662 -m state --state NEW -j ACCEPT
sudo iptables -I INPUT 1 -i eth0 -p udp --dport 4662 -m state --state NEW -j ACCEPT
sudo iptables -A INPUT -p udp -m udp --dport 4662 -j ACCEPT
```

---

### Post by girtart3d on 2008-01-07
hmm. i dont htink so. heres what it says on amule. - 'no valid servers found' and 'not connected (kad:off)' . maybe i should try a different server? but i dont know how. i dont think this is fixable.

---

### Post by Hallvor on 2008-01-08
You have to add a serverlist. Try the one from peerates or gruk.org Use google or check my sig.

---

### Post by girtart3d on 2008-01-08
woah it worked. i added a different server and it connected. thanks alot!

---

