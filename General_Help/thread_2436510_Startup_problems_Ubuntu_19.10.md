---
title: "Startup problems Ubuntu 19.10"
date: 2020-02-07
forum: General Help
---

### Post by s9032g@comcast.net on 2020-02-07
When starting, after shutdown for a day or two, I do not reach the password point. Just does to and fro on the dots. In order to start I have to shut down completely and try again. Starts on second try. 
I have the "Boot Repair" app and it ran a report designated as paste.ubuntu.com/p/SPgbt6RZ7X.

Thanks

---

### Post by CelticWarrior on 2020-02-07
Thank you for the Boot Repair report but in this case it isn't relevant. It merely shows a correct installation in BIOS (or Legacy) mode. Whatever is happening is likely not related to the installation mode.

That said, hoe old the computer is? Maybe it's having trouble "cold booting"... You may try pressing ESC when it appears to be stuck to read the last messages that may or may not be informative.

Anyway, please also post your hardware specifications.

---

### Post by s9032g@comcast.net on 2020-02-07
Dell Latitude E7240, 64 bit, 256 ssd, mem 15.5 GiB. Ubuntu is the only operating system on the laptop.

---

### Post by GhX6GZMB on 2020-02-07
> **s9032g@comcast.net said:**
> When starting, after shutdown for a day or two, I do not reach the password point. Just does to and fro on the dots. In order to start I have to shut down completely and try again. Starts on second try. 
I have the "Boot Repair" app and it ran a report designated as paste.ubuntu.com/p/SPgbt6RZ7X.

Thanks

Sounds to me like you're not shutting down, but just closing the lid. If that's not the case, it could be a CMOS problem.

---

### Post by s9032g@comcast.net on 2020-02-07
I am doing a complete "Power Off"

Has anyone tried the site below? Comments?

[https://www.youtube.com/watch?v=Tg4fWsFPzSE](https://www.youtube.com/watch?v=Tg4fWsFPzSE)

---

### Post by dragonfly41 on 2020-02-07
As another Dell user I offer this suggestion. I have not encountered that particular issue.

Install rEFInd alongside your existing grub configuration (they do not conflict).

[https://www.rodsbooks.com/refind/installing.html](https://www.rodsbooks.com/refind/installing.html)

Install thus using PPA ..

$ sudo apt-add-repository ppa:rodsmith/refind
$ sudo apt-get update
$ sudo apt-get install refind

You can always uninstall if you do not get results.

---

### Post by oldfred on 2020-02-07
Have you updated UEFI & SSD firmware?
Did you change drives from RAID/Intel RST to AHCI?

Issues are common across many Dell models. Even others than 7000 series. Bigger difference if AMD or Intel based.

Dell 7000
Dell 7791 UEFI update & some settings
[https://ubuntuforums.org/showthread.php?t=2431450&page=3](https://ubuntuforums.org/showthread.php?t=2431450&page=3)
Ubuntu 19.10 Provides Good Out-Of-The-Box Support For The Dell XPS 7390 Icelake Laptop
[https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1](https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1)
[https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options](https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options)
[https://wiki.ubuntu.com/Dell/XPS/XPS-13-7390-2-in-1](https://wiki.ubuntu.com/Dell/XPS/XPS-13-7390-2-in-1)
[https://ubuntuforums.org/showthread.php?t=2431791](https://ubuntuforums.org/showthread.php?t=2431791)
Dell XPS 15 Series 7590 (2019)
[https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590](https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590)
[https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019](https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019)
DELL Inspiron 15 7577 18.04 needed boot parameters
[https://ubuntuforums.org/showthread.php?t=2386049](https://ubuntuforums.org/showthread.php?t=2386049)

---

### Post by s9032g@comcast.net on 2020-02-08
I have had this laptop for some time. Converted 100% to Ubuntu as soon as I got it. The cold start problem is recent. I will check this out.

---

### Post by s9032g@comcast.net on 2020-02-08
Did the "refind" bit that Dragonfly suggested. Certainly boots faster now. Thanks

---

