---
title: "USB key/flashdrive/thumbdrive"
date: 2006-07-09
forum: General Help
---

### Post by FieldsofOmar on 2006-07-09
Hi all,

I have been enjoying Ubuntu, my USB thumbdrive (shintaro 1 Gig) no longer appears on the desktop or in nautilus. I have tried reformatting the thumbdrive in Windows several times without any effect.

Dmesg gives the following response:

[HTML][17180992.280000] sda: Mode Sense: 00 00 00 00
[17180992.280000] sda: assuming drive cache: write through
[17180992.280000]  sda: unable to read partition table
[17180992.284000] sda : READ CAPACITY failed.
[17180992.284000] sda : status=0, message=00, host=7, driver=00
[17180992.284000] sda : sense not available.
[17180992.284000] sda: Write Protect is off
[17180992.284000] sda: Mode Sense: 00 00 00 00
[17180992.284000] sda: assuming drive cache: write through
[17180992.284000] sda : READ CAPACITY failed.
[17180992.284000] sda : status=0, message=00, host=7, driver=00
[17180992.284000] sda : sense not available.
[17180992.284000] sda: Write Protect is off
[17180992.284000] sda: Mode Sense: 00 00 00 00
[17180992.284000] sda: assuming drive cache: write through
[17180992.284000]  sda: unable to read partition table
[17180994.284000] sda : READ CAPACITY failed.
[17180994.284000] sda : status=0, message=00, host=7, driver=00
[17180994.284000] sda : sense not available.
[17180994.284000] sda: Write Protect is off
[17180994.284000] sda: Mode Sense: 00 00 00 00
[17180994.284000] sda: assuming drive cache: write through
[17180994.284000] sda : READ CAPACITY failed.
[17180994.284000] sda : status=0, message=00, host=7, driver=00
[17180994.284000] sda : sense not available.
[17180994.284000] sda: Write Protect is off
[17180994.284000] sda: Mode Sense: 00 00 00 00
[17180994.284000] sda: assuming drive cache: write through
[17180994.284000]  sda:<4>printk: 7 messages suppressed.
[17180994.284000] Buffer I/O error on device sda, logical block 0
[17180994.284000]  unable to read partition table
[17180994.288000] sda : READ CAPACITY failed.
[17180994.288000] sda : status=0, message=00, host=7, driver=00
[17180994.288000] sda : sense not available.
[17180994.288000] sda: Write Protect is off
[17180994.288000] sda: Mode Sense: 00 00 00 00
[17180994.288000] sda: assuming drive cache: write through
[17180994.288000] sda : READ CAPACITY failed.
[17180994.288000] sda : status=0, message=00, host=7, driver=00
[17180994.288000] sda : sense not available.
[17180994.288000] sda: Write Protect is off
[17180994.288000] sda: Mode Sense: 00 00 00 00
[17180994.288000] sda: assuming drive cache: write through
[17180994.288000]  sda: unable to read partition table
[/HTML]

Any and all help would be appreciated as this is driving me insane!!!

Cheers

---

### Post by Rui Pais on 2006-07-09
Hi,
ensure that you are on plugdev group.
On a terminal type:
```
groups `whoami`
```
among others should appears the word **plugdev**

Check too the several suggestions on this [thread]("http://ubuntuforums.org/showthread.php?t=191963"), specially those concerning module loading (sometimes autoload modules won't work and is necessary to had them to /etc/modules)

hope that helps

---

### Post by FieldsofOmar on 2006-07-09
Hi,

Thanks for the reply - plugdev is certainly listed in the groups.

Will check the suggestions in the other thread.

Cheers

---

### Post by FieldsofOmar on 2006-07-09
Still no joy... however I did note that when I try to mount /dev/sda the output is:

mount: /dev/sda: can't read superblock

and sudo fdisk -l /dev/sda does not produce any result.

---

### Post by Rui Pais on 2006-07-09
> **FieldsofOmar said:**
> Still no joy... however I did note that when I try to mount /dev/sda the output is:

mount: /dev/sda: can't read superblock

and sudo fdisk -l /dev/sda does not produce any result.

what ls /dev/sda* says? 
and whats the output of lsmod (with the usb drive plugged)?

---

### Post by FieldsofOmar on 2006-07-09
Rui Pais,

ls dev/sda* returns:
/dev/sda

lsmod outputs

[html]
Module                  Size  Used by
nfnetlink_queue        13120  1
binfmt_misc            12296  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ipt_NFQUEUE             1920  3
ipt_limit               2432  8
iptable_mangle          2944  0
ipt_LOG                 6912  8
ipt_MASQUERADE          3456  0
ip_nat                 19628  1 ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              5632  1
ip_conntrack_irc        6768  0
ip_conntrack_ftp        7792  0
ipt_state               2048  9
ip_conntrack           51500  5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntr ack_ftp,ipt_state
nfnetlink               6552  4 nfnetlink_queue,ip_nat,ip_conntrack
iptable_filter          3072  1
ip_tables              22400  9 ipt_NFQUEUE,ipt_limit,iptable_mangle,ipt_LOG,ipt _MASQUERADE,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
ppdev                   9220  0
i915                   20608  1
drm                    73236  2 i915
speedstep_centrino      8400  1
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
sg                     37920  0
sd_mod                 19984  0
nls_iso8859_1           4224  1
nls_cp437               5888  1
vfat                   13440  1
fat                    53020  1 vfat
nls_utf8                2176  1
ntfs                  103536  1
ipv6                  265728  6
af_packet              22920  2
dm_mod                 58936  1
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  0
lp                     11844  0
pcmcia                 40508  0
joydev                 10048  0
usb_storage            74176  0
scsi_mod              139496  5 sg,sd_mod,sr_mod,sbp2,usb_storage
tsdev                   8000  0
e100                   40580  0
ipw2200               107308  0
mii                     5888  1 e100
ieee80211              37064  1 ipw2200
ieee80211_crypt         6272  1 ieee80211
ieee80211_1_1_13       38216  0
ieee80211_1_1_13_crypt     6784  1 ieee80211_1_1_13
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
pcspkr                  2180  0
snd_intel8x0           33692  1
rtc                    13492  0
psmouse                36100  0
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
usblp                  13056  0
usbhid                 39904  0
serio_raw               7300  0
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixe r_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
intel_agp              22940  1
agpgart                34888  3 drm,intel_agp
evdev                   9856  2
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               34184  0
uhci_hcd               33680  0
usbcore               130692  6 usb_storage,usblp,usbhid,ehci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  5
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  2 speedstep_centrino,thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

[/html]

Cheers

---

### Post by Rui Pais on 2006-07-09
uhmmm all needed modules seem to be loaded... 

re-reading yout first post i noted now:
> [17180994.288000] sda: assuming drive cache: write through
[17180994.288000]  sda: unable to read partition table

That seems to indicate un unformated drive. 
What filesystem was on there?  

Can you check what gparted says about it?

Once a shutdown of a Windows machine with my usb drive connected but not unmouted unformated it!! :(

---

### Post by FieldsofOmar on 2006-07-09
Rui Pais,

It was either FAT or FAT32. I think it was FAT32.

GParted lists it as unallocated. When I try to set disklabel or create a new partition on the usb thumbdrive produces an error: "Error while setting new disklabel".

The first problem I had with the thumbdrive was when a windows machine wanted to reformat it, which I didn't do. When I got it back to my notebook it wouldn't recognise or detect it.

It is possible, although unlikely, that I failed to eject it from my ubuntu machine before I removed it.

Cheers

---

### Post by Rui Pais on 2006-07-09
Do you have any Windows around?

Maybe trying to see what happen on Windows could definitly decide if it was erased or is some obscure problem with Linux. 

Sorry, the perspectives don't look very goods...

---

### Post by FieldsofOmar on 2006-07-09
Windows doesn't appear to have a problem with it. I can copy files to and from the thumbdrive and format it to my heart's content!

I'd be happy to write it off and buy another if I knew what had happened and wasn't worried it would happen again!!!!

Cheers

---

### Post by Rui Pais on 2006-07-09
well, anyway, thats good news! 

Did the drive mount on Linux after been reformated on Windows?

By the way, on which kernel that this happened? I read that the ubuntu version -25 sometimes give problems.

---

### Post by FieldsofOmar on 2006-07-09
Nope - reformatting doesn't seem to make any difference. 

I have to apologise as a ubuntu newbie - how do I find out which version kernel I'm running?

Cheers

---

### Post by FieldsofOmar on 2006-07-09
Got it - 2.6.15-25-386

We may have a culprit!

---

### Post by Rui Pais on 2006-07-09
hi again, 
using synaptic you can check which versions you have.
If you dont have a 2.6.15-23 you can install it from there.
That will add an entry for it to grub.

Try to start your ubuntu with the 23 version (choose from the grub menu) and check if you got the same behave.

good luck

---

### Post by FieldsofOmar on 2006-07-09
Thanks for all your help!

It's 1am here now so I might leave mucking about with the kernel until tomorrow! :)

Cheers

---

