---
title: "A few problems - 12.04 64-bit"
date: 2012-11-10
forum: General Help
---

### Post by Dalek Draco ON LINUX on 2012-11-10
I have an up-to-date 64-bit Ubuntu 12.04 running on a dreambook laptop. 

I am having a few problems. I made a thread for one of them earlier but I'll amalgamate everything into the one thread:

1. I ran update manager last night, there were a number of updates (python and synaptic updates I think). I logged in this morning and I am unable to use my mouse (doesn't move and clicking doesn't work). I can see the mouse pointer (unresponsive) on the login screen. But there is nothing when I log in. I've tried a few commands but nothing seems to be fixing the problem. Really annoying as I can't use the computer.

2. Previously Ubuntu has been freezing randomly. It'll go fine and then an application will stop responding or something else will happen and the system just freezes. The only thing to fix it is to hold down the power button and restart. This has now caused chkdsk to constantly come up finding errors on my hdd each time I do this. Any suggestions as to what could be causing the freezing/where I should look, would be appreciated. 

3. Finally, VLC doesn't seem to like the whole "snap to" window feature. I try to snap it to the right of the screen and do something else on the left and VLC automatically fills up the screen behind my open window. 

HELP :P.

---

### Post by HiImTye on 2012-11-10
re: problem 1, can you paste the output of */var/log/apt/term.log*? just the last batch at the end between 'Log started: ' and 'Log ended: '

re: problem 2, are you running nvidia drivers? it could be a driver issue. an alternative to hard booting, which works most times, is to do *Raising Elephants*. this process is to hold alt, press print screen, then enter the first letter of each of the following words:
> **r**aising
**e**lephants
**i**s
**s**o
**u**tterly
**b**oringthen let go of alt. this won't recover the system, but it will safely reboot, if the kernel is still responsive.
what each of these do is explained in this wiki article: [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

for problem 3, I neither use VLC, nor Unity, so I can't help you there

---

### Post by Dalek Draco ON LINUX on 2012-11-10
Thanks for your reply.  Using only the keyboard I have managed to extract the relevant information:    

Log started: 2012-11-09  19:23:24  Setting up libqtcore4 (4:4.8.1-0ubuntu4.3) ...  
Setting up libqt4-test (4:4.8.1-0ubuntu4.3) ...  
Setting up libqt4-xml (4:4.8.1-0ubuntu4.3) ...  
Setting up libqt4-dbus (4:4.8.1-0ubuntu4.3) ...  
Setting up libqt4-network (4:4.8.1-0ubuntu4.3) ...  
Setting up libqt4-sql (4:4.8.1-0ubuntu4.3) ...  
Setting up libqt4-script (4:4.8.1-0ubuntu4.3) ...  
Setting up libqt4-xmlpatterns (4:4.8.1-0ubuntu4.3) ...  
Setting up qdbus (4:4.8.1-0ubuntu4.3) ...  
Setting up aptitude (0.6.6-1ubuntu1.1) ...  
update-alternatives: warning: forcing reinstallation of alternative /usr/bin/aptitude-curses because link group aptitude is broken.  
Setting up flashplugin-installer (11.2.202.251ubuntu0.12.04.1) ...  
Setting up aptdaemon-data (0.43+bzr805-0ubuntu6) ...  
Setting up python-aptdaemon (0.43+bzr805-0ubuntu6) ...  
Setting up python-aptdaemon.gtk3widgets (0.43+bzr805-0ubuntu6) ...  
Setting up python-aptdaemon.pkcompat (0.43+bzr805-0ubuntu6) ...  
Setting up aptdaemon (0.43+bzr805-0ubuntu6) ...  
Setting up libqt4-declarative (4:4.8.1-0ubuntu4.3) ...  
Setting up libqtgui4 (4:4.8.1-0ubuntu4.3) ...  
Setting up libqt4-help (4:4.8.1-0ubuntu4.3) ...  
Setting up libqt4-scripttools (4:4.8.1-0ubuntu4.3) ...  
Setting up libqt4-designer (4:4.8.1-0ubuntu4.3) ...  
Setting up libqt4-svg (4:4.8.1-0ubuntu4.3) ...     

I'm not sure which of these if any would have caused the problem, so any advice would be gratefully accepted :P.

---

### Post by Dalek Draco ON LINUX on 2012-11-10
bump :P. 

Sorry about the lack of formatting, I had NoScript enabled and I can't disable it without my mouse pointer :P. Seems to prevent spacing.

I've done some research and none of those packages seem remotely related to the touchpage/mouse.

---

### Post by Dalek Draco ON LINUX on 2012-11-12
Bump again. Anyone? 

Kind of really need a touchpad/mouse to use the computer properly (I do anyway).

---

### Post by varunendra on 2012-11-12
First and formost - get a usb mouse if you can, to make things easy.

Next - try the generic moust driver as a quickshot -
```
sudo modprobe -rfv psmouse
sudo modprobe -v psmouse
```To let us see if your touchpad is detected at all, please post the output of -
```
xinput -list
```If you have to post the output using keyboard only, you can redirect the output to a text file to make the copy-paste easy -
```
xinput -list > Desktop/xinput
```to create 'xinput' file on your desktop.

And to let us see the currently loaded modules -
```
lsmod
```you can also redirect it to a different file (to avoid overwriting or clutter) similarly as above.

---

### Post by Dalek Draco ON LINUX on 2012-11-13
Thanks for your reply.  Using sudo modprobe -v psmouse results in &quot;could not /lib/modules...etc etc/mouse/psmouse.ko : no such file or directory.  Xinput -list output:  &#9121; Virtual core pointer                        id=2    [master pointer  (3)] &#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)] &#9123; Virtual core keyboard                       id=3    [master keyboard (2)]     &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]     &#8627; Power Button                                id=6    [slave  keyboard (3)]     &#8627; Video Bus                                   id=7    [slave  keyboard (3)]     &#8627; Power Button                                id=8    [slave  keyboard (3)]     &#8627; Sleep Button                                id=9    [slave  keyboard (3)]     &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]  Lsmod output: Module                  Size  Used by bnep                   18281  2  parport_pc             32866  0  rfcomm                 47604  0  bluetooth             180104  10 bnep,rfcomm ppdev                  17113  0  binfmt_misc            17540  1  dm_crypt               23125  1  ip6t_LOG               16974  5  arc4                   12529  2  nf_conntrack_ipv6      13906  5  nf_defrag_ipv6         13368  1 nf_conntrack_ipv6 snd_hda_codec_hdmi     32474  1  xt_hl                  12521  6  ip6t_rt                12558  3  ipt_REJECT             12576  1  ipt_LOG                12919  6  xt_multiport           12597  6  snd_hda_codec_realtek   224173  1  xt_limit               12711  14  xt_tcpudp              12603  66  xt_state               12578  10  xt_addrtype            12713  4  dm_multipath           23230  0  ip6table_filter        12815  1  ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter nf_conntrack_netbios_ns    12665  0  nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns nf_nat_ftp             12704  0  nf_nat                 25891  1 nf_nat_ftp nf_conntrack_ipv4      19716  7 nf_nat nf_defrag_ipv4         12729  1 nf_conntrack_ipv4 snd_seq_midi           13324  0  nf_conntrack_ftp       13452  1 nf_nat_ftp nf_conntrack           81926  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp snd_rawmidi            30748  1 snd_seq_midi snd_seq_midi_event     14899  1 snd_seq_midi iptable_filter         12810  1  ip_tables              27473  1 iptable_filter x_tables               29846  14 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,xt_state,xt_addrtype,ip6table_filter,ip6_tables,iptable_filter,ip_tables snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event snd_hda_intel          33773  5  i7core_edac            28102  0  snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel snd_hwdep              13668  1 snd_hda_codec iwlwifi               397012  0  edac_core              53746  1 i7core_edac snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq serio_raw              13211  0  snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec mac80211              506816  1 iwlwifi jmb38x_ms              17646  0  cfg80211              205544  2 iwlwifi,mac80211 memstick               16569  1 jmb38x_ms snd_timer              29990  2 snd_seq,snd_pcm snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_hda_intel,snd_seq,snd_hda_codec,snd_hwdep,snd_seq_device,snd_pcm,snd_timer mei                    41616  0  soundcore              15091  1 snd snd_page_alloc         18529  2 snd_hda_intel,snd_pcm mac_hid                13253  0  lp                     17799  0  parport                46562  3 parport_pc,ppdev,lp dm_raid45              78155  0  xor                    12894  1 dm_raid45 dm_mirror              22203  0  dm_region_hash         20918  1 dm_mirror dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash radeon                804460  2  jme                    41259  0  sdhci_pci              18826  0  ttm                    76949  1 radeon sdhci                  33205  1 sdhci_pci drm_kms_helper         46978  1 radeon drm                   241921  4 radeon,ttm,drm_kms_helper i2c_algo_bit           13423  1 radeon wmi                    19256  0  video                  19596  0  Again apologies for the formatting. I can't seem to format the test on here.

---

### Post by varunendra on 2012-11-13
Wow! What a holy mess! Let me first try to put it in a formatted way (took me 15-20 min on gedit ;)) -
> **Dalek Draco ON LINUX said:**
> Using sudo modprobe -v psmouse results in
"**could not /lib/modules...etc etc/mouse/psmouse.ko : [COLOR=Red]no such file or directory[/COLOR]**".

Xinput -list output:
```

 &#9121; Virtual core pointer id=2 [master pointer (3)]
 &#9116; &#8627; Virtual core XTEST pointer id=4 [slave pointer (2)]
 &#9123; Virtual core keyboard id=3 [master keyboard (2)]
 &#8627; Virtual core XTEST keyboard id=5 [slave keyboard (3)]
 &#8627; Power Button id=6 [slave keyboard (3)]
 &#8627; Video Bus id=7 [slave keyboard (3)]
 &#8627; Power Button id=8 [slave keyboard (3)]
 &#8627; Sleep Button id=9 [slave keyboard (3)]
 &#8627; AT Translated Set 2 keyboard id=10 [slave keyboard (3)]

```
Lsmod output:
```
Module            Size        Used by

bnep            18281        2
parport_pc        32866        0
rfcomm            47604        0
bluetooth        180104        10 bnep,rfcomm
ppdev            17113        0
binfmt_misc        17540        1
dm_crypt        23125        1
ip6t_LOG        16974        5
arc4            12529        2
nf_conntrack_ipv6    13906        5
nf_defrag_ipv6        13368        1 nf_conntrack_ipv6
snd_hda_codec_hdmi    32474        1
xt_hl            12521        6
ip6t_rt            12558        3
ipt_REJECT        12576        1
ipt_LOG            12919        6
xt_multiport        12597        6
snd_hda_codec_realtek    224173    1
xt_limit        12711        14
xt_tcpudp        12603        66
xt_state        12578        10
xt_addrtype        12713        4
dm_multipath        23230        0
ip6table_filter        12815        1
ip6_tables        27864        3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12665        0
nf_conntrack_broadcast    12589        1 nf_conntrack_netbios_ns
nf_nat_ftp        12704        0
nf_nat            25891        1 nf_nat_ftp
nf_conntrack_ipv4    19716        7 nf_nat
nf_defrag_ipv4        12729        1 nf_conntrack_ipv4
snd_seq_midi        13324        0
nf_conntrack_ftp    13452        1 nf_nat_ftp
nf_conntrack        81926        8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_rawmidi        30748        1 snd_seq_midi
snd_seq_midi_event    14899        1 snd_seq_midi
iptable_filter        12810        1
ip_tables        27473        1 iptable_filter
x_tables        29846        14 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,xt_state,xt_addrtype,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_seq            61896        2 snd_seq_midi,snd_seq_midi_event
snd_hda_intel        33773        5
i7core_edac        28102        0
snd_hda_codec        127706        3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep        13668        1 snd_hda_codec
iwlwifi            397012        0
edac_core        53746        1 i7core_edac
snd_seq_device        14540        3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw        13211        0
snd_pcm            97188        3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211        506816        1 iwlwifi
jmb38x_ms        17646        0
cfg80211        205544        2 iwlwifi,mac80211
memstick        16569        1 jmb38x_ms
snd_timer        29990        2 snd_seq,snd_pcm
snd            78855        20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_hda_intel,snd_seq,snd_hda_codec,snd_hwdep,snd_seq_device,snd_pcm,snd_timer
mei            41616        0
soundcore        15091        1 snd
snd_page_alloc        18529        2 snd_hda_intel,snd_pcm
mac_hid            13253        0
lp            17799        0
parport            46562        3 parport_pc,ppdev,lp
dm_raid45        78155        0
xor            12894        1 dm_raid45
dm_mirror        22203        0
dm_region_hash        20918        1 dm_mirror
dm_log            18564        3 dm_raid45,dm_mirror,dm_region_hash
radeon            804460        2
jme            41259        0
sdhci_pci        18826        0
ttm            76949        1 radeon
sdhci            33205        1 sdhci_pci
drm_kms_helper        46978        1 radeon
drm            241921        4 radeon,ttm,drm_kms_helper
i2c_algo_bit        13423        1 radeon
wmi            19256        0
video            19596        0
```


Not having psmouse module rings a bell to me. Perhaps you have a broken update. Try 'dpkg - fix broken packages' option in "Recovery" mode.
If that doesn't fix the problem, and you can connect to internet, make sure 'dkms' and 'linux-headers' are installed -
```
sudo apt-get install --reinstall dkms linux-headers-generic
```then do -
```
sudo dpkg --configure -a
sudo modprobe -v psmouse
```Even if then modprobe returns same error (/lib/modules/..../psmouse.ko not found!), then do -
```
sudo dpkg-reconfigure -a
```..and go play golf, watch movies whatever, while dpkg does its job ;) (it 'may' take really long to complete since 'all' of the installed packages are reconfigured).
After it finishes, retry modprobe psmouse.

---

### Post by mastablasta on 2012-11-13
while a fresh install will take about 30 mins.

---

### Post by varunendra on 2012-11-13
> **mastablasta said:**
> while a fresh install will take about 30 mins.
:lolflag:
You forgot - "....+ time to download updates again", which may again cause similar (or same) problems if there is a kernel upgrade included but not dkms or headers ! ;)

---

