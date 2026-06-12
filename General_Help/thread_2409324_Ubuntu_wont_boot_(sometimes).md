---
title: "Ubuntu wont boot (sometimes)"
date: 2018-12-31
forum: General Help
---

### Post by chris230291 on 2018-12-31
Hi guys. I got myself a supermicro server and installed Ubuntu on a SSD. This is my first server motherboard and the first time I have had any problems with Ubuntu booting. I can only assume that I am not doing something correctly in the install.

I wonder if this means anything to anyone. Normally if I see this I just try a reset until it boots normally.

[https://cl.ly/14e6e2235d10/Screenshot_2.png](https://cl.ly/14e6e2235d10/Screenshot_2.png)

[https://cl.ly/09cfd2e02b89/Screenshot_1.png](https://cl.ly/09cfd2e02b89/Screenshot_1.png)

Any input is apreciated.
Chris

---

### Post by clementc on 2018-12-31
Hi Chris,

According to [this blog entry]("http://www.acargil.net/2016/08/comreset-failed-errno-32.html"), your issue could be caused by a poor SATA cable connection (either SATA cable or SATA port on the motherboard) or potentially failing hardware (e.g. optical drive or SSD on its way out).

Of course these are only pointers, the only way to know for sure would be for you to open up your server and try unplugging a few things, leaving only the SSD connected to the motherboard.

Please do not attempt this unless you feel confident about the whole procedure.

---

### Post by chris230291 on 2018-12-31
Thanks for the reply. 

I tried different SATA cables and ports but that didnt help. I updated the BIOS on this board and that seems to have fixed it though. After a lot of reading it seems the board, atleast when it shipped, only supported Ubuntu 11. 

I still get some messages though, but they only appear breifly and booting is now both consistent and much faster.

These are the only things I see now

[IMG]https://cl.ly/9195667c4633/Screenshot_4.png[/IMG]

Would like to learn what this means if possible. All I found was a kernal bug report here ([https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=824854](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=824854))

Either way its booting much faster and consistenly now so I am happy.

Cheers,
Chris

---

### Post by clementc on 2018-12-31
Hi Chris,

I am glad to hear that you managed to fix your issue. Good to know that a BIOS update can fix this!

Regarding the messages that you still see at boot up time, according to [this page]("https://www.linuxquestions.org/questions/arch-29/acpi-error-namespace-lookup-failure-ae_not_found-1st-time-arch-dual-boot-attempt-4175600545/") which links to [this page]("https://www.linuxquestions.org/questions/linux-hardware-18/acpi-error-what-means-4175605357/"), this means that the ACPI implementation in your motherboard's BIOS/UEFI is faulty.

However, generally, it's not cause for concern. So if everything else works, I wouldn't worry too much about it.

---

### Post by wildmanne39 on 2018-12-31
Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

---

