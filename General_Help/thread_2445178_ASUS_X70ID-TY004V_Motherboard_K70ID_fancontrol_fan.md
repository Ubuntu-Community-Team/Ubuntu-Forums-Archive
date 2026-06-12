---
title: "ASUS X70ID-TY004V Motherboard K70ID fancontrol fan speed 100%"
date: 2020-06-10
forum: General Help
---

### Post by gastonia on 2020-06-10
I have searched the internet about how to control the fan speed on **ASUS [COLOR=#ff0000]X70ID[/COLOR]-TY004V** Motherboard [COLOR=#ff0000]**K70ID**[/COLOR].
Current BIOS is #203, seems there is a [BIOS #205]("https://www.asus.com/Laptops/K70ID/HelpDesk_BIOS/") for K70ID, but I haven't found what the difference is.
It seems near impossible to update the BIOS, since the BIOS utility Easy Flash v1.14 accepts floppy disks only and wont mount CD-ROM nor USB-HDD.
There seems to be a way to update the BIOS with a DOS-utility AFLASH2.EXE, but it failed on a FreeDOS image on USB-stick made with Unetbootin.
Not knowing if a BIOS-upgrade might fix the fan issue, I am still at BIOS #203.
**[COLOR=#ff0000]EDIT[/COLOR]**: I finally managed to find another [AFLASH2.EXE]("http://ftp.tekwind.co.jp/pub/asustw/nb/Apps/Aflash2/V3.01/") from 2007 which did the job. Now I am at BIOS #205 (latest).

I tried several distros on this laptop  X70ID, but none has been able to reduce the fan which is constantly at 100% throttle, although not necessary. The CPU runs cool, still the fan is at max.
This is a quite common issue with ASUS laptops, which seems to have been addressed by Ubuntu 20.04. Somebody maybe knows how to deal with this. It should be possible to control the fans, but **how**?

I tried the proprietary NVIDIA driver as well, but the fan(s), maybe there are two fans in this laptop, keep spinning at maximum.

```

$ sensors
Core 0:       +43.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +41.0°C  (high = +105.0°C, crit = +105.0°C)

nouveau-pci-0200
Adapter: PCI adapter
GPU core:     +0.80 V  (min =  +0.80 V, max =  +0.95 V)
temp1:        +41.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

$ sudo pwmconfig
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```
`sudo sensors-detect` does not find any fan controls.
`sudo pwmconfig` cannot setup fancontrol.

Some threads point to an arch-linux solution called [asus-fan-control]("https://github.com/dominiksalvet/asus-fan-control"). It didn't do any change.
Some threads point to similar problems, like this one for [GL753VE]("https://rog.asus.com/forum/showthread.php?98775-LINUX-Fan-speed-issue-on-GL753VE-nvidia-bumblebee-bbswitch-ACPI"), which points to 
this [post]("https://github.com/Bumblebee-Project/Bumblebee/issues/764#issuecomment-559980823"). I didn't succeed to get any better fan behavior.

I also tried
```
sudo apt-get install tlp
sudo tlp start
```
but it didn't bite on the fan.

**I am sure someone knows how to fix this**, and maybe it would be great to make the installation take this into account right at a fresh install.

[COLOR=#ff0000]**All help is greatly appreciated.**[/COLOR]

---

### Post by CatKiller on 2020-06-10
> **gastonia said:**
> `sudo sensors-detect` does not find any fan controls.
That's the fundamental problem. Without a way to control the speed, there's no way to control the speed. 

If the manufacturer doesn't provide support for those chips then it has to be reverse engineered, which takes time and needs someone able to do it to have access to the hardware. 

You think support for your fan controller has been added in 20.04. Have you tried 20.04?

---

### Post by gastonia on 2020-06-10
I started off by installing Ubuntu Budgie 20.04, then Linux Mint 19.3 and now I installed Ubuntu 20.04 on the laptop X70ID. None of these three distros provide any effective fan control for this laptop, unfortunately.

In addition to this fan issue, `poweroff` seems to be the only way to shutdown or restart the laptop. Otherwise it hangs at the ubuntu logo and refuses to reboot, unless the powerbutton is pressed 2-3 seconds. I tried, as in another post, to use Alt + Sys Rq and then type `s`   `u`   `b` (which was supposed to shut it down), but that doesn't seem to work. Ctrl + Alt + Delete doesn't poweroff either. Funny...

There was one idea somewhere to use the coretemp and issue a command to control the fan, but I didn't find the way to control the fan in these distros. Previously, a Windows installation on the machine did control the fan so there should be a fan control possibility at least. I do not know why some manufacturers (ASUS?) would not provide the possibility to control the fans.

I read in some forum that there were some talks about Ubuntu 20.04 addressing the fan issue that at least some ASUS laptops seem to have, but that may be wrong. Somehow it should be possible to fix this I think, but you say it can't be fixed? It is quite tiring to hear the fans on 100% all the time... Everything else seem to work, just the loud fans destroy the peace.

I have finally succeeded to install BIOS #205 since last post. Used another [AFLASH2.EXE]("http://ftp.tekwind.co.jp/pub/asustw/nb/Apps/Aflash2/V3.01/") and booted FreeDOS made by [binary Unetbootin]("https://unetbootin.github.io/linux_download.html") image just as a live-CD without additional drivers (selected last option). Then `cd c:` and execute `aflash2` and type in the filename of the new BIOS-file-#205.

---

### Post by CatKiller on 2020-06-10
> **gastonia said:**
> I do not know why some manufacturers (ASUS?) would not provide the possibility to control the fans. 

Because they don't care. They aren't concerned that their firmware doesn't do what it's supposed to, as long as it can boot Windows, and having their fan controlled by their own software in Windows is a marketing opportunity. They've already got your money, so why would they be interested that it doesn't work for you? 

There are companies that sell computers with Linux pre-installed: Dell, Lenovo, System76, Tuxedo, and so on. If you want good Linux support from your hardware, buy one of those. 

> Somehow it should be possible to fix this I think, but you say it can't be fixed? 

You need the BIOS/UEFI to expose an interface for the cheapest-fan-controller-chip-they-could-find, work out what signals it provides, and work out the format of the signals you can give it, then put that information into a kernel module so that you can use the standard interface for controlling fans to control your fans. And hope that the cheapest-fan-controller-chip-they-could-find isn't a different chip when the manufacturer does the next production run.

The people that do that for all the other fan controllers don't have access to your hardware. They'll prioritise the ones that they have, and the easiest ones, and the popular ones if they get hold of a sample. If you get in touch with them there might be things you can do to help get that chip supported.

---

### Post by gastonia on 2020-06-10
Any chance you would know how to get in touch with relevant developers or development team for this fan issue on ASUS?

---

### Post by CatKiller on 2020-06-10
No idea at all, sorry.

I believe that the subsystem that handles hardware monitoring is called hwmon, which might give you a place to start.

---

### Post by gastonia on 2020-08-24
To let anyone reading this know: **Fan control works now**. I am not entirely aware of how it got fixed, but I suspect a recent update of the operating system has something to do with it working as expected now. To the developer who fixed it: THANK YOU!

---

