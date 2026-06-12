---
title: "Qemu &amp; Networking"
date: 2007-05-28
forum: General Help
---

### Post by CHUCKYCHUCK on 2007-05-28
Hi !
I'm using Qemu with nat networking, meaning that from inside the guest os i can connect to the internet, but this guest os can't be accessed from the outside ( don't have his own ip, can't run a test server for example )

I would like to know how can i enable a "real" networking between the guest Os and the host/internet, ( i would like to access the guest os with ssh, and test the guest's apache from the outside )

i read some documentation about qemu and "tuntap", but it's not very very clear, if you know precisely how to do that
( i have a Wifi card, wep-encrypted, with ndiswrapper )

thanks in advance

---

### Post by CHUCKYCHUCK on 2007-05-29
help me please :)

---

### Post by bronson on 2007-05-30
This is a very difficult question to answer.  A good intro is [http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC25](http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC25) and I've put some notes up here: [http://wiki.u32.net/KVM#Networking](http://wiki.u32.net/KVM#Networking)

---

### Post by mitko_ on 2007-05-30
The best solution is to set up a bridge on your host OS (you will need the bridge-utils package) and then run the guest OS with tun/tap interface. What you have to do is, add your network interface and the tun/tap interface to the same bridge.

Here is a script I use to add an interface to a bridge:

```

#!/bin/bash

BR=$1
ETH=$2

BRCTL=`which brctl`
IFDOWN=`which ifdown`
IFCONFIG=`which ifconfig`
DHCP=`which dhclient`


if [ `id -u` -gt 0 ]; then
    echo "Need root permissions to run."
    exit 1
fi

echo "***Taking $ETH down..."
$IFDOWN $ETH

echo "***Adding bridge $BR ..."
$BRCTL addbr $BR

echo "***Adding $ETH to $BR ..."
$BRCTL addif $BR $ETH

echo "***Bringing $ETH up... "
$IFCONFIG $ETH up

echo "***Configuring bridge with DHCP..."
$DHCP $BR

sleep 2

echo "$0 is done!"

```

The usage is:
```

./bridge.sh br0 eth0 
[start your virtual OS with the *-net nic -net tap* parameters]
./bridge br0 tap0

```

I assume here that you have saved the script with the bridge.sh filename, and the network interface which you want to share with your guest is eth0. If you start another guest OS with the *-net nic -net tap* parameters add the new interface to the bridge with ./bridge br0 tap0.

I got a lot of help from [this thread]("http://qemu-forum.ipi.fi/viewtopic.php?t=144&highlight=bridge+tap") from the qemu forums.

This way you should get "full networking" working, and your guest OS will have its own external IP address.

[COLOR="Red"]**NOTE:**[/COLOR] There is a problem when bridging a WiFi connection, which you may or may not experience. More about this problem, and a way around it, you can find [here]("http://www.linuxquestions.org/questions/showthread.php?t=472402").

Hope this will help.

---

