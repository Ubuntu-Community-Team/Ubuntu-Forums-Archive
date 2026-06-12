---
title: "Problems trying to install Cuckoo"
date: 2019-07-05
forum: General Help
---

### Post by alialnuaimi1996 on 2019-07-05
Hi everyone, first of all i'm very new to this so please forgive me if my question is stupid,

I'm following this guide to install Cuckoo on windows linux subsystem, everything goes great until i reach this: 

"[I]C:\> pip install cuckoo"

After running that, I get the following output:
[/I][https://i.imgur.com/zH0j74r.png](https://i.imgur.com/zH0j74r.png)

I'm really unsure where to go from here? Another thing is, in the tutorial they are running the command from cmd, not bash as it appears? if i go to cmd, it will not recognize any linux commands... maybe that ?

---

### Post by wildmanne39 on 2019-07-05
Hello and welcome to the forum.

Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

Instead of using images for terminal out please post the output in text format by using code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by QIII on 2019-07-05
For example, the following is what happens between code tags for a lengthy output.  Note that the format of the output is also preserved.

```
lsmod
Module                  Size  Used by
rfcomm                 77824  4
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
bridge                151552  0
stp                    16384  1 bridge
llc                    16384  2 bridge,stp
ebtable_filter         16384  0
ebtables               32768  1 ebtable_filter
cmac                   16384  1
devlink                45056  0
bnep                   20480  2
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  3
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
xt_LOG                 16384  10
xt_limit               16384  13
xt_tcpudp              16384  24
xt_addrtype            16384  4
arc4                   16384  2
iwlmvm                364544  0
joydev                 24576  0
mac80211              778240  1 iwlmvm
input_leds             16384  0
iwlwifi               286720  1 iwlmvm
nf_conntrack_ipv4      16384  13
edac_mce_amd           28672  0
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  17
kvm_amd                86016  0
kvm                   598016  1 kvm_amd
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
uvcvideo               86016  0
ghash_clmulni_intel    16384  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
pcbc                   16384  0
videobuf2_v4l2         24576  1 uvcvideo
snd_usb_audio         204800  1
videobuf2_core         40960  2 videobuf2_v4l2,uvcvideo
snd_hda_codec_realtek   106496  1
snd_usbmidi_lib        32768  1 snd_usb_audio
videodev              184320  3 videobuf2_core,videobuf2_v4l2,uvcvideo
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
aesni_intel           188416  2
media                  40960  2 videodev,uvcvideo
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
snd_hda_codec_hdmi     49152  1
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
btusb                  45056  0
snd_seq_midi           16384  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
snd_seq_midi_event     16384  1 snd_seq_midi
btintel                16384  1 btusb
wmi_bmof               16384  0
snd_hda_intel          40960  5
snd_rawmidi            32768  2 snd_seq_midi,snd_usbmidi_lib
bluetooth             548864  33 btrtl,btintel,btbcm,bnep,btusb,rfcomm
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
ecdh_generic           24576  2 bluetooth
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
snd_pcm                98304  5 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
cfg80211              622592  3 iwlmvm,iwlwifi,mac80211
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
ip6table_filter        16384  1
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
snd_timer              32768  2 snd_seq,snd_pcm
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 32768  3 nf_nat_masquerade_ipv4,nf_nat_ftp,nf_nat_ipv4
ccp                    73728  0
snd                    81920  25 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
k10temp                16384  0
nf_conntrack_ftp       20480  1 nf_nat_ftp
soundcore              16384  1 snd
nf_conntrack          131072  11 xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv6,nf_conntrack_ipv4,nf_nat,nf_nat_ftp,ipt_MASQUERADE,nf_conntrack_netbios_ns,nf_nat_ipv4,nf_conntrack_broadcast,nf_conntrack_ftp
libcrc32c              16384  2 nf_conntrack,nf_nat
shpchp                 36864  0
mac_hid                16384  0
sch_fq_codel           20480  19
nct6775                57344  0
hwmon_vid              16384  1 nct6775
parport_pc             36864  0
ppdev                  20480  0
iptable_filter         16384  1
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  3 iptable_filter,iptable_nat,iptable_mangle
x_tables               40960  17 ebtables,ip6table_filter,xt_conntrack,iptable_filter,xt_LOG,xt_tcpudp,ipt_MASQUERADE,xt_addrtype,xt_CHECKSUM,ip6t_rt,ip6_tables,ipt_REJECT,ip_tables,xt_limit,xt_hl,ip6t_REJECT,iptable_mangle
autofs4                40960  2
hid_logitech_hidpp     32768  0
hid_logitech_dj        20480  0
usbhid                 53248  0
hid                   118784  3 usbhid,hid_logitech_dj,hid_logitech_hidpp
usb_storage            69632  0
amdkfd                274432  1
amd_iommu_v2           20480  1 amdkfd
amdgpu               3166208  40
amdchash               16384  1 amdgpu
amd_sched              24576  1 amdgpu
amdttm                110592  1 amdgpu
mxm_wmi                16384  0
amdkcl                 28672  4 amdkfd,amd_sched,amdttm,amdgpu
drm_kms_helper        167936  1 amdgpu
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   401408  16 drm_kms_helper,amd_sched,amdttm,amdgpu,amdkcl
nvme                   36864  0
igb                   212992  0
nvme_core              61440  6 nvme
i2c_piix4              24576  0
e1000e                249856  0
dca                    16384  1 igb
i2c_algo_bit           16384  2 igb,amdgpu
ptp                    20480  2 igb,e1000e
ahci                   40960  2
pps_core               20480  1 ptp
libahci                32768  1 ahci
gpio_amdpt             16384  0
wmi                    24576  2 wmi_bmof,mxm_wmi
gpio_generic           20480  1 gpio_amdpt

```

---

### Post by alialnuaimi1996 on 2019-07-06
Hi! 

I'm following this guide to install cuckoo on linux subsystem for winodws: [https://www.trustwave.com/en-us/resources/blogs/spiderlabs-blog/cuckoo-linux-subsystem-some-love-for-windows-10/](https://www.trustwave.com/en-us/resources/blogs/spiderlabs-blog/cuckoo-linux-subsystem-some-love-for-windows-10/)


I get stuck on the step where im installing cuckoo, I don't get where to go from here, heres the output: 

```
root@DESKTOP-SNK95BA:/mnt/c# pip install cuckoo
The directory '/home/ali/.cache/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
The directory '/home/ali/.cache/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
Collecting cuckoo
  Downloading https://files.pythonhosted.org/packages/11/9c/85cd4af08962a4f4ff3ab00a2f453d343f5ff8ede9366978f4457e72d28a/Cuckoo-2.0.7.tar.gz (8.6MB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 8.6MB 123kB/s
Collecting alembic==1.0.10 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/6e/8b/fa3bd058cccd5e9177fea4efa26bfb769228fdd3178436ad5e05830ef6ef/alembic-1.0.10.tar.gz (1.0MB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 1.0MB 342kB/s
Collecting androguard==3.0.1 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/0e/eb/278e1bca7c073b25e4bed0fbaa0d5d9caaa3cee6c99cde711f8ff361fa9f/androguard-3.0.1.tar.gz (3.5MB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 3.5MB 253kB/s
Collecting beautifulsoup4==4.5.3 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/cf/9b/8a6891f8c349431ee94669ce592fc375a19d4e3f4273a01a47207c7990b2/beautifulsoup4-4.5.3-py2-none-any.whl (85kB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 92kB 1.7MB/s
Collecting chardet==2.3.0 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/7e/5c/605ca2daa5cf21c87690d8fe6ab05a6f2278c451f4ede6456dd26453f4bd/chardet-2.3.0-py2.py3-none-any.whl (180kB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 184kB 429kB/s
Collecting click==6.6 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/1c/7c/10b4132dd952b6a04e37626258825b8aa8c1eb99545f2eb26a77c21efb55/click-6.6-py2.py3-none-any.whl (71kB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 71kB 2.0MB/s
Collecting django==1.8.4 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/7e/c3/2574a681af30d99b8fd60008c3e56f4ab0acad2af70fea6c135b8bff60a2/Django-1.8.4-py2.py3-none-any.whl (6.2MB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 6.2MB 180kB/s
Collecting django_extensions==1.6.7 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/c5/b8/b0a563f18548168492afa9786f2b9d26774d75b578969488effa1f4061c0/django_extensions-1.6.7-py2.py3-none-any.whl (206kB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 215kB 819kB/s
Collecting dpkt==1.8.7 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/c6/78/3baab9f9cbf06a416e0bdd9b95268abe2b2faab4a1cc6d8ae83251bf915f/dpkt-1.8.7-py2-none-any.whl (112kB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 122kB 1.4MB/s
Collecting egghatch<0.3,>=0.2.3 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/f9/eb/a46edbdd9d9cb981b01b389eebb08ab736831a6bc485ec2b22af694fc354/egghatch-0.2.3.tar.gz
Collecting elasticsearch==5.3.0 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/37/88/692a8ece505675a62f542f06fb3c0b10f2271605576114c992b34a60492e/elasticsearch-5.3.0-py2.py3-none-any.whl (66kB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 71kB 1.9MB/s
Collecting flask-sqlalchemy==2.4.0 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/08/ca/582442cad71504a1514a2f053006c8bb128844133d6076a4df17117545fa/Flask_SQLAlchemy-2.4.0-py2.py3-none-any.whl
Collecting flask==0.12.2 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/77/32/e3597cb19ffffe724ad4bf0beca4153419918e7fa4ba6a34b04ee4da3371/Flask-0.12.2-py2.py3-none-any.whl (83kB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 92kB 1.2MB/s
Collecting gevent<1.3,>=1.2 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/74/fe/1d681dc31f61cb95fcc55e9c3baf7117e52db78270aa1bf169262f86707e/gevent-1.2.2-cp27-cp27mu-manylinux1_x86_64.whl (1.6MB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 1.6MB 435kB/s
Collecting httpreplay<0.3,>=0.2.4 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/48/3f/d139f812b14a6571b93f735aabad1f51d32d297f28981e90ca38d221370d/HTTPReplay-0.2.6.tar.gz
Collecting ipaddress>=1.0.22 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/fc/d0/7fc3a811e011d4b388be48a0e381db8d990042df54aa4ef4599a31d39853/ipaddress-1.0.22-py2.py3-none-any.whl
Collecting jinja2==2.9.6 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/5e/73/10c45b82a88ed6b7751bd40da31eeefd7b362e07b56a99aa6e56655a0794/Jinja2-2.9.6-py2.py3-none-any.whl (340kB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 348kB 700kB/s
Collecting jsbeautifier==1.6.2 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/52/ad/6800a58aa8c13b0127e2d57d284d3e3aea182aeb09da62b02c3e255d1eea/jsbeautifier-1.6.2.tar.gz (47kB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 51kB 1.9MB/s
Collecting oletools==0.51 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/3d/65/d013d389b2ab7a1e3b5b75d9352d32dfc2bb950b4b64eab81ca0593fa561/oletools-0.51.tar.gz (1.5MB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 1.5MB 427kB/s
Collecting peepdf<0.5,>=0.4.2 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/01/0f/12a50ada4a3ff2a2c0c4c74e6fababf374eff037c9786745c51fdf246c8b/peepdf-0.4.2.tar.gz (108kB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 112kB 1.4MB/s
Collecting pefile2==1.2.11 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/a1/ab/61489e4acfaa41ffb53b821f649646cd79f5787886aadc30c4058fd6ec3c/pefile2-1.2.11.tar.gz (53kB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 61kB 2.1MB/s
Collecting pillow==3.2 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/e2/af/0a3981fffc5cd43078eb8b1057702e0dd2d5771e5aaa36cbd140e32f8473/Pillow-3.2.0.tar.gz (10.3MB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 10.3MB 106kB/s
Collecting pyelftools==0.24 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/ba/78/d4a186a2e38731286c99dc3e3ca8123b6f55cf2e28608e8daf2d84b65494/pyelftools-0.24.tar.gz (411kB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 419kB 622kB/s
Collecting pyguacamole==0.6 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/ed/6f/a3ee5dc8a00c62876ebc6c72bf5fef1920f5d736badf84c85a6a628fb9ab/pyguacamole-0.6.tar.gz
Collecting pymisp==2.4.106 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/72/85/a4afc64be6c00311075cd8006fe2a47edac024f09838b60f8693b996af63/pymisp-2.4.106-py2-none-any.whl (202kB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 204kB 744kB/s
Collecting pymongo==3.0.3 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/bd/91/1857471b63eaa192127c985b29362c094ae925720d5571daf286222c9716/pymongo-3.0.3.tar.gz (419kB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 419kB 604kB/s
Collecting python-dateutil==2.4.2 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/22/75/666cd70de6a70cc7c6560429340ee7ef08196c93f552428983a808423755/python_dateutil-2.4.2-py2.py3-none-any.whl (188kB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 194kB 835kB/s
Collecting python-magic==0.4.12 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/d8/94/4b2930f2146c1318e6250c85d884c87720f3089085e4d4ba53fa0f8c620c/python-magic-0.4.12.tar.gz
Collecting roach<0.2,>=0.1.2 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/24/8c/576e1ad9c9918c65ab712f427c905758b85e0e255809ad91d994baf216a2/roach-0.1.2.tar.gz
Collecting sflock<0.4,>=0.3.10 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/97/4f/1ae8358cab38bea9d9b4b196b66c7eb68e3db8df74b77d4adf13667c792b/SFlock-0.3.10.tar.gz (1.4MB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 1.4MB 407kB/s
Collecting sqlalchemy==1.3.3 (from cuckoo)
  Downloading https://files.pythonhosted.org/packages/2b/b2/e6f5c5efc68942edefaa924e8fbea0b32375baa434a511cbf6bb17769cf6/SQLAlchemy-1.3.3.tar.gz (5.9MB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 5.9MB 166kB/s
Collecting unicorn==1.0.1 (from cuckoo)
  Retrying (Retry(total=4, connect=None, read=None, redirect=None, status=None)) after connection broken by 'ReadTimeoutError("HTTPSConnectionPool(host='files.pythonhosted.org', port=443): Read timed out. (read timeout=15)",)': /packages/7f/44/e6dd134bd7cc2dccc83e57ce435881b452a04ad5412836ba8a8e6db98dc0/unicorn-1.0.1-py2.py3-none-manylinux1_x86_64.whl
  Retrying (Retry(total=3, connect=None, read=None, redirect=None, status=None)) after connection broken by 'ReadTimeoutError("HTTPSConnectionPool(host='files.pythonhosted.org', port=443): Read timed out. (read timeout=15)",)': /packages/7f/44/e6dd134bd7cc2dccc83e57ce435881b452a04ad5412836ba8a8e6db98dc0/unicorn-1.0.1-py2.py3-none-manylinux1_x86_64.whl
  Retrying (Retry(total=2, connect=None, read=None, redirect=None, status=None)) after connection broken by 'ReadTimeoutError("HTTPSConnectionPool(host='files.pythonhosted.org', port=443): Read timed out. (read timeout=15)",)': /packages/7f/44/e6dd134bd7cc2dccc83e57ce435881b452a04ad5412836ba8a8e6db98dc0/unicorn-1.0.1-py2.py3-none-manylinux1_x86_64.whl
  Retrying (Retry(total=1, connect=None, read=None, redirect=None, status=None)) after connection broken by 'ReadTimeoutError("HTTPSConnectionPool(host='files.pythonhosted.org', port=443): Read timed out. (read timeout=15)",)': /packages/7f/44/e6dd134bd7cc2dccc83e57ce435881b452a04ad5412836ba8a8e6db98dc0/unicorn-1.0.1-py2.py3-none-manylinux1_x86_64.whl
  Retrying (Retry(total=0, connect=None, read=None, redirect=None, status=None)) after connection broken by 'ReadTimeoutError("HTTPSConnectionPool(host='files.pythonhosted.org', port=443): Read timed out. (read timeout=15)",)': /packages/7f/44/e6dd134bd7cc2dccc83e57ce435881b452a04ad5412836ba8a8e6db98dc0/unicorn-1.0.1-py2.py3-none-manylinux1_x86_64.whl
Exception:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/pip/basecommand.py", line 215, in main
    status = self.run(options, args)
  File "/usr/lib/python2.7/dist-packages/pip/commands/install.py", line 342, in run
    requirement_set.prepare_files(finder)
  File "/usr/lib/python2.7/dist-packages/pip/req/req_set.py", line 380, in prepare_files
    ignore_dependencies=self.ignore_dependencies))
  File "/usr/lib/python2.7/dist-packages/pip/req/req_set.py", line 620, in _prepare_file
    session=self.session, hashes=hashes)
  File "/usr/lib/python2.7/dist-packages/pip/download.py", line 821, in unpack_url
    hashes=hashes
  File "/usr/lib/python2.7/dist-packages/pip/download.py", line 659, in unpack_http_url
    hashes)
  File "/usr/lib/python2.7/dist-packages/pip/download.py", line 853, in _download_http_url
    stream=True,
  File "/usr/share/python-wheels/requests-2.18.4-py2.py3-none-any.whl/requests/sessions.py", line 533, in get
    return self.request('GET', url, **kwargs)
  File "/usr/lib/python2.7/dist-packages/pip/download.py", line 386, in request
    return super(PipSession, self).request(method, url, *args, **kwargs)
  File "/usr/share/python-wheels/requests-2.18.4-py2.py3-none-any.whl/requests/sessions.py", line 520, in request
    resp = self.send(prep, **send_kwargs)
  File "/usr/share/python-wheels/requests-2.18.4-py2.py3-none-any.whl/requests/sessions.py", line 630, in send
    r = adapter.send(request, **kwargs)
  File "/usr/share/python-wheels/CacheControl-0.11.7-py2.py3-none-any.whl/cachecontrol/adapter.py", line 47, in send
    resp = super(CacheControlAdapter, self).send(request, **kw)
  File "/usr/share/python-wheels/requests-2.18.4-py2.py3-none-any.whl/requests/adapters.py", line 508, in send
    raise ConnectionError(e, request=request)
ConnectionError: HTTPSConnectionPool(host='files.pythonhosted.org', port=443): Max retries exceeded with url: /packages/7f/44/e6dd134bd7cc2dccc83e57ce435881b452a04ad5412836ba8a8e6db98dc0/unicorn-1.0.1-py2.py3-none-manylinux1_x86_64.whl (Caused by ReadTimeoutError("HTTPSConnectionPool(host='files.pythonhosted.org', port=443): Read timed out. (read timeout=15)",))
```

---

### Post by deadflowr on 2019-07-06
Threads merged.
Do not start new threads on same topic/issue.

---

### Post by The Cog on 2019-07-06
I was able to download the file OK using curl, so it is there, size 17M. They just look like network timeouts to me. All I can suggest is try again some other time in case it's down to a busy network.

---

### Post by The Cog on 2019-07-07
After replying to your post, I have come across this thread: [https://ubuntuforums.org/showthread.php?t=2422383](https://ubuntuforums.org/showthread.php?t=2422383) which may have a bearing. You could try disabling SACK as described in post #3 if you're still having the problem.

---

