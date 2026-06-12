---
title: "Ubuntu 12.10 does not boot properly"
date: 2013-02-10
forum: General Help
---

### Post by bargaho on 2013-02-10
Hi everyone,

I decided to drop Wubi because I had [issues ]("http://ubuntuforums.org/showthread.php?t=2112927")with fglrx which the Wubi installation might have exacerbated. So I initially installed Ubuntu 12.04 on one of my hard drives and then replaced Unity with Gnome Shell. After discovering that 12.04 uses Gnome 3.4 and not 3.6, I upgraded Ubuntu to 12.10 and install Gnome 3.6.

Now this morning when I woke up, it wouldn't boot properly. By pressing Ctrl-Alt-F2 (or maybe just Alt-F2 was needed), I got a command prompt. I was able to start a graphical interface by using ```
startx
```

These are the things that I noticed:
[LIST]
[*]There was no top bar or dash (I installed DockbarX), just the desktop icons
[*]I got a prompt that said the Gnome keyring was not unlocked and it asked for my password again
[*]I got another prompt later on saying something about a change in language. I canceled it, but the language still changed to what seemed like Chinese
[*]Programs had to be opened through the terminal, and I was unable to alt-tab
[/LIST]

I am hoping that I wouldn't have to reinstall the whole thing. I just want to know if there is a way to repair the installation or reset it to default settings.

Thanks!

P.S.

I'm in the office right now so I can't try any suggestions right away, sorry.

---

### Post by oldfred on 2013-02-12
I have nVidia, so I have not followed AMD. But there was some info where AMD dropped support for older cards.

With nVidia and I think the newer AMD drivers you have to install linux headers first with 12.10 or it will not install correctly.
       sudo apt-get install linux-headers-generic
    
       [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

    
       [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1)> 
On the proprietary driver side, the AMD Catalyst 12.11 Beta Linux graphics driver was used. For this initial testing, three discrete graphics cards from the AMD Radeon HD 5000/6000 series were used, since pre-HD5000 graphics cards are now on the Catalyst Legacy driver and the latest-generation Radeon HD 7000 series hardware still doesn't fully work with the open-source Gallium3D "RadeonSI" driver.

    


---

### Post by bargaho on 2013-02-13
Hi,

Thanks for your reply :) I've decided to just take the plunge and dual-boot Ubuntu with Windows using separate hard drives. I haven't had time to install the AMD driver, but since Gnome Shell went broke on me, I think the problems had more to do with GS than with the driver.

Thanks!

---

