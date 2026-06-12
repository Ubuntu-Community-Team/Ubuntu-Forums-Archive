---
title: "Need help troubleshooting boot errors"
date: 2018-06-17
forum: General Help
---

### Post by maeldun2 on 2018-06-17
[ATTACH=CONFIG]280125[/ATTACH]
I'm dual booting windows 10 and ubuntu. Recently I've only been using windows 10 because booting ubuntu was a bit of a coin flip, sometimes I got the splash screen and desktop and sometimes I just got a black screen. Now however, I cannot get passed this error screen, there is a new line "generic_reg_wait" and I can either reboot or use the command line. I just installed an update, probably the issue here.

I'm using an AMD Ryzen 3 2200g which I also believe is the main issue. I have the Mesa 18.1 drivers installed, which seemed to work fine (although that didn't fix the boot error messages, once landing on the desktop everything was great).

Any help with this would be appreciated (and apologies if this is posted in the wrong section).

---

### Post by oldfred on 2018-06-17
Do not know AMD, but this says you may need to add ppa to get newer kernel & support software.

        Ryzen 2400G UEFI issue on 4K at 60Hz
[https://ubuntuforums.org/showthread.php?t=2387396](https://ubuntuforums.org/showthread.php?t=2387396)
Raven Ridge With The Ryzen 5 2400G On Mesa 18.2 + Linux 4.17 Is Finally Stable MSI B350M GAMING PRO
[https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1)

---

### Post by maeldun2 on 2018-06-18
I see, thank you, however I'm pretty much a noobie and have no idea how to upgrade to the linux 4.17 kernal, especially from the trouble shooting command line.

---

### Post by oldfred on 2018-06-18
You may then want to wait for 18.10. Also since 18.04 is LTS, it will get updated kernels over time.
[https://wiki.ubuntu.com/BionicBeaver/ReleaseSchedule](https://wiki.ubuntu.com/BionicBeaver/ReleaseSchedule)
This does not yet say what kernel will be default in 18.04.2
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

If you are willing to test, but it may have issues as the developers are changing things daily. I do install a daily just to test, but keep my older version as main working install. I do not have anything that I may be concerned about losing in a test install.

Not even sure what kernel daily now has. As soon as it is available, it is almost identical to 18.04 and every day things change, until finalized in October.
       Ubuntu 18.10 Cosmic Cuttlefish 
[http://cdimage.ubuntu.com/daily-live/current/HEADER.html](http://cdimage.ubuntu.com/daily-live/current/HEADER.html)

---

### Post by maeldun2 on 2018-06-20
I updated the kernal to 4.17.2, installing all the packages under "Build for amd64 succeeded". I still boot into emergency mode =( uname -a shows the updated kernal.

---

