---
title: "Hp 250 G3 freezing on both shutdown and suspend plus more issues."
date: 2015-12-09
forum: General Help
---

### Post by gianmarco2 on 2015-12-09
I've got some weird issues with my notebook (HP 250 G3). I bought this pc as a freedos and installed windows 10 but since I didn't like it, I removed it completely and installed Ubuntu mate and also used the lvm partition with the encryption. Problem is that since then the pc won't shut down, or suspend without freezing, the only way to power it off is to force the shutdown with the power button. Also, when it restarts often it doesn't display the decryption password interface but remains with a black screen instead, I can still type the password on the blackscreen (knowing that it's there even if I can't see it) and log in. Is there a way to fix this? I've looked on the web and found a similar issue with a Lenovo that was solved updating the bios but I'm not sure this is my case. Can you help me please?

---

### Post by cmcanulty on 2015-12-09
I assume you have a swap partition. Also to enable hibernate swap partition must be at least as large as amount of RAM

---

### Post by gianmarco-massarotto on 2015-12-09
The system created all the partition so I don't know if I have one, probably yes. It is quite dumb that the system doesn't configure the partitions properly though.

---

