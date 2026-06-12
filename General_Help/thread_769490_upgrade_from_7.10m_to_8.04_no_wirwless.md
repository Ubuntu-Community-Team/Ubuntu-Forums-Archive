---
title: "upgrade from 7.10m to 8.04 no wirwless"
date: 2008-04-26
forum: General Help
---

### Post by idoisler on 2008-04-26
so i just upgraded and i novice in Linux
my wireless worked just fine on 7.10 
when i write in the terminal iwconfig

i get 

 lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


any ideas ????

---

### Post by lanruisen on 2008-04-26
I have the same problem. It does not detect my wireless card after update. I have a D-Link Atheros based card.

---

### Post by Zyphrexi on 2008-04-26
I had the same issue as well. Is it fixed yet?

Atheros-based chipset here also.

---

### Post by lanruisen on 2008-04-26
This post worked for me. #7
[http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529)

---

### Post by Zyphrexi on 2008-04-27
I checked my installed linux-restricted-modules against uname -r, and found that I didn't actually have the metapackage installed (or updated) so my guess is that originally what happened is it set up the latest kernel ver to boot from but didn't have the linux-restricted-modules for that kernel version. [uname -r spits out 2.6.24-16-generic.]

now I do, so everything is hunky dory. for those still with no net, grab your livecd, chroot, and apt-get install whatever restricted module ver you need. worked for me. (provided you DONT have it installed, if you do, then I really have no idea)

---

