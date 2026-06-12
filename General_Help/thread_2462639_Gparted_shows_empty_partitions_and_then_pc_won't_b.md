---
title: "Gparted shows empty partitions and then pc won't boot"
date: 2021-05-24
forum: General Help
---

### Post by sofasurfer on 2021-05-24
I ran Gparted from my running 20.04 install. Everything looks normal. I then inserted a Gparted dvd and rebooted. Gparted show all partitions as empty. I removed dvd and rebooted. The splash screen comes up and after about 15 seconds a black screen comes up with a flashing cursor. Thats all I get. After I shut computer off with switch on the back it will the reboot. System has been running great and I have never had trouble with this Gparted dvd before. Any idea what happens when this occurs?

---

### Post by sofasurfer on 2021-05-25
I discovered my problem was that I was using an old version of Gparted. It had the partitions marked as ext3 when they were actually ext4. Got a new Gparted and all is well. Case solved.

---

### Post by HermanAB on 2021-05-25
I would not use a special gparted DVD, since it may be hopelessly out of date and may not work with new hardware. The Ubuntu install media contains gparted, so you should try the latest Ubuntu install media, boot to the live system and run gparted.

---

### Post by sofasurfer on 2021-05-25
Good idea. Thanks

---

