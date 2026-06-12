---
title: "network unreachable after automatic update"
date: 2006-08-29
forum: General Help
---

### Post by TDKBacke on 2006-08-29
Until a few days ago I had a perfectly working network consisting of two machines running kubuntu, a windows box and a "Eumex 300 IP" dsl router, which also functions as a dhcp server.
Suddenly one of the kubuntu boxes has no access to the LAN or Internet anymore. There are no answers to pings. "ifup eth0" results in a list of DHCPDISCOVER-messages followed by "send_packet: Network is down"

It's definately no hardware defect, since the problems are not present after booting with an knoppix live cd and I already tried another network adapter and cable. Also the other machines connected to the router work normally.

The last thing I did before this behaviour occured was a "Full Upgrade" in Adept. (I guess that's equivalent to an "apt-get dist-upgrade".)
Unfortunately I can't remember which packages were altered (is there a log file?).

Are there any known issues concerning the recent updates and networking?

---

### Post by orbital on 2006-08-29
I'm having the same problem with Ubuntu. No networking.

---

### Post by ubuntuanu on 2006-08-29
Probably it does not help anyone if I cry here about the same problem, but..
haven't been able to connect either since upgrading. Hardware's fine and network is not down, reboot isn't helping - don't know what to do, please help if you can.

--edit--
ifconfig gives the following output when booting with the Dapper Live Cd

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:19:20:39
          inet addr:88.112.236.114  Bcast:88.112.239.255  Mask:255.255.252.0
          inet6 addr: fe80::2c0:9fff:fe19:2039/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:950 errors:0 dropped:0 overruns:0 frame:0
          TX packets:925 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:761383 (743.5 KiB)  TX bytes:132332 (129.2 KiB)
          Interrupt:9 Base address:0x1c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

And when booting from hard drive:

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:19:20:39
          inet6 addr: fe80::2c0:9fff:fe19:2039/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0(0.0 b)  TX bytes:0 (0.0 KiB)
          Interrupt:9 Base address:0x1c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

Does someone have the solution? Even sudo ifdown -v --force eth0 didn't help this time. ](*,)

---

### Post by rpriha on 2006-08-31
> **ubuntuanu said:**
> Probably it does not help anyone if I cry here about the same problem, but..
haven't been able to connect either since upgrading. Hardware's fine and network is not down, reboot isn't helping - don't know what to do, please help if you can.

[...]

Does someone have the solution? Even sudo ifdown -v --force eth0 didn't help this time. ](*,)

For anyone experiencing the same issue, I took a quick look at ubuntuanu's laptop, the network problem was fixed by adding "acpi=noirq" in kernel boot options. ("acpi=off" is also a working solution if you're willing to live with that)

---

### Post by TDKBacke on 2006-09-01
Thanks for answering. Unfortunetly, neither acpi=noirq nor acpi=off helps in my case.

---

### Post by pcmacman on 2006-09-02
I'm having the same issue as well.  

After rebooting, I lost the ability to see either my wired (eth0) or wireless(eth1) connections in ifconfig.  I'm getting close to pulling my hair out over this.

---

### Post by scottme on 2006-09-03
Not sure if I have the same problem or a different one, but I just did an automatic upgrade from Breezy to the latest & greatest and I have stack of issues not least of which is that no network interface will come up. I can see eth0 in KControl, showing as disabled, but when I try to enable it, it very quickly pops back to disabled.

I also have a 3Com wireless card which was previously working perfectly that now will not come active.  Suspiciously, KControl shows it as eth2, but the system logs show that it gets recognized and configured as eth1.  What is going on here?

---

### Post by Agent_M on 2006-09-06
im having a simmilar problem, on my laptop it can connect to my router via wifi but it looks like it only has limited access or somthing strange, i can ping servers, i can traceroute but i cant load any pages, not connect with anything like gaim.

i managed to fix this somehow while messing around with settings on my router and laptop, that was on monday but it seems it was only temporary as its now not working. my laptop can connect to a diffrent router if i set it up and i can get onto a router at my dads fine.

in the mac address list of my router in the wifi section it shows the laptops mac address but doesnt list a host name or ip for my laptop.

ifconfig doesnt look iffy ether, my laptop has an ip and all that stuff so im really quite stuck as it works with other routers, but it was working perfectly fine before

---

### Post by chrisccoulson on 2006-09-10
I don't know whether my problem is related to this or not, but my loopback interface no longer comes up automatically. I only realised this as I was trying to debug why it was taking me several minutes to log in to a session. It turns out that the lack of loopback interface is causing this.

If I bring up the loopback interface using 'ifconfig lo up' in text mode, and then start GDM, i can log in fine.

Edit: It turns out my problem was unrelated to this and was actually due to /var/run not being mounted after moving my root partition yesterday

---

