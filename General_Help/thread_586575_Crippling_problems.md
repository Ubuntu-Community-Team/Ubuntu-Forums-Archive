---
title: "Crippling problems"
date: 2007-10-22
forum: General Help
---

### Post by Six Ways on 2007-10-22
Hi,
I just built a new PC from scratch about a month ago, intending to run Ubuntu as my primary OS and Windows XP for some games.

The specs are as follows:
MBoard - Asus P5N32 SLi-Premium (integrated WiFi)
Graphics - nVidia GeForce 8800GTX 768mb
Sound - Creative X-Fi XtremeMusic
RAM - 2Gb 800MHz OCZ
HDD - 500Gb SATA 2 Western Digital


However, upon installing Feisty I came up against a few major problems. Firstly, I have no sound whatsoever. I've tried to find the appropriate drivers but Creative only seem to offer x86_64 drivers for X-Fi under Linux, leading me to believe that under normal circumstances I should be having no problems with sound at all under default driver settings. This is a serious problem since I intended to use Ubuntu primarily for music and graphics creation.

Secondly, I've tried multiple times to install the nVidia graphics drivers for my GPU, but each time I activate them the X server crashes and I have to reconfigure it back to the default VESA driver. Thus I have no OpenGL acceleration, which prevents me from running most games, desktop effects, and severely hampers what I can do in terms of 3D graphics creation.

Thirdly,  my wireless, while being recognised, refused to use WPA encryption under Ubuntu. I've had to switch my router to WEP and install the WICD network manager app to get it to work. The ndiswrapper for WPA does not appear to work. Obviously, this setup is tenable but WPA is preferable.

I have a suspicion that these problems are caused by my motherboard. I've looked for relevant drivers on the Asus website but to be honest, all I can find is drivers for other distributions. I've tried recompiling these with Alien but the drivers don't seem to help at all. A friend has suggested that the problem could be in the way GRUB communicates with the BIOS, and that LiLo might do a better job of it. However, I've come up against problems installing LiLo which I can't seem to get around. Or rather, installation is fine, configuration is not. This appears to have something to do with my Windows XP bootable partition - once I've gone through the config, LiLo asks me whether the XP partition is bootable, saying that if it re-labels it XP will have a hissy fit. I tell it that it is a bootable partition, and therefore presumably to not touch it, at which point the config crashes.

So - my questions.
a) does it seem likely that my motherboard is the problem?
b) if so, should LiLo fix those problems?
c) if not, what IS the problem?

Please help - I'm very close to completely giving up on Ubuntu for my PC, which will be a huge and bitter disappointment because I wholeheartedly approve of the open source philosophy and despise having to do anything that might benefit Microsoft. In short, for my moral hygiene, I NEED Ubuntu to work for me.

Thanks for any help you can give. If you can only sort one problem, make it the sound card. Cheers!

---

### Post by Sef on 2007-10-22
> a) does it seem likely that my motherboard is the problem?
b) if so, should LiLo fix those problems?
c) if not, what IS the problem?


1) If Windows works fine, then it is unlikely to be your motherboard.  A bad motherboard wil cause problems for all systems running on it.

2) No.  Grub is boot up manager.  Once the system boots up, GRUB's job is over.

3) Not sure.

---

### Post by Six Ways on 2007-10-22
> **Sef said:**
> 1) If Windows works fine, then it is unlikely to be your motherboard.  A bad motherboard wil cause problems for all systems running on it.

I was meaning in a driver sense rather than the motherboard itself being faulty - could Ubuntu just be having problems with it?

---

### Post by Sef on 2007-10-22
> I was meaning in a driver sense rather than the motherboard itself being faulty - could Ubuntu just be having problems with it?

Yes, that is possible.

---

### Post by PmDematagoda on 2007-10-22
Since you have an issue with the X-Fi driver being only for 64 bit, you can give Ubuntu 64bit a try, I myself use it and it is very easy to use, and the installation of java and flash is simplified in Ubuntu 7.10.

About your Nvidia troubles, could you please post what you have tried and on all accounts, what sort of error messages X-server gave.

I'm afraid I do not use a wireless and do not have much experience in solving problems there, but I believe you can give the networking and wireless section of the forum a try and you could get better results there.

---

### Post by Six Ways on 2007-10-22
I'll give 64 a try, see what happens. As for the graphics problems, the x server to my memory crashes saying 'no suitable screens found'. I'll try it again tomorrow at some point and post the log.
Thanks for your help so far!

---

