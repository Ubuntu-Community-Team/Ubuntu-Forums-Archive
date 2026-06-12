---
title: "Use wlan usb dongle as access point?"
date: 2006-07-09
forum: General Help
---

### Post by RacerII on 2006-07-09
Is it possible to set up my wlan usb dongle as an access point on my dapper machine?

And how do i get started?

The wlan usb dongle is recognized:

eth0      Link encap:Ethernet  HWaddr 00:02:44:50:82:86
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:44ff:fe50:8286/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1528483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1463381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1057205889 (1008.2 MiB)  TX bytes:934116675 (890.8 MiB)
          Interrupt:233 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35022 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2064376 (1.9 MiB)  TX bytes:2064376 (1.9 MiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:172.16.55.1  Bcast:172.16.55.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.114.1  Bcast:192.168.114.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0E:2E:57:DC:8D
          inet6 addr: fe80::20e:2eff:fe57:dc8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



As you can see , my dapper machine is hooked up to a normal/ethernet router.
So i want to set my wlan0 interface as an access point , and forward it to eth0 i think?



Edit:
Got a little further

jasper@Dapper:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.

wlan0     802.11b/g NIC  ESSID:"pspap"
          Mode:Master  Frequency=2.412 GHz  Access Point: 00:0E:2E:57:DC:8D
          Bit Rate:1 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=40/92  Signal level=19/154  Noise level=161/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

But i still dont know how to "share internet"

Thanks in advance

---

### Post by RacerII on 2006-07-09
Ok i managed to get a little further again , but im not there yet.

iwconfig:

wlan0     802.11b/g NIC  ESSID:"pspap"
          Mode:Master  Frequency=2.412 GHz  Access Point: 00:0E:2E:57:DC:8D
          Bit Rate:11 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=76/92  Signal level=46/154  Noise level=161/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:02:44:50:82:86
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:44ff:fe50:8286/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6662 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12537549 (11.9 MiB)  TX bytes:752173 (734.5 KiB)
          Interrupt:233 Base address:0x4000



wlan0     Link encap:Ethernet  HWaddr 00:0E:2E:57:DC:8D
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe57:dc8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:866 (866.0 b)  TX bytes:3010 (2.9 KiB)


I can now connect to the wlan usb dongle , but cant access the internet.

On the device that i whish to connect trough my dapper box , i have these settings:

Ip address 192.168.1.3
Subnet mask 255.255.255.0
Default router 192.168.1.1
Primary DNS 192.168.1.1

But i keep getting a failed , when testing for an internet connection.

---

### Post by RacerII on 2006-07-10
I figured it out myself, heres how i got it working:

ifconfig wlan0 up
ip link set dev wlan0 up
iwconfig wlan0 channel 6
iwconfig wlan0 mode master
iwconfig wlan0 key bla
iwconfig wlan0 essid bla
iwconfig wlan0 channel 6
ifconfig eth0 0.0.0.0 up
ifconfig wlan0 0.0.0.0 up
brctl addbr br0
brctl addif br0 eth0
brctl addif br0 wlan0

ifconfig br0 up

dhcpcd br0

I needed the dhcpcd and brctl packages , and all works fine now.

---

