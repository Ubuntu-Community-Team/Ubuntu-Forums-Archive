---
title: "Freezing after upgrade from 13.04 to 13.10"
date: 2014-02-18
forum: General Help
---

### Post by artwie on 2014-02-18
I finally got around to upgrading from 13.04 to 13.10 seeing as the support for 13.04 had ended and while the upgrade went smoothly (did it through do-release-upgrade if that matters), the computer now seems to completely freeze after 10-20 hours. 

On the desktop nothing works apart from the fact that at first I can still move the mouse cursor. Eventually it freezes too. I can't use ctrl-alt-f1 to get into tty1. Interestingly, however, I could ssh into the box but if I tried to do anything like run "top", the ssh froze as well. First time this happened alt-sysrq-reisub worked but then another time it didn't. Also my mumble server still seemed to respond to pings but actually connecting to the server didn't work.

I ran a memtest and it went through just fine. 

Any suggestions?

---

### Post by jeanjd63 on 2014-02-18
Hello

In console (CTRL+ALT+F1) could give the return of :
**sudo  lspci  -vnn | grep -i vga**

---

### Post by artwie on 2014-02-18
> **jeanjd63 said:**
> Hello

In console (CTRL+ALT+F1) could give the return of :
**sudo  lspci  -vnn | grep -i vga**

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G92 [GeForce 8800 GTS 512] [10de:0600] (rev a2) (prog-if 00 [VGA controller])

Using latest drivers (319.76) from [http://www.geforce.com/drivers/results/70743](http://www.geforce.com/drivers/results/70743)

I previously had a  problem  where my screen would just go black at the login screen and  downgrading to  295.33 helped. But these new drivers seemed to be working so I didn't think too much about it... Still could be the culprit? Should I try downgrading to 295.33 again?

---

### Post by jeanjd63 on 2014-02-18
You can try :
[B]sudo  apt-get  purge "nvidia *"
sudo  apt-get  install nvidia-current[/B]
and reboot
**sudo reboot**

---

### Post by artwie on 2014-02-18
> **jeanjd63 said:**
> You can try :
[B]sudo  apt-get  purge "nvidia *"
sudo  apt-get  install nvidia-current[/B]
and reboot
**sudo reboot**

Ah, I forgot to mention that I had those drivers before (they were installed with the upgrade) and the freezes happened. I then installed the latest ones from nvidia's site in case it might help, but it didn't.

ETA: 

Froze again. Sort of. This time I had System Monitor running so I could see if it might be a memory leak but no, still using only about 580 mb of ram. Anyway, System Monitor is still running. I just can't do anything -- keyboard, mouse, ssh, nothing works. But for instance, there is a spike in the network graph when I try to connect to the mumble server. Again, ctrl-alt-f1 and alt-sysrq-reisub does nothing.

It'd be an odd coincidence but could this also be because of a faulty hard drive? And if so, how would I go about checking whether that's the case?

---

