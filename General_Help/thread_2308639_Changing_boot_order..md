---
title: "Changing boot order."
date: 2016-01-04
forum: General Help
---

### Post by jdmr4815 on 2016-01-04
I installed Ubuntu 14.04 a while back and I've been quite pleased with it. Today I decided to give Debian a try. It's a little too much for me. I noticed that when I restarted my computer that the boot order had changed, with Debian replacing Ubuntu as the default. I've browsed the internet and not found any solutions that work. 

I've also looked around this forum and not found anything that quite matches my situation. (Yes, I did employ the "check if already posted" button.)

I have downloaded Grub Customizer and used it to change the boot order but it has no effect. I have gone into my other operating systems (Mint and Debian) and tried to affect the changes there, but without result. I noticed that when I run Customizer on Ubuntu it omits the Ubuntu OS [the (on dev/sda7) bit]. The others are listed. When I use Customizer in Mint or Debian, Ubuntu is listed. When using Customizer I have selected previous booted entry (after booting into Ubuntu) and the predefined option. 

I have also tried to manually change the boot order via the terminal, in Ubuntu and again in Mint and Debian. Editing the gedit /etc/default/grub file did nothing either. 

Having a wrong boot order isn't necessarily a problem per se, it'll just be a headache at times. Still, I'd like to solve the problem. 

My apologies if this problem has been solved elsewhere and I didn't look hard enough. 

Thanks in advance.

---

### Post by sammiev on 2016-01-04
Hi and Welcome,

Boot into Ubuntu 1st

I usually just use this from within "Terminal"

```
sudo grub-install /dev/sda
```

note sda is the 1st boot HDD/SSD sdb would be the second or a usb stick/drive.

```
sudo update-grub
```

There is other ways of doing it but I find this quick and easy.

---

### Post by Bucky Ball on 2016-01-04
> **sammiev said:**
> 
Boot into Ubuntu 1st

```
sudo grub-install /dev/sda
sudo update-grub
```



^^^
This.

Make sure you boot to Ubuntu and run those commands. Generally, the last one installed gets control of grub unless you manually tell it otherwise (by issuing the above commands). Good luck. :)

---

### Post by yancek on 2016-01-04
If you accepted the defaults during the install of Debian, it would have installed the Grub bootloader pointing to its root partition and you would therefore be using the Grub bootloader from Debian.  If you want Grub from Ubuntu to boot and don't plan to use Debian, first boot Ubuntu and run the commands above to install Grub to sda (Master Boot Record) and then the update-grub command.  After making any changes to the /etc/default/grub file you need to update-grub for the changes to take effect.

If you plan to leave Debian on the machine and just want Ubuntu or Mint to be the default boot, change the line below in /etc/default/grub in Debian to the correct menuentry for Ubuntu or Mint, counts from zero.

> GRUB_DEFAULT=0

---

### Post by jdmr4815 on 2016-01-05
Thanks for the answers. Unfortunately, I'm a restless person and I ended up just formatting the hard drive and starting from scratch. I do appreciate the help though, and when next I get myself into a pickle I'll be sure to come here. Thanks again.

---

### Post by Bucky Ball on 2016-01-05
Restless with time on their hands. A rather radical approach considering you were shown how to fix your issue with two lines of code prior to deciding to go for a full reinstall, but anyway ...

Please see the first link in my signature and mark the thread as solved.

---

### Post by jdmr4815 on 2016-01-05
I had been wrestling with the problem for nearly three hours before I posted here, and was already considering a full reinstall. I posed my question and waited for a bit (admittedly not very long) before checking back on the thread. I didn't see any responses so I went ahead with the reinstall. I checked on the thread this morning, saw the responses, and regretted my haste. It's not that I disregarded the help, just that I jumped that gun. I'm sorry about that.   That being said, my wife wants a fresh install of Windows on her laptop so I'm going to surreptitiously slip Ubuntu in there and then see if I can employ the information in this thread.   I'll mark the thread as solved.  ***UPDATE:  I went ahead and followed the sage advice in this thread on my laptop. Long story short, it worked. I have no earthly idea why I couldn't find such a simple solution yesterday. It's maddening. I'm such a tool. Anyway, thanks a million. I'm indebted.***

---

