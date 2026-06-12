---
title: "Ubuntu 16.04 - Qualcomm Atheros Killer E220x - Slow download &amp; upload speed"
date: 2019-05-08
forum: General Help
---

### Post by alexclander on 2019-05-08
Hello Ubuntu forums,

I am encountering slow download & upload speeds with a freshly installed ubuntu 16.04 server.

I have tried to troubleshoot the problem with help of my ignorance and google searches, but that wasn't enough. Therefore I come here for your help.

Output for: ```
lspci | awk '/[Nn]et/ {print $1}' | xargs -i% lspci -ks %
```

```
02:00.0 Ethernet controller: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller (rev 13)        Subsystem: Micro-Star International Co., Ltd. [MSI] Killer E220x Gigabit Ethernet Controller
        Kernel driver in use: alx
        Kernel modules: alx

```

Output for: ```
ifconfig -a
``` (I changed default value from MTU 1500 (doesn't seem to have helped))

```
enp2s0    Link encap:Ethernet  HWaddr d8:cb:8a:c0:3d:47          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:103739 errors:0 dropped:38 overruns:0 frame:0
          TX packets:67333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:84543706 (84.5 MB)  TX bytes:13110312 (13.1 MB)
          Interrupt:19


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:12340 (12.3 KB)  TX bytes:12340 (12.3 KB)

```

Output for: ```
lsmod
```

```
Module                  Size  Used bysnd_hda_codec_hdmi     53248  1
intel_rapl             20480  0
snd_hda_codec_realtek    90112  1
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
coretemp               16384  0
kvm_intel             176128  0
kvm                   552960  1 kvm_intel
snd_hda_intel          40960  0
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
irqbypass              16384  1 kvm
snd_hda_core           77824  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
serio_raw              16384  0
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_timer              32768  1 snd_pcm
mei_me                 36864  0
snd                    81920  8 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
mei                    98304  1 mei_me
soundcore              16384  1 snd
shpchp                 36864  0
intel_smartconnect     16384  0
acpi_pad               24576  0
lpc_ich                24576  0
8250_fintek            16384  0
mac_hid                16384  0
ib_iser                49152  0
rdma_cm                49152  1 ib_iser
iw_cm                  45056  1 rdma_cm
ib_cm                  49152  1 rdma_cm
ib_sa                  36864  2 rdma_cm,ib_cm
ib_mad                 49152  2 ib_cm,ib_sa
ib_core               106496  6 rdma_cm,ib_cm,ib_sa,iw_cm,ib_mad,ib_iser
ib_addr                20480  2 rdma_cm,ib_core
iscsi_tcp              20480  0
libiscsi_tcp           24576  1 iscsi_tcp
libiscsi               53248  3 libiscsi_tcp,iscsi_tcp,ib_iser
scsi_transport_iscsi   102400  4 iscsi_tcp,ib_iser,libiscsi
autofs4                40960  2
btrfs                 987136  0
raid10                 49152  0
raid456               106496  0
async_raid6_recov      20480  1 raid456
async_memcpy           16384  2 raid456,async_raid6_recov
async_pq               16384  2 raid456,async_raid6_recov
async_xor              16384  3 async_pq,raid456,async_raid6_recov
async_tx               16384  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
xor                    24576  2 btrfs,async_xor
raid6_pq              102400  4 async_pq,raid456,btrfs,async_raid6_recov
libcrc32c              16384  1 raid456
raid1                  40960  0
raid0                  20480  0
multipath              16384  0
linear                 16384  0
i915                 1232896  2
mxm_wmi                16384  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        155648  1 i915
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
syscopyarea            16384  1 drm_kms_helper
aesni_intel           167936  0
sysfillrect            16384  1 drm_kms_helper
aes_x86_64             20480  1 aesni_intel
sysimgblt              16384  1 drm_kms_helper
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
fb_sys_fops            16384  1 drm_kms_helper
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
psmouse               131072  0
ahci                   40960  3
drm                   364544  3 i915,drm_kms_helper
alx                    36864  0
libahci                32768  1 ahci
mdio                   16384  1 alx
wmi                    20480  1 mxm_wmi
video                  40960  1 i915
fjes                   28672  0

```

Output for: ```
route -n
```

```
Kernel IP routing tableDestination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 enp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 enp2s0

```

Output for: ```
cat /etc/resolv.conf
```

```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 1.1.1.1
nameserver 8.8.8.8

```

Speedtest result: ```
~$ speedtest-cliRetrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from Telefonica de Espana (XX.XXX.XX6.61)...
Selecting best server based on latency...
Hosted by Vodafone ES (Madrid) [16.01 km]: 2514.771 ms
Testing download speed........................................
Download: 8.05 Mbit/s
Testing upload speed..................................................
Upload: 3.08 Mbit/s



```

Spedtest from my desktop, same network:

[IMG]https://i.imgur.com/T8qKnNX.png[/IMG]

iperf test:

```
$ iperf -c 192.168.1.8
------------------------------------------------------------
Client connecting to 192.168.1.8, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.6 port 32796 connected with 192.168.1.8 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  1.08 GBytes   928 Mbits/sec



```

Would highly appreciate any help received. I discard being a cable problem, already tried with different cat5e-cat6 cables, also tried different sockets from the switch.

Kind regards,

---

### Post by rsteinmetz70112 on 2019-05-08
Good luck, I had a similar problem with the same chip but it went away when I upgraded to 18.04.

Have you checked the speed on you local network?

---

### Post by alexclander on 2019-05-08
> **rsteinmetz70112 said:**
> Good luck, I had a similar problem with the same chip but it went away when I upgraded to 18.04.

Have you checked the speed on you local network?

Hello rteinmetz70112,

Maybe I'll try to update to 18.04, I haven't made any tests over LAN, what kidn of test would you sugest?

I have tried iperf and this is the result:

```
iperf -c 192.168.1.8------------------------------------------------------------
Client connecting to 192.168.1.8, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.6 port 32796 connected with 192.168.1.8 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  1.08 GBytes   928 Mbits/sec



```

Kind regards,

---

### Post by alexclander on 2019-05-09
Changed my primary DNS from 1.1.1.1 to 8.8.8.8 and my internet connection seems to work again... (more or less)

```
Retrieving speedtest.net configuration...Retrieving speedtest.net server list...
Testing from Telefonica de Espana (XX.XXX.XXX.61)...
Selecting best server based on latency...
Hosted by Vodafone ES (Alcobendas) [1.96 km]: 9.416 ms
Testing download speed........................................
Download: 599.03 Mbit/s
Testing upload speed..................................................
Upload: 102.28 Mbit/s



```

---

