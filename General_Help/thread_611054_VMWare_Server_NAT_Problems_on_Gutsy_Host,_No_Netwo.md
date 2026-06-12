---
title: "VMWare Server NAT Problems on Gutsy Host, No Network for VM"
date: 2007-11-12
forum: General Help
---

### Post by superbrose on 2007-11-12
[SIZE="3"]I have been trying to connect my VM to the network, without success. I am using a Gusty host (kernel 2.6.22-14-generic) with vmware server 1.0.4 build-56528, and Windows XP Pro SP2 guest.

After installing vmware server, the network connection on the host somehow split into two, on my Gutsy laptop (1 wireless adapter, 1 wired): One interface only worked for IP addresses within the LAN, the other only worked for requests outside it!

Using route I found that my default route had somehow been removed, so I added it again. Now both network interfaces work for LAN and Internet, but I am still unable to connect the VMs to the network. It appears that the vmware DHCP client does not work, or at least does not communicate with the VM, as it does not receive an IP address. I even tried configuring the VM's IP address manually within the Guest OS, but even setting a static address I cannot connect the VM to the network. I think it must also be a routing issue.[/SIZE] :confused:

[SIZE="3"]The VM is configured to use NAT, vmnet8. I want to connect through eth1, the wirless adapter, which in the vmware server config is set up as a bridge:[/SIZE]

```
$ ps ax | grep bridge
6428 pts/0 S 0:00 /usr/bin/vmnet-bridge -d /var/run/vmnet-bridge-0.pid /dev/vmnet0 eth1
```

[SIZE="3"]This is my routing information:[/SIZE]

```
$ route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
172.16.39.0 * 255.255.255.0 U 0 0 0 vmnet1
localnet * 255.255.255.0 U 0 0 0 eth1
172.16.61.0 * 255.255.255.0 U 0 0 0 vmnet8
169.254.0.0 * 255.255.0.0 U 1000 0 0 eth1
default 192.168.1.1 0.0.0.0 UG 100 0 0 eth1
```
[SIZE="3"]
This is the output from starting the vmware network services:[/SIZE]

```
# /usr/lib/vmware/net-services.sh restart
Bridged networking on /dev/vmnet0 done
DHCP server on /dev/vmnet1 done
Host-only networking on /dev/vmnet1 done
DHCP server on /dev/vmnet8 done
NAT service on /dev/vmnet8 done
Host-only networking on /dev/vmnet8 done
Bridged networking on /dev/vmnet0 done
Host-only networking on /dev/vmnet1 (background) done
Host-only networking on /dev/vmnet8 (background) done
NAT service on /dev/vmnet8 done
```

[SIZE="3"]Output from ifconfig, with eth0 unplugged as usual:[/SIZE]

```
$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:13:A9:C1:08:C1
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:16

eth1 Link encap:Ethernet HWaddr 00:1B:77:1D:2D:1F
inet addr:192.168.1.124 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::21b:77ff:fe1d:2d1f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1621 errors:11 dropped:31 overruns:0 frame:0
TX packets:744 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:255755 (249.7 KB) TX bytes:103378 (100.9 KB)
Interrupt:18 Base address:0xc000 Memory:fa000000-fa000fff

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:43 errors:0 dropped:0 overruns:0 frame:0
TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:5768 (5.6 KB) TX bytes:5768 (5.6 KB)

vmnet1 Link encap:Ethernet HWaddr 00:50:56:C0:00:01
inet addr:172.16.39.1 Bcast:172.16.39.255 Mask:255.255.255.0
inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

vmnet8 Link encap:Ethernet HWaddr 00:50:56:C0:00:08
inet addr:172.16.61.1 Bcast:172.16.61.255 Mask:255.255.255.0
inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
```

[SIZE="3"]Apart from networking the Guest OS works perfectly, resolution, sound and USB. Any help is **[SIZE="4"]much[/SIZE]** appreciated![/SIZE]

PS: I think the problem I am having has been described before at [this thread (ubuntuforums.org)]("http://ubuntuforums.org/showthread.php?t=415841"), but it seems to have become stale without a solution... I also posted this problem at the [vmware forum (vmware.com)]("http://communities.vmware.com/thread/112331?tstart=0"), but no answers from there yet.

PPS: My vmx file:
```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4"
scsi0.present = "TRUE"
memsize = "512"
ide0:0.present = "TRUE"
ide0:0.fileName = "Windows XP Professional.vmdk"
ide0:0.writeThrough = "TRUE"
ide1:0.present = "TRUE"
ide1:0.fileName = "/dev/scd0"
ide1:0.deviceType = "cdrom-raw"
floppy0.startConnected = "FALSE"
floppy0.fileName = "/dev/fd0"
Ethernet0.present = "TRUE"
Ethernet0.connectionType = "nat"
displayName = "Windows XP Professional"
guestOS = "winxppro"
priority.grabbed = "normal"
priority.ungrabbed = "normal"
powerType.powerOff = "hard"
powerType.powerOn = "hard"
powerType.suspend = "hard"
powerType.reset = "hard"

floppy0.present = "FALSE"

annotation = "Windows XP Professional SP2."

ide0:0.redo = ""
ide1:0.startConnected = "TRUE"
ethernet0.addressType = "generated"
uuid.location = "56 4d 32 6b 25 2c 66 1a-dc 18 58 77 88 8c ff 5f"
uuid.bios = "56 4d 32 6b 25 2c 66 1a-dc 18 58 77 88 8c ff 5f"
ethernet0.generatedAddress = "00:0c:29:8c:ff:5f"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"

sound.present = "TRUE"
sound.fileName = "-1"
sound.autodetect = "TRUE"

sound.virtualDev = "es1371"

usb.present = "TRUE"
usb.generic.autoconnect = "FALSE"

scsi0:0.present = "FALSE"
scsi0:0.deviceType = "scsi-passthru"
scsi0:0.fileName = "/dev/sdb1"

usb.autoConnect.device0 = ""
usb.autoConnect.device1 = ""
```

---

### Post by superbrose on 2007-11-14
[SIZE="3"]I decided to uninstall vmware server and then reinstall it. That somehow did the trick, although I did not change the configuration at all!

Now there is one minor problem left - DNS resolution does not work for some reason. I can ping IP addresses of FQDNs from the VM, but ping fails if I use only the FQDN. It seems like vmware server does not use the DNS servers of the host.

Also, occasionally the sound card does not work, even though there are no problems on the host. I get the error "failed to open /dev/dsp".[/SIZE]

---

