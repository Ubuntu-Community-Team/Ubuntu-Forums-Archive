---
title: "problematic wifi belkin f5d6020v2"
date: 2005-10-15
forum: General Help
---

### Post by txcountymounty on 2005-10-15
here's hoping someone can help me. I have a belkin pcmcia wireless card model f5d6020 v 2. I cannot get this P.O.S working. kwifimanager shows me a big fat green line and tells me its scanning but it always tells me no networks found even though i know there are at least 4 going through my house. both encrypted and not. the lights blinnk like its doing something too.
*iwconfig* lists it with all 0's for access point.
will@ubuntu:/etc/init.d$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"linuxbox"
          Mode:Managed  Frequency:2.427 GHz  Access Point: FF:00:00:00:00:00
          Bit Rate:11 Mb/s
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

*ifconfig* says this:
will@ubuntu:/etc/init.d$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:20:C7:9B:C3
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:20ff:fec7:9bc3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1552142 (1.4 MiB)  TX bytes:721871 (704.9 KiB)
          Interrupt:11 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:30:BD:D1:F5:B2
          inet6 addr: fe80::230:bdff:fed1:f5b2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:49582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3697508 (3.5 MiB)  TX bytes:3697508 (3.5 MiB)

and *dmesg* said this (exerpt):
[4301095.210000]  [<c0102e9f>] sysenter_past_esp+0x54/0x75
[4301095.210000] handlers:
[4301095.210000] [<dcbe7164>] (service_interrupt+0x0/0x262 [atmel])
[4301095.210000] Disabling IRQ #3
[4301095.743000] eth1: MAC address 00:30:bd:d1:f5:b2
[4301095.743000] eth1: Atmel at76c50x wireless. Version 0.96 [email]simon@thekelleys.org.uk[/email]
[4301095.743000] eth1: Belkin F5D6020-V2 index 0x01: Vcc 5.0, irq 3, io 0x0100-0x011f
[4301106.363000] eth1: no IPv6 routers present
[4302177.990000] eth1: no IPv6 routers present
[4302236.977000] cs: IO port probe 0x100-0x4ff: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[4302236.981000] cs: IO port probe 0xc00-0xcf7: clean.
[4302236.982000] cs: IO port probe 0xa00-0xaff: clean.
[4302569.651000] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
[4302569.651000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[4302569.661000] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).

if someone knows something that I don't, and I don't know too much, please help. I also tried to install the atmelwlandriver but I keep getting this message when I try to do the "make" command
Building pcmf502r
        Debug
make[1]: Entering directory `/home/will/Downloads/atmelwlandriver/objs/pcmf502r/debug'
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: Entering an unknown directorymake: Leaving an unknown directorymake[1]: *** [all] Error 2
make[1]: Leaving directory `/home/will/Downloads/atmelwlandriver/objs/pcmf502r/debug'
make: *** [pcmf502r] Error 2
will@ubuntu:~/Downloads/atmelwlandriver$

---

### Post by samjam on 2005-10-15
Can you post your /etc/network/interfaces?

Mine has the releevant section:
> 
iface wlan0 inet dhcp
wireless-essid MYESSIT
wireless-key mykeyinhexadecimal

auto wlan0


I have the same card, but am using the ndis wrappersm and *specific*windows* drivers which I could send, although I plan to give the amtel stuff a go one day.

---

### Post by txcountymounty on 2005-10-18
Im not on my laptop now but will post that as soon as i can. I tried using Ndiswrapper but could never find the proper inf file, its a good posibility I dont know what im doing.

---

### Post by txcountymounty on 2005-10-18
here what /etc/network/interfaces had to say (essid and key changed to protect the innocent)
# The primary network interface
iface eth0 inet dhcp

iface eth1 inet static
address 192.168.1.104
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid xxxxxxx
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

"interfaces" 26L, 590C.

here is what i get when i use the Kwifimanager app.
[http://img.photobucket.com/albums/v650/Masticator/Screenshot.png](http://img.photobucket.com/albums/v650/Masticator/Screenshot.png)

---

### Post by txcountymounty on 2005-10-19
also i keep getting compile errors whe i try the atmelwlandriver. i have the windows intall disk for the card but i cant find any .inf or .sys files to use ndiswrapper on. are they stashed away in one of the .cab files. if anyone knows please let me know, that might solve the problem.

---

