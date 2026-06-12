---
title: "System freezes periodically for a few seconds following kernel update"
date: 2019-05-22
forum: General Help
---

### Post by frankvw on 2019-05-22
I updated my system about a month ago (Fri 26 April 2019). This was the first update in several weeks and installed fresh versions of a whole truck load of applications including a kernel update. Since this latest bunch of updates the system freezes for a few seconds at regular intervals. Not fatal, but very annoying.

Output from "journalctl -f" shows the following errors occurring at the same time as these freezes:

Apr 27 15:31:18 dellfvw wpa_supplicant[1078]: wlp3s0: CTRL-EVENT-SCAN-FAILED ret=-110
Apr 27 15:31:18 dellfvw kernel: ath10k_pci 0000:03:00.0: failed to receive scan abortion completion: timed out
Apr 27 15:31:18 dellfvw kernel: ath10k_pci 0000:03:00.0: failed to stop scan: -110
Apr 27 15:31:18 dellfvw kernel: ath10k_pci 0000:03:00.0: failed to start hw scan: -110

Corresponding lines in /var/log/syslog:

Apr 27 15:29:16 dellfvw avahi-daemon[1053]: Registering new address record for fe80::424:c75b:2a2d:52e2 on wlp3s0.*.
Apr 27 15:29:55 dellfvw avahi-daemon[1053]: Withdrawing address record for fe80::424:c75b:2a2d:52e2 on wlp3s0.
Apr 27 15:31:18 dellfvw wpa_supplicant[1078]: wlp3s0: CTRL-EVENT-SCAN-FAILED ret=-110
Apr 27 15:31:18 dellfvw kernel: [45569.661175] ath10k_pci 0000:03:00.0: failed to receive scan abortion completion: timed out
Apr 27 15:31:18 dellfvw kernel: [45569.661183] ath10k_pci 0000:03:00.0: failed to stop scan: -110
Apr 27 15:31:18 dellfvw kernel: [45569.661187] ath10k_pci 0000:03:00.0: failed to start hw scan: -110

I do note the interval between the avahi-daemon entry and the subsequent errors related to the wireless network interface, but the former precede the latter consistently in syslog, suggesting they may be related, which is why I'm including it in this report.

The freezes last a few seconds. Keyboard input is preserved at this time and typed input appears after the freeze is resolved. Mouse cursor continues to move during freezes but mouse clicks are only processed after the freeze is resolved, i.e. the result of the mouse click is suspended (e.g. buffered) until the system becomes responsive again. For example, clicking on a window during the freeze will focus that window after the freeze has been resolved.

The system is a Dell Inspiron 15 laptop. Relevant output of lspci -nnk:

03:00.0 Network controller [0280]: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter [168c:0042] (rev 31)

As already said, this is a new issue that has began occurring only after the recent batch of updates that included a kernel update. I [reported the bug]("https://bugzilla.kernel.org/show_bug.cgi?id=203445") (maybe in the wrong place) but so far I have received no response.  I've lived with this for a month or so hoping that further updates would fix the problem but it still persists.

Any and all suggestions on how to proceed would be greatly appreciated!

---

