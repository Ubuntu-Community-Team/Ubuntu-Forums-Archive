---
title: "What Version You Suggest For Toshiba NB200-10z"
date: 2015-01-02
forum: General Help
---

### Post by shahbaz3 on 2015-01-02
It is Toshiba NB200-10z
Here are specs:

Processor: Intel Atom N280 @ 1.6 Ghz single core
RAM: 2GiB DDR2
Graphics: Intel GMA 950

Also I want to install it with my windows. With Wubi right? I saw it doesn't works with Windows 8. My netbook was preinstalled with Win XP. I have now Windows 8.1 + Tiny 7 (unofficial version of Win7) installed. If I install any version through Wubi, will my windows boot along with Ubuntu?

P.S: I have been using some random ubuntu version with USB flash drive.

Thanks for your help.

---

### Post by stalkingwolf on 2015-01-02
unless i am mistaken wubi is no longer supported .  There are several distros that will work . Lubuntu, kubuntu, zorin, mint (i use mint 13 mate)  and some ive missed im sure.  pick what works best for you.

---

### Post by Gordonbp531 on 2015-01-02
I'm very surprised that Windows 8 even installed on your machine - Windows 8 won't install on non-UEFI machines (AFAIK) and the Tosh NB280 certainly isn't UEFI enabled...
I've installed Ubuntu 14.04 on a very similar specced Eeee PC - 2GB RAM, Intel Atom N270 1.66GHz processor and it runs perfectly OK.
You'd be far better off installing it as dual-boot and not using Wubi. As you correctly say, Wubi doesn't work with Windows 8 anyway.

---

### Post by shahbaz3 on 2015-01-02
> **stalkingwolf said:**
> unless i am mistaken wubi is no longer supported .  There are several distros that will work . Lubuntu, kubuntu, zorin, mint (i use mint 13 mate)  and some ive missed im sure.  pick what works best for you.

Oh, didn't knew that wubi is not supported. Please suggest any one that would best suit as I can't test all :S Does each one have any difference between their software centers and terminal commands?

> **Gordonbp531 said:**
> I'm very surprised that Windows 8 even installed on your machine - Windows 8 won't install on non-UEFI machines (AFAIK) and the Tosh NB280 certainly isn't UEFI enabled...
I've installed Ubuntu 14.04 on a very similar specced Eeee PC - 2GB RAM, Intel Atom N270 1.66GHz processor and it runs perfectly OK.
You'd be far better off installing it as dual-boot and not using Wubi. As you correctly say, Wubi doesn't work with Windows 8 anyway.

Actually Windows 8.1 :P. Works ok but it is heavy and eventually makes pc slow but it have many features. And how to dual-boot without wubi? I tired to do it with Android x86 but failed.

---

### Post by Impavidus on 2015-01-02
> **Gordonbp531 said:**
> I'm very surprised that Windows 8 even installed on your machine - Windows 8 won't install on non-UEFI machines (AFAIK) and the Tosh NB280 certainly isn't UEFI enabled...
I've installed Ubuntu 14.04 on a very similar specced Eeee PC - 2GB RAM, Intel Atom N270 1.66GHz processor and it runs perfectly OK.
You'd be far better off installing it as dual-boot and not using Wubi. As you correctly say, Wubi doesn't work with Windows 8 anyway.To be precise (if I'm correct), Wubi doesn't work with UEFI and all preinstalled Win8 computers use UEFI, so Wubi doesn't work on most Win8 systems. Therefore (and some other reasons) it's no longer supported. It was a confusing installation method anyway, and offers less performance than a real dual boot. It might work in your case, but isn't recommended.

> **shahbaz3 said:**
> Oh, didn't knew that wubi is not supported. Please suggest any one that would best suit as I can't test all :S Does each one have any difference between their software centers and terminal commands?The main difference between the different Ubuntu flavours and derivatives is the GUI. I don't know if they use different software centres, but any derivative using the same repositories (including the official flavours Lubuntu, Xubuntu and Kubuntu) has the same software available from the software centre. The terminal commands work exactly the same, except for the commands to control the GUI of course, but most users don't need them.

Xubuntu and Lubuntu are official lightweight Ubuntu flavours. They may perform better on less powerful hardware. Lubuntu is the lightest of them.

For installing, first read this: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by hakuna_matata on 2015-01-02
> **shahbaz3 said:**
> 
With Wubi right? I saw it doesn't works with Windows 8.
All official versions of Wubi don't work in UEFI mode. It is possible to install Windows 7 in UEFI mode and it is possible to install Windows 8 in non-UEFI mode. If you don't use UEFI, Windows version is not important. 

But Wubi is not easy to use because of other known issues, too:

14.04 and above: [bug 1317437]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1317437") workaround: [http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted](http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted)
14.04.1: [bug 1367071]("http://bugs.launchpad.net/wubi/+bug/1367071") workaround: [http://ubuntu-with-wubi.blogspot.ca/2014/10/installing-ubuntu-14041-with-wubi.html](http://ubuntu-with-wubi.blogspot.ca/2014/10/installing-ubuntu-14041-with-wubi.html)
14.10: [bug 1385930]("https://bugs.launchpad.net/wubi/+bug/1385930") workaround: [URL="http://ubuntuforums.org/showthread.php?t=2251986&p=13162861#post13162861"]http://ubuntuforums.org/showthread.php?t=2251986&p=13162861#post13162861

[/URL]So, try to avoid Wubi.

---

### Post by shahbaz3 on 2015-01-03
> **Impavidus said:**
> To be precise (if I'm correct), Wubi doesn't work with UEFI and all preinstalled Win8 computers use UEFI, so Wubi doesn't work on most Win8 systems. Therefore (and some other reasons) it's no longer supported. It was a confusing installation method anyway, and offers less performance than a real dual boot. It might work in your case, but isn't recommended.

The main difference between the different Ubuntu flavours and derivatives is the GUI. I don't know if they use different software centres, but any derivative using the same repositories (including the official flavours Lubuntu, Xubuntu and Kubuntu) has the same software available from the software centre. The terminal commands work exactly the same, except for the commands to control the GUI of course, but most users don't need them.

Xubuntu and Lubuntu are official lightweight Ubuntu flavours. They may perform better on less powerful hardware. Lubuntu is the lightest of them.

For installing, first read this: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Thanks for the info! Downloaded Lubuntu, made USB drive bootable and gonna flash now. And read that link too.

> **hakuna_matata said:**
> All official versions of Wubi don't work in UEFI mode. It is possible to install Windows 7 in UEFI mode and it is possible to install Windows 8 in non-UEFI mode. If you don't use UEFI, Windows version is not important. 

But Wubi is not easy to use because of other known issues, too:

14.04 and above: [bug 1317437]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1317437") workaround: [http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted](http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted)
14.04.1: [bug 1367071]("http://bugs.launchpad.net/wubi/+bug/1367071") workaround: [http://ubuntu-with-wubi.blogspot.ca/2014/10/installing-ubuntu-14041-with-wubi.html](http://ubuntu-with-wubi.blogspot.ca/2014/10/installing-ubuntu-14041-with-wubi.html)
14.10: [bug 1385930]("https://bugs.launchpad.net/wubi/+bug/1385930") workaround: [URL="http://ubuntuforums.org/showthread.php?t=2251986&p=13162861#post13162861"]http://ubuntuforums.org/showthread.php?t=2251986&p=13162861#post13162861

[/URL]So, try to avoid Wubi.

Oh I see, I am not gonna use Wubi.

---

### Post by shahbaz3 on 2015-01-04
Working fine, just a minor graphic glitch in floating notifications. I just have one problem, I want a VPN program to access blocked sites/apps like YouTube. I couldn't find a proper way, would be great if you can link/guide me.

---

### Post by billy_bob2 on 2015-02-11
> **shahbaz3 said:**
> It is Toshiba NB200-10z
Here are specs:

Processor: Intel Atom N280 @ 1.6 Ghz single core
RAM: 2GiB DDR2
Graphics: Intel GMA 950

Also I want to install it with my windows. With Wubi right? I saw it doesn't works with Windows 8. My netbook was preinstalled with Win XP. I have now Windows 8.1 + Tiny 7 (unofficial version of Win7) installed. If I install any version through Wubi, will my windows boot along with Ubuntu?

P.S: I have been using some random ubuntu version with USB flash drive.

Thanks for your help.
Hi shahbaz3, I have 14.04.1 LTS running on the exact same laptop without any problems. Startup takes about a minute, so it's not superfast.

---

