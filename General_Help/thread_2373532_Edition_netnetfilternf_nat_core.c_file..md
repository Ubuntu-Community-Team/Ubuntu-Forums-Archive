---
title: "Edition net/netfilter/nf_nat_core.c file."
date: 2017-10-07
forum: General Help
---

### Post by smithbox on 2017-10-07
My desktop - Ubuntu 16.10.
Kernel:
```
uname -r
4.8.0-59-generic
```
Currently loaded modules:
```
lsmod
Module                  Size  Used by
bnep                   20480  2
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
xt_multiport           16384  1
tcp_diag               16384  0
inet_diag              20480  1 tcp_diag
nfnetlink_queue        24576  0
bluetooth             552960  7 bnep
bridge                139264  0
stp                    16384  1 bridge
llc                    16384  2 bridge,stp
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               454656  3 vboxnetadp,vboxnetflt,vboxpci
nfnetlink_log          20480  1
ipt_MASQUERADE         16384  15
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
joydev                 20480  0
input_leds             16384  0
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 24576  2 nf_nat_masquerade_ipv4,nf_nat_ipv4
xt_CHECKSUM            16384  7
xt_tcpudp              16384  16
snd_emu10k1           159744  4
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
snd_util_mem           16384  1 snd_emu10k1
sparse_keymap          16384  1 asus_wmi
snd_ac97_codec        131072  1 snd_emu10k1
iptable_mangle         16384  1
binfmt_misc            20480  1
snd_rawmidi            32768  1 snd_emu10k1
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
kvm_amd                73728  0
snd_hda_intel          36864  6
kvm                   598016  1 kvm_amd
snd_hda_codec         135168  3 snd_hda_intel,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           86016  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_generic,snd_hda_codec_realtek
irqbypass              16384  1 kvm
snd_seq_device         16384  2 snd_emu10k1,snd_rawmidi
snd_hwdep              16384  2 snd_emu10k1,snd_hda_codec
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
ac97_bus               16384  1 snd_ac97_codec
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
snd_pcm               110592  5 snd_hda_intel,snd_emu10k1,snd_hda_codec,snd_hda_core,snd_ac97_codec
ablk_helper            16384  1 aesni_intel
snd_timer              32768  2 snd_emu10k1,snd_pcm
emu10k1_gp             16384  0
snd                    86016  31 snd_hda_intel,snd_emu10k1,snd_hwdep,snd_hda_codec,snd_ac97_codec,snd_timer,snd_rawmidi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
cryptd                 24576  3 ablk_helper,ghash_clmulni_intel,aesni_intel
shpchp                 36864  0
tpm_infineon           20480  0
soundcore              16384  1 snd
gameport               16384  2 emu10k1_gp
serio_raw              16384  0
k10temp                16384  0
fam15h_power           16384  0
i2c_piix4              24576  0
mac_hid                16384  0
nf_conntrack_ipv6      20480  1
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_ipv4      16384  10
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  10
nf_log_ipv4            16384  4
nf_log_common          16384  1 nf_log_ipv4
xt_LOG                 16384  4
xt_limit               16384  3
iptable_filter         16384  1
nf_conntrack_netlink    40960  0
nf_conntrack          114688  7 nf_conntrack_ipv6,nf_conntrack_ipv4,nf_conntrack_netlink,nf_nat_masquerade_ipv4,xt_conntrack,nf_nat_ipv4,nf_nat
nfnetlink              16384  4 nfnetlink_log,nfnetlink_queue,nf_conntrack_netlink
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  3 iptable_mangle,iptable_filter,iptable_nat
x_tables               36864  14 xt_LOG,xt_multiport,ipt_REJECT,iptable_mangle,ip_tables,ebtables,iptable_filter,xt_tcpudp,ipt_MASQUERADE,xt_limit,xt_CHECKSUM,ip6table_filter,xt_conntrack,ip6_tables
autofs4                40960  2
pata_acpi              16384  0
hid_logitech_hidpp     28672  0
hid_logitech_dj        20480  0
hid_generic            16384  0
usbhid                 53248  0
hid                   118784  5 hid_generic,usbhid,hid_logitech_dj,hid_logitech_hidpp
nouveau              1572864  7
mxm_wmi                16384  1 nouveau
video                  40960  2 asus_wmi,nouveau
psmouse               139264  0
i2c_algo_bit           16384  1 nouveau
ttm                   102400  1 nouveau
drm_kms_helper        167936  1 nouveau
pata_atiixp            16384  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   368640  10 nouveau,ttm,drm_kms_helper
ahci                   36864  1
r8169                  81920  0
libahci                32768  1 ahci
mii                    16384  1 r8169
fjes                   28672  0
wmi                    16384  3 asus_wmi,mxm_wmi,nouveau
```
```
modinfo iptable_nat
filename:       /lib/modules/4.8.0-59-generic/kernel/net/ipv4/netfilter/iptable_nat.ko
license:        GPL
srcversion:     1F0CF39D3A7E66C295AA4FE
depends:        ip_tables,nf_nat_ipv4
intree:         Y
vermagic:       4.8.0-59-generic SMP mod_unload modversions 


```Loaded NAT module:
```
lsmod | grep nat
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 24576  2 nf_nat_masquerade_ipv4,nf_nat_ipv4
nf_conntrack          114688  7 nf_conntrack_ipv6,nf_conntrack_ipv4,nf_conntrack_netlink,nf_nat_masquerade_ipv4,xt_conntrack,nf_nat_ipv4,nf_nat
ip_tables              28672  3 iptable_mangle,iptable_filter,iptable_nat

```
Help:
```
The generic NAT module is net/netfilter/nf_nat_core.c
```
Question:
Howto find and edit with nano " nf_nat_core.c " file ?

---

### Post by mörgæs on 2017-10-07
First of all your Ubuntu release (16.10) is unsupported. I recommend that you begin with a fresh install of 17.04. 

When that is working people are ready to help with the NAT questions.

---

### Post by Doug S on 2017-10-07
> **smithbox said:**
> 
Question:
Howto find and edit with nano " nf_nat_core.c " file ?that file is part of the kernel source code. It is a fairly large file, and not something you should need to edit, nor should you if you are not comfortable making changes to and compiling the kernel. Perhaps tell us why you think you need to edit that file.

---

### Post by smithbox on 2017-10-07
@[**[COLOR=#DD4814][B]mörgæs**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=939075")
> First of all your Ubuntu release (16.10) is unsupported. I recommend that you begin with a fresh install of 17.04.
What do you think about Kernel compilation ?


@Doug S
I study packets traversing in Kernel (NAT, SNAT, DNAT).
To understand it correctly I need to get access to " nf_nat_core.c " file.

Ubuntu 17.04 Zesty Zapus installed:
```
cat /etc/issue
Ubuntu 17.04 \n \l
```
```
uname -r
4.10.0-19-generic
```
Loaded Kernel modules:
```
lsmod|grep -E "nf_|xt_|ip"
nf_nat_ftp             16384  0
nf_conntrack_ftp       20480  1 nf_nat_ftp
iptable_nat            16384  0
nf_conntrack_ipv4      16384  1
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_ftp,nf_nat_ipv4
nf_conntrack          131072  5 nf_conntrack_ftp,nf_conntrack_ipv4,nf_nat_ftp,nf_nat_ipv4,nf_nat
libcrc32c              16384  1 nf_nat
ip_tables              24576  1 iptable_nat
x_tables               36864  1 ip_tables

```
```
lsmod|grep 'ipt'
iptable_nat            16384  0
nf_nat_ipv4            16384  1 iptable_nat
ip_tables              24576  1 iptable_nat
```
```
lsmod | grep nat
nf_nat_ftp             16384  0
nf_conntrack_ftp       20480  1 nf_nat_ftp
iptable_nat            16384  0
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_ftp,nf_nat_ipv4
nf_conntrack          131072  6 nf_conntrack_ftp,nf_conntrack_ipv4,nf_nat_ftp,xt_conntrack,nf_nat_ipv4,nf_nat
libcrc32c              16384  1 nf_nat
ip_tables              24576  2 iptable_filter,iptable_nat
```

```
modinfo iptable_nat
filename:       /lib/modules/4.10.0-19-generic/kernel/net/ipv4/netfilter/iptable_nat.ko
license:        GPL
srcversion:     1F0CF39D3A7E66C295AA4FE
depends:        ip_tables,nf_nat_ipv4
intree:         Y
vermagic:       4.10.0-19-generic SMP mod_unload 

```
Howto get access to " nf_nat_core.c " file?

---

### Post by mörgæs on 2017-10-07
> **smithbox said:**
> @[**[COLOR=#DD4814][B]mörgæs**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=939075")

What do you think about Kernel compilation ?



I don't think anything. Have never tried it.

---

### Post by Doug S on 2017-10-07
> **smithbox said:**
> @Doug S
I study packets traversing in Kernel (NAT, SNAT, DNAT).
To understand it correctly I need to get access to " nf_nat_core.c " file.So do it, but I've never needed to edit nf_nat_core.c to do it.
If you want to proceed you will have to learn how to compile the kernel.

---

