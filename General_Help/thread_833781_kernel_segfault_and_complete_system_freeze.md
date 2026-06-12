---
title: "kernel segfault and complete system freeze"
date: 2008-06-18
forum: General Help
---

### Post by meanerelk on 2008-06-18
Hardy 8.04 failed catastrophically on me today. The system was completely frozen, and did not respond to mouse or keyboard. I tried every key combination, including Raising Skinny Elephants, to no avail. With a heavy heart, I pressed the hard reset button. Thankfully, nothing seems to have been lost.

Upon inspecting the logs, I found this in /var/log/messages, right about the time it probably froze:
```
Jun 18 19:15:51 hostname kernel: [19567.659433] python[12635]: segfault at 00002e07 eip b7a33dd3 esp bfe27fd0 error 4
```

I know segfaults are bad, but I haven't the slightest idea how to go about interpreting or fixing this. Any help would be greatly appreciated.

---

### Post by meanerelk on 2008-06-19
it happened again last night. This time, there was nothing about a segfault in the logs. Instead, this is what showed up. Could they be related? Would switching to different kernel help? I am really upset, because I've never had these kinds of freezes with linux before. I need my computer running 24-7, because I am running a research project on it.

```
Jun 19 05:27:19 carnifex kernel: [25964.029381] ata6: hard resetting link
Jun 19 05:27:19 hostname kernel: [25964.761117] ata6: SATA link down (SStatus 0 SControl 300)
Jun 19 05:27:19 hostname kernel: [25964.761128] ata6: failed to recover some devices, retrying in 5 secs
Jun 19 05:27:24 hostname kernel: [25969.757028] ata6: hard resetting link
Jun 19 05:27:25 hostname kernel: [25970.077118] ata6: SATA link down (SStatus 0 SControl 300)
Jun 19 05:27:25 hostname kernel: [25970.077128] ata6: failed to recover some devices, retrying in 5 secs
Jun 19 05:27:30 hostname kernel: [25975.071474] ata6: hard resetting link
Jun 19 05:27:30 hostname kernel: [25975.395511] ata6: SATA link down (SStatus 0 SControl 300)
Jun 19 05:27:30 hostname kernel: [25975.395520] ata6.00: disabled
Jun 19 05:27:31 hostname kernel: [25975.894633] ata6: EH complete
Jun 19 05:27:31 hostname kernel: [25975.894641] ata6.00: detaching (SCSI 5:0:0:0)
Jun 19 05:27:31 hostname kernel: [25975.894892] sd 5:0:0:0: [sdb] Synchronizing SCSI cache
Jun 19 05:27:31 hostname kernel: [25975.894932] sd 5:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Jun 19 05:27:31 hostname kernel: [25975.894940] sd 5:0:0:0: [sdb] Stopping disk
Jun 19 05:27:31 hostname kernel: [25975.894952] sd 5:0:0:0: [sdb] START_STOP FAILED
Jun 19 05:27:31 hostname kernel: [25975.894956] sd 5:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
```

---

### Post by meanerelk on 2008-06-19
Argh, it happened again! This time there was not even any message in any log to hint at what the cause could be.

Anyone else have problems like this?

---

### Post by daftman on 2008-08-03
Yep I have this problem and I can't understand why it happens.
For me, it starts with evolution segfault and then just rolled downhill from there to nautilus segfault, gnome-terminal segfault, main-menu segfault, gnome-panel, etc
I couldn't open another ttys using the alt+f1-5 keys. However, I was able to use the alt + RSEIUB and manage to get into the prompt and "shutdown -r now"
This happens on a Dell m1530.

---

