---
title: "Linux on Symbol / Motorola MC75A(6)"
date: 2012-11-16
forum: General Help
---

### Post by mc75 on 2012-11-16
Moved from;
Ubuntu Forums > The Ubuntu Forum Community > Ubuntu Specialised Support > Development & Programming > Ubuntu Dev Link Forum
reason - no respons...

Hi everyone,

I'll be honest with all and I'll say that I am an M$ kiddo. My knowledge never goes deeper than a little bit of building M$ server (using IIS build-in services) and a little bit of Windows debugger.
I know that's actually nothing, comparing to knowledge of "managing linux-base systems". I had even tried these my self, but couldn't get through command prompt in linux...(Ubuntu, Mandriva most).

I am user of Motorola EDA (Symbol) MC75 [A6] with build in Windows Mobile 6.5 Proffesional. Device spec:

CPU: Intel XScale ("Monahan") PXA320 (806 MHz)
Memory: 256MB RAM, Storage: 1 GB, microSD (SDHC up to 32GB)
Display: 3.5&#8221; VGA, 640x480
Touch Panel: Glass	analog -resistive touch
Battery: Lithium Ion: 3.7V,	3600 mAh (13.3 Wh)

[RedBoot] BOOT LOADER

I think it would be the most important about it. If more necessary: [http://www.thebarcodewarehouse.co.uk/Assets/PDF/17702.pdf](http://www.thebarcodewarehouse.co.uk/Assets/PDF/17702.pdf)

I just have enough of this M$ sh^t... Hoping I could get a little help to manage Linux-base system instalation on it, the latest possibly compatible sys with ARM (v5 - end of 2006) processors would be DEBIAN or MINT PPC. I will post same message on Mint forum (can't register at the moment). I have spent whole week, reading thousands posts and websites about Androids, Linux, Symbian...and I am "sick of it"...There is everything for Nokia's, HTC's, I-thing's...etc, but nothing...absolutely nothing about this PPC. And even if I found something, software and everything are linux-kind - don't really know what to do with them on WinMobile... I know M$ is not open-source, I would love to get rid of it...

I don't care about phone function's, because this device is retired ;p I use it only for some recreation when I am at home (music/streaming/video/www etc).
If some drivers would be necessary to be build for audio device or similar, the only thing I could help is providing Windows Registry Keys / Drivers from the device. That's what would be for me.
I know that there are other people using MC70 / MC75 (similar build) that are interested with "Moving Windows/System to trash" :D

Let's help some of us to Bin M$, and let us use a little more from those devices.
I am not native-english speaker so apologizes for misunderstandings.

I would like to add also, there are many informations about Ubuntu for / not for PPC...I even found some distro's for PPC but don't even know which distro (if)is supporting Intel XScale... :(
I Apologize but I am confused...some wiki-pages confirm Ubuntu for PPC, some deny... I would actually go for any Linux distro just not to see Windows Mobile ever again...

Hmm...I have just realized about LAN Port in cradle docking station for this device...OMG :D
Would it be possible to bite it all together with on-line Linux installer? ;D ...I'll keep looking more this way maybe...

P.S. Posted also at Debian Forum:
[http://forums.debian.net/viewtopic.php?f=19&t=88254&p=461471#p461471]("http://forums.debian.net/viewtopic.php?f=19&t=88254&p=461471#p461471")

Thank You for any replays,
Glad to be here ;]
Cheers!

-_____-_____-_____-_____-_____-

As long this topic will persist without response I will keep posting what I have found and on what stage I am currently stucked.

[**REDBOOT**] website gave me some more options to look for. _REDBOOT does allow me "net booting" futures._ I have actually no clue what to do next, so I am not digging more about netbooting. I have already learn a lesson how it is easy to damage BIOS structure - my knowledge is not high enough to dig any further...at least just for now.
sources:
[http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/RedBoot-an-open-source-bootdebug-environment/]("http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/RedBoot-an-open-source-bootdebug-environment/")
[http://sourceware.org/redboot/]("http://sourceware.org/redboot/")

I will focus on "HDD Booting" method at this stage. It should give me some help-back door in case something goes wrong.

I am actually stuck how to even see hidden files within the device... :confused:

**[COLOR="red"]I will use HARET to test linux;[/COLOR]**

According to some info's, I think I should pick:
[U]> armel (omap, [s]omap4[/s])**-> Is Intel XScale Pxa 320  "armel OMAP" CPU?**
[/U]

Note: because there are no longer lists of any "ARMEL" distros, had to pick this: [DOWNLOAD]
.../sites/cdimage.ubuntu.com/cdimage/releases/**_11.10_**/release/
[http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/11.10/release/ubuntu-11.10-preinstalled-desktop-armel+omap.img.gz]("http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/11.10/release/ubuntu-11.10-preinstalled-desktop-armel+omap.img.gz")

If everything goes the way it should...I will present video of that Linux test soon.

:arrow:[COLOR="Red"]Stuck with[/COLOR] Ubuntu 11.04 image is a *.raw file with file size 2 gb (o . O)

more infos soon... :idea:

---

