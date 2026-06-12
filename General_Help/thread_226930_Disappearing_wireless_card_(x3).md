---
title: "Disappearing wireless card (x3)"
date: 2006-07-31
forum: General Help
---

### Post by jimmygoon on 2006-07-31
I've had this happen 3 times before on Ubuntu and I've bitten it and just reinstalled. Here's the deal, I execute my upgrades, I reboot, I have no wireless! :-&#-o

WHY? I'm currently on wired hookup but would really enjoy having back my wireless connection... any ideas?

---

### Post by Dr. Nick on 2006-07-31
Are you updating your kernel in these upgrades? do a fresh install and run 

lsmod

save the output then rereun your upgrades and re run lsmod. then compare the 2 outputs for any differneces. lsmod shows all driver in use.

If it is indeed the kernel upgrade messing things up then restart into the previous kernel by selecting it from the grub boot screen on boot.

---

### Post by jimmygoon on 2006-07-31
> **Dr. Nick said:**
> Are you updating your kernel in these upgrades? do a fresh install and run 

lsmod

save the output then rereun your upgrades and re run lsmod. then compare the 2 outputs for any differneces. lsmod shows all driver in use.

If it is indeed the kernel upgrade messing things up then restart into the previous kernel by selecting it from the grub boot screen on boot.

One, thank you for the response.
Two, I can't do a fresh install, I'm at camp with no disc in sight.
Third, here is lsmod output: ```
jimmygoon@nunya:~$ lsmod
Module                  Size  Used by
binfmt_misc            13064  1
ipt_limit               2624  8
iptable_mangle          2976  0
ipt_LOG                 7392  8
ipt_MASQUERADE          3840  0
ip_nat                 20652  1 ipt_MASQUERADE
ipt_TOS                 2528  0
ipt_REJECT              6176  1
ip_conntrack_irc        6992  0
ip_conntrack_ftp        8176  0
ipt_state               2016  6
ip_conntrack           54136  5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
nfnetlink               6808  2 ip_nat,ip_conntrack
iptable_filter          3104  1
ip_tables              23744  8 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
i915                   23136  3
drm                    88920  4 i915
ppdev                   9668  0
cpufreq_userspace       6496  0
cpufreq_stats           6688  0
freq_table              4928  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
video                  16324  0
tc1100_wmi              6884  0
sony_acpi               5580  0
pcc_acpi               12416  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
button                  6704  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               22848  1 i2c_acpi_ec
ipv6                  286976  31
dm_mod                 63256  1
md_mod                 76052  0
af_packet              24520  2
sr_mod                 17988  0
sbp2                   25060  0
scsi_mod              145960  2 sr_mod,sbp2
parport_pc             37988  0
lp                     12356  0
parport                39400  3 ppdev,parport_pc,lp
pcmcia                 41948  0
yenta_socket           30124  1
rsrc_nonstatic         14624  1 yenta_socket
pcmcia_core            45272  3 pcmcia,yenta_socket,rsrc_nonstatic
wlan                  146684  0
8139cp                 24032  0
joydev                 10432  0
8139too                29056  0
mii                     6176  2 8139cp,8139too
tsdev                   8032  0
usbhid                 42752  0
snd_intel8x0           35772  2
snd_ac97_codec        100224  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  2 snd_pcm_oss
snd_pcm                96708  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
psmouse                40004  0
serio_raw               7748  0
soundcore              10784  2 snd
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
intel_agp              24700  1
agpgart                36784  3 drm,intel_agp
evdev                  10176  2
ext3                  148104  1
jbd                    65876  1 ext3
ide_generic             1504  0
ohci1394               37524  0
ieee1394              306520  2 sbp2,ohci1394
ehci_hcd               36104  0
uhci_hcd               35408  0
usbcore               139076  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 35780  0
cdrom                  41440  2 sr_mod,ide_cd
ide_disk               19136  3
piix                   11652  1
generic                 5124  0
thermal                13768  0
processor              26344  1 thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit

```
Fourth, as you can see from the attachment... the Device Manager is still reading it as an Atheros Wireless Networking Card (correctly)
Fifth, Like I said before I can't really compare the outputs.

Sixth, How do I know if the kernel WAS being upgraded? I didn't read the list... is there a log somewhere?

Thanks

---

### Post by Dr. Nick on 2006-07-31
you can tell if the kernel is updated by looking at the first grub boot-loader screen that appears, If you have more then 3 entries in the list then your kernel was updated.

It would have said upgrading linux-image, when it updates the kernel the old version isnt removed, just installs the new one along side it. when you boot up choose the older kernel at the black screen, not the recovery mode or memtest though.

run 

uname -a

to see what kernel you are using currently, then just choose the other one at boot and see if it works. That could avoid a fresh install

---

### Post by jimmygoon on 2006-08-01
> **Dr. Nick said:**
> you can tell if the kernel is updated by looking at the first grub boot-loader screen that appears, If you have more then 3 entries in the list then your kernel was updated.

It would have said upgrading linux-image, when it updates the kernel the old version isnt removed, just installs the new one along side it. when you boot up choose the older kernel at the black screen, not the recovery mode or memtest though.

run 

uname -a

to see what kernel you are using currently, then just choose the other one at boot and see if it works. That could avoid a fresh install
LOL! I've had more than one kernel in my grub menu for quite some time... alas I shall attempt to use an older kernel... though I'm in an important conversation at this exact moment...

---

### Post by jimmygoon on 2006-08-01
Okay, so I used an older kernel and it worked just fine, should I just wait for a new update or what?

---

### Post by Dr. Nick on 2006-08-01
while in the older kernel you can run lsmod and compare some, look for what is not loading in the new kernel, if you see the module that is missing then run

sudo  modprobe [I]module

[/I]in the new kernel and see if it loads
It really doesnt matter to much if you use the old kernel, as long as all your hardware works you will be fine.

Every thing else updated and replaced the old, kernel is the only one that doesnt replace the old on updates I believe, so even in  a old kernel everything else is new

---

### Post by bionnaki on 2006-08-01
check out this guide: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

