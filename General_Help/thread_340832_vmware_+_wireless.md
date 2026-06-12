---
title: "vmware + wireless"
date: 2007-01-17
forum: General Help
---

### Post by Denn1s on 2007-01-17
Hello everyone, i have a win virtual machine and im trying to make it connect to the Internet through my wireless card (ath0), i cant seem to find instructions on how to do it, any help would be greatly appreciated, thank you all.

wath i have tried: select bridge connection and a warning pops up that says could not open /dev/vmnet0: no such file or directory virtual device Ethernet0 will start disconnected

---

### Post by Richard Kut on 2007-01-18
Hello Denn1s! I have the same setup at home, and it works as long as I select bridged networking in the VMware setup panel. I am not in front of my machine right now. I will try to update this post again tonight with some more specific details.

---

### Post by Richard Kut on 2007-01-20
OK, I don't recall the exact steps that I took to set up the bridged ethernet connection. my  However, here is what ifconfig output is like:

> richard@ubuntu:~/kxgenerator-0.3.7$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:90:4B:B7:F1:68
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12306 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14911991 (14.2 MiB)  TX bytes:1313209 (1.2 MiB)
          Interrupt:201 Memory:d0204000-d0206000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6412 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6412 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1157657 (1.1 MiB)  TX bytes:1157657 (1.1 MiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:10.1.1.1  Bcast:10.1.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Note the vmnet1 entry.

In the configuration settings of my virtual machine I have the network connection set to bridged.

Here are the contents of my /etc/vmware/config file:

> vmnet1.hostonlyaddress = "10.1.1.1"
serverd.init.fullpath = "/usr/lib/vmware/serverd/init.pl"
authd.client.port = "902"
control.fullpath = "/usr/bin/vmware-cmd"
authd.fullpath = "/usr/sbin/vmware-authd"
loop.fullpath = "/usr/bin/vmware-loop"
libdir = "/usr/lib/vmware"
vmware.fullpath = "/usr/bin/vmware"
vmnet1.hostonlynetmask = "255.255.255.0"
vmdir = "/var/lib/vmware/Virtual Machines"
dhcpd.fullpath = "/usr/bin/vmnet-dhcpd"
serverd.fullpath = "/usr/sbin/vmware-serverd"

datastore.name = "local"

datastore.localpath = "/var/lib/vmware/Virtual Machines/"


From what I can recall, these settings are created when you run the /usr/bin/vmware-config.pl script.

I hope that this helps. Let me know how it goes, and good luck!

---

### Post by Redeyes_Gambit on 2007-01-26
I'm having the same issue and the config script doesn't work. I have also tried configuring the card inside VMWare with no change.

The wireless connection worked before I upgraded to edgy.

---

### Post by Richard Kut on 2007-01-26
Did you run the vmware-config.pl command to configure the vmnet interfaces?

---

### Post by Redeyes_Gambit on 2007-01-27
Yup. Repeatedly. The error I get when configing reads: 

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Bridged networking on /dev/vmnet2                                  failed
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

vmnet2 is my wireless. I accept all default options when running the config script.

---

### Post by Richard Kut on 2007-01-28
Maybe you had previously installed vmware-player, and then later switched to vmware-server? If so,  ensure that the old vmware-player file /etc/init.d/vmware-player is gone, or it will be started on bootup. To remove the file:

$sudo update-rc.d -f vmware-player remove

Also, be sure to remove /etc/vmware/not_configured, if it exists, before you reboot.
This will prevent vmware-player from being started at boot time and on next reboot, vmware should be starting just fine.

---

### Post by Denn1s on 2007-01-29
thanks for your answers, ill try to get my setup as yours, ill tell you later how this goes, thank you very much for your help

---

### Post by Redeyes_Gambit on 2007-01-30
Well, you were right when you thought I had installed VMWare player. I had, but later removed it. The init.d had entries for the player (I hate it when an un-install script leaves peices) which I removed per your specifications. I also removed the not_configured file which I have to do anyway (it keeps putting it back.) I then restarted and ran the config script again but got the same error.

---

### Post by Richard Kut on 2007-01-30
OK Redeyes_Gambit, you've got me stumped! Have you tried the free help forums offered by VMware? Maybe they could give you better guidance than I can. Try going to:

[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

I am sorry that I could not be of more help to you. Good luck in your search for a solution.

Please consider posting what you did to fix the problem here in the forums so that others might benefit from your experience. Thanks!

---

### Post by StarkD on 2007-05-01
> **Redeyes_Gambit said:**
> 
   Bridged networking on /dev/vmnet2                                  failed


I had the same problem. It helped to inactivate the wireless in the network manager. I reran the config script without any errors.

Now I can start VMware but I still have no Internet connection in Windows. So I do not have any complaints but I get no IP or anything in Windows. Any idea what to do?

---

### Post by Psyklops on 2007-08-12
> **StarkD said:**
> I had the same problem. It helped to inactivate the wireless in the network manager. I reran the config script without any errors.

Now I can start VMware but I still have no Internet connection in Windows. So I do not have any complaints but I get no IP or anything in Windows. Any idea what to do?

I had the same problem setting up my system over a wireless connection.  I'm running Feisty and VMware workstation 6.0.

I ended up configuring NAT for my Vmachines with VMware doing DHCP.

I still have the not_configured issue with VMware which I can resolve by deleting it prior to firing up VMware.  Any fixes?

---

