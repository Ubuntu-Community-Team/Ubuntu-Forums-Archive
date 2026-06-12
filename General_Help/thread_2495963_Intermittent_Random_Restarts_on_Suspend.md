---
title: "Intermittent Random Restarts on Suspend"
date: 2024-03-09
forum: General Help
---

### Post by notesetter on 2024-03-09
Hardware:

Dell Ispiron 5570
Intel Core i7 8th gen
Pop OS 22.04

Recently, when I suspend using Power Off / Log Out >> Suspend or when the system attemps to automatically suspend after inactivity, the system may fail to suspend, crash, and then reboot. Not sure what's causing the issue, but I went digging in syslog and was able to pinpoint when (I think) the last time it happened - yesterday morning. Here's a snippet of the syslog where I think the crash happened:

```

Mar  8 06:32:19 pop-os gsd-media-keys[3105]: gvc_mixer_card_get_index: assertion 'GVC_IS_MIXER_CARD (card)' failed
Mar  8 06:32:19 pop-os systemd[1]: Starting System Suspend...
Mar  8 06:32:19 pop-os wpa_supplicant[834]: wlp2s0: CTRL-EVENT-DSCP-POLICY clear_all
Mar  8 06:32:19 pop-os wpa_supplicant[834]: wlp2s0: CTRL-EVENT-DSCP-POLICY clear_all
Mar  8 06:32:19 pop-os wpa_supplicant[834]: nl80211: deinit ifname=wlp2s0 disabled_11b_rates=0
Mar  8 06:32:19 pop-os rfkill: block set for type bluetooth
Mar  8 06:32:19 pop-os kernel: [109730.740939] PM: suspend entry (deep) ## <-- crash here?

Mar  8 06:32:50 pop-os systemd-modules-load[391]: Inserted module 'lp'
Mar  8 06:32:50 pop-os systemd-modules-load[391]: Inserted module 'ppdev'
Mar  8 06:32:50 pop-os systemd-modules-load[391]: Inserted module 'parport_pc'
Mar  8 06:32:50 pop-os systemd-modules-load[391]: Module 'ecryptfs' is built in
Mar  8 06:32:50 pop-os systemd-modules-load[391]: Inserted module 'msr'

```

Anyone keen to help a non-hardware guy investigate?

---

