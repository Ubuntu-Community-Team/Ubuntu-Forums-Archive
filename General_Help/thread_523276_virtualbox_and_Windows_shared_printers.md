---
title: "virtualbox and Windows shared printers"
date: 2007-08-11
forum: General Help
---

### Post by mykrob on 2007-08-11
Hey-
Running Kubuntu Feisty on a Dell Inspiron 6000. I have installed virtualbox so that the user can still use Microsoft Money. He needs to be able to see his physical network, but VirtualBox is giving him a "routed" address of 10.0.0.1.

How do i get the virtual machine to allow him to see his real network so he can access a printer and some file shares that are on a Windows machine?

Thanks,
-myk

---

### Post by mykrob on 2007-08-12
bump

---

### Post by strabes on 2007-08-12
Can't you enable the different network devices (eth0, eth1) in virtualbox so that you can connect to the internet/network on the virtual machine?

---

### Post by mykrob on 2007-08-12
I am able to access the internet with the virtual machine, but since it gets an IP address from a different subnet, I am unable to access any shares on the network.

---

### Post by JustAboutRealJAR on 2007-09-19
I've heard of people getting it to work with NAT but it didn't work for me.

Here's how I got it to work:

[LIST=1] Set up "Host Interface" as the Network Adapter[/LIST]

This is described very well for several distros in the [VirtualBox End User Documentation]("http://www.virtualbox.org/download/UserManual.pdf"), but I'm gonna copy/paste what you need to know for ubuntu (since this *is* Ubuntu forums)

> **6.5.1.1 Debian and Ubuntu hosts**
To set up a permanent host interface on a modern Debian or Ubuntu host, follow these
steps:

1. First install the bridge utilities (bridge-utils). package. You can do this from the command line as follows

```
$ sudo apt-get install bridge-utils
```

2. Next, you must add an entry to the file /etc/network/interfaces to describe the bridge. The following sample entry creates a bridge called br0, adds the host ethernet interface eth0 to it and tells it to obtain an IP address using DHCP so that the host remains able to access the network.

```
   auto br0
   iface br0 inet dhcp
         bridge_ports eth0
```

You will probably want to change this to suit your own networking needs. In particular, you may want to assign a static IP address to the bridge. You will find more documentation in the files

    a) /usr/share/doc/bridge-utilities/README.Debian.gz and
    b) /usr/share/doc/ifupdown/examples/network-interfaces.gz.


3. Restart networking on the host:

  ```
$ sudo /etc/init.d/networking restart
```

After this the bridge will remain on your system even after a restart.

4. Now, to create a permanent host interface called 'vbox0' (all host interfaces created in this way must be called 'vbox' followed by a number) and add it to the network bridge created above, use the following command (see chapter 6.5.1.5, Host Interface Networking utilities for Linux, page 68 for more details):

```
$ sudo VBoxAddIF vbox0 <user> br0
```

Replace <user> with the name of the user who is supposed to be able to use the new interface.

To tell VirtualBox to use the interface, select the virtual machine which is to use it in the main window of the VirtualBox application, configure one of its network adaptors to use Host Interface Networking (using “Settings”, “Network”, “Attached to”) and enter 'vbox0' into the “Interface name” field.
   
Alternatively, you can use the VBoxManage command line tool (in this example we are attaching the interface to the first network card of the virtual machine “My VM”):

```
$ VBoxManage modifyvm "My VM" -hostifdev1 vbox0
```


That probably seems like a lot, but you're not done!

[LIST=2]Chane permissions on vbox devices[/LIST]

It seems there's a bit of a bug here ([a bug report has been filed]("http://www.nabble.com/-Bug-33629--NEW:-virtualbox-requires-root-access-in-order-to-run-virtual-machines-t4450307.html"))

The solution is on bug report page, but here it is simple and condensed:

Create a group called vboxusers (this is usually already created by the virtualbox install but just make sure)
```

$ newgrp vboxusers

```

Add yourself to the group (replace <userid> with your user name):
```
$ sudo usermod -G vboxusers -a <userid>. 
```
Repeat as necessary for each user you want to be able to use virtual box

Change the permissions of these 2 critical files so that vboxusers can access them:
```
$ sudo chown root:vboxusers /dev/vboxdrv
$ sudo chown root:vboxusers /dev/net/tun
```

Now give vboxusers read and write access...
```
$ sudo chmod 0660 /dev/net/tun
$ sudo chmod 0660 /dev/vboxdrv
```

And you should be ready to go!

---

### Post by JustAboutRealJAR on 2007-09-19
PS - at Step 2 of the VirtualBox End User Documentation...
I chose to look up those readme files and such and here's what I added to my /etc/network/interfaces file:

```
auto br0

iface br0 inet static

    address 192.168.1.11

    network 192.168.1.0

    netmask 255.255.255.0

	bridge_ports eth0
```

This is a static IP address (which is what I wanted since I was also using this as a print server)

---

### Post by ssc351 on 2008-01-03
found an answer for you if you are still interested using NAT::

[http://forums.virtualbox.org/viewtopic.php?t=1465](http://forums.virtualbox.org/viewtopic.php?t=1465)

---

