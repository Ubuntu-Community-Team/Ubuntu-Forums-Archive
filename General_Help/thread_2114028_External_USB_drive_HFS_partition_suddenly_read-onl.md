---
title: "External USB drive HFS partition suddenly read-only"
date: 2013-02-08
forum: General Help
---

### Post by linuxn00bface on 2013-02-08
[http://ubuntuforums.org/showthread.php?t=1797320](http://ubuntuforums.org/showthread.php?t=1797320)

Pretty much the same as this guy, I don't want to screw anything up though.

As [this guy]("http://ubuntuforums.org/showpost.php?p=11013929&postcount=4") said, the last 10-15 lines of dmesgare:
```

[   40.138251] cfg80211: Disabling freq 5900 MHz
[   40.138252] cfg80211: Disabling freq 5910 MHz
[   40.138253] cfg80211: Disabling freq 5920 MHz
[   40.138254] cfg80211: Disabling freq 5930 MHz
[   40.138255] cfg80211: Disabling freq 5940 MHz
[   40.138256] cfg80211: Disabling freq 5950 MHz
[   40.138257] cfg80211: Disabling freq 5960 MHz
[   40.138257] cfg80211: Disabling freq 5970 MHz
[   40.138258] cfg80211: Disabling freq 5980 MHz
[   40.138259] cfg80211: Disabling freq 5990 MHz
[   40.138260] cfg80211: Disabling freq 6000 MHz
[   40.138261] cfg80211: Disabling freq 6010 MHz
[   40.138262] cfg80211: Disabling freq 6020 MHz
[   40.138263] cfg80211: Disabling freq 6030 MHz
[   40.138264] cfg80211: Disabling freq 6040 MHz
[   40.138265] cfg80211: Disabling freq 6050 MHz
[   40.138266] cfg80211: Disabling freq 6060 MHz
[   40.138266] cfg80211: Disabling freq 6070 MHz
[   40.138267] cfg80211: Disabling freq 6080 MHz
[   40.138268] cfg80211: Disabling freq 6090 MHz
[   40.138269] cfg80211: Disabling freq 6100 MHz
[   40.138270] cfg80211: Disabling freq 6110 MHz
[   40.138271] cfg80211: Disabling freq 6120 MHz
[   40.138272] cfg80211: Disabling freq 6130 MHz
[   40.138273] cfg80211: Disabling freq 6140 MHz
[   40.138284] cfg80211: Regulatory domain changed to country: HK
[   40.138285] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   40.138287] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   40.138288] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   40.138290] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   40.138291] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   40.138293] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   41.218795] audit_printk_skb: 48 callbacks suppressed
[   41.218798] type=1400 audit(1360384676.430:28): apparmor="DENIED" operation="open" parent=1017 profile="/sbin/dhclient" name="/etc/ld.so.preload" pid=2024 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   41.235641] type=1400 audit(1360384676.446:29): apparmor="DENIED" operation="open" parent=2024 profile="/usr/lib/NetworkManager/nm-dhcp-client.action" name="/etc/ld.so.preload" pid=2026 comm="nm-dhcp-client." requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   41.299327] type=1400 audit(1360384676.510:30): apparmor="DENIED" operation="open" parent=2024 profile="/usr/lib/NetworkManager/nm-dhcp-client.action" name="/etc/ld.so.preload" pid=2027 comm="nm-dhcp-client." requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   51.712056] eth1: no IPv6 routers present
[   61.313459] type=1400 audit(1360384696.530:31): apparmor="DENIED" operation="open" parent=2510 profile="/usr/lib/telepathy/mission-control-5" name="/etc/ld.so.preload" pid=2511 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

```User permissions for the hfs partition of the external, and the files contained within, are "99 - user #99"

Help, please!

---

### Post by linuxn00bface on 2013-02-12
... help?

TY

---

