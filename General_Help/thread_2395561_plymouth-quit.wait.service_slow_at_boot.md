---
title: "plymouth-quit.wait.service slow at boot"
date: 2018-07-03
forum: General Help
---

### Post by mwwuite on 2018-07-03
When booting up my Ubuntu 18.04 the plymouth wait service takes a long time during boot. This happened this morning for the first time.  Any idea how to fix this?   

3min 3.994s plymouth-quit-wait.service
    1min 31.194s snapd.seeded.service
          6.367s NetworkManager-wait-online.service
          1.937s dev-sda1.device
          1.611s dev-loop19.device
          1.566s dev-loop15.device
          1.557s dev-loop20.device
          1.553s dev-loop16.device
          1.531s dev-loop22.device
          1.530s dev-loop17.device
          1.530s dev-loop21.device
          1.515s dev-loop23.device
          1.502s dev-loop24.device
          1.500s dev-loop13.device
          1.493s dev-loop18.device
          1.469s dev-loop29.device
          1.465s dev-loop14.device
          1.463s dev-loop25.device
          1.449s dev-loop27.device
          1.444s dev-loop30.device
          1.436s dev-loop31.device
          1.428s dev-loop28.device
          1.423s dev-loop5.device

---

### Post by #&amp;thj^% on 2018-07-03
This has been brought up with recent updates:
Try booting to an older kernel through grub >> Advanced Options.
EDIT: I'm not affected by the slow bootup luckily.
```
 Startup finished in 4.412s (kernel) + 31.072s (userspace) = 35.485s
graphical.target reached after 31.065s in userspace

```
Others also affected: [https://ubuntuforums.org/showthread.php?t=2395459](https://ubuntuforums.org/showthread.php?t=2395459)
And: [https://ubuntuforums.org/showthread.php?t=2395452](https://ubuntuforums.org/showthread.php?t=2395452)

---

