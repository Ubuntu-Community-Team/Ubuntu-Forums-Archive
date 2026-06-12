---
title: "Sharing files in VrtualBox"
date: 2008-06-03
forum: General Help
---

### Post by coubury on 2008-06-03
Im running xp on virtualBox and im looking to take a folder from xp and put it in Ubuntu

how do i do this?

Thanks

---

### Post by Brucevdk on 2008-06-04
Documentation used:
[LIST]
[*][VirtualBox  - Networking - Community Ubuntu Documentation]("https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03")
[/LIST]

Note that the configuration I present below (and personally use) is based upon the before mentioned documentation but differs quite significantly in certain aspects. It might not be The Right Way (TM) to go about things but in the end it'll still allow network communication between the host and the guest machine (Microsoft Windows XP in your case) and vice versa (and other networks, e.g. the Internet). If you encounter any problems be sure to reply to this thread.

***The first few steps here are directly taken from the documentation.*** To start, NAT is by far the easiest way to get your guests connected to the interweb, but you may want to use the guests as servers, for this you need Host Networking. You will need to install bridge-utils and uml-utilities so that you can make a tap device and add it to a bridge.

```
sudo apt-get install bridge-utils uml-utilities 
```

Now make a bridge, and put your current interface into it:

```
sudo tunctl -t tap1 -u fred # where fred is the user you will be running vbox as
sudo chown root.vboxusers /dev/net/tun
sudo chmod g+rw /dev/net/tun
```

Set the permission to persist across reboots, by editing as root /etc/udev/rules.d/20-names.rules and changing:

```
KERNEL=="tun",                          NAME="net/%k" 
```

to

```
KERNEL=="tun",                          NAME="net/%k",  GROUP="vboxusers",     MODE="0660" 
```

***This is where the procedure differs from the documentation.*** Edit rc.local to configure the network devices on restart:
```

# create a tap
tunctl -t tap1 -u fred # where fred is the user you will be running vbox as
ip link set up dev tap1

# create the bridge
brctl addbr br0
brctl addif br0 tap1

# set the IP address and routing
ip link set up dev br0
ip addr add 10.1.1.1/24 dev br0
ip route add 10.1.1.0/24 dev br0

```

To allow the guest to access other interfaces (e.g. go out on the Internet) edit */etc/sysctl.conf* to enable IP forwarding (and make it permanent), add the following line to the end of the file:
```
net.ipv4.ip_forward=1
```

You'll have to setup everything (since you probably don't want to restart):
```

sudo /etc/rc.local
sudo sysctl -p

```

Now all that remains is setting up the netwerk settings in the VirtualBox manager (Settings -> Network -> Attached to (Host Interface) -> Interface name (tap1)) and the guest itself (static IP configuration).

---

### Post by Brucevdk on 2008-06-18
[Cross posted here.](http://ubuntuforums.org/showthread.php?t=817587) 

I'll let my "solution" here stand, even though it's probably too technical (compared to VirtualBox Guest Additions + Shared Folders [as described in post #3 on that thread](http://ubuntuforums.org/showpost.php?p=5109222&postcount=3)).

---

