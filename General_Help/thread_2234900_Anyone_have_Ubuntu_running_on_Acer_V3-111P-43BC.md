---
title: "Anyone have Ubuntu running on Acer V3-111P-43BC?"
date: 2014-07-17
forum: General Help
---

### Post by cbraxton on 2014-07-17
I'm considering the purchase of an Acer Aspire V3-111P-43BC laptop (aka "NX.MP0AA.001") to replace an old, defunct Asus netbook. Has anyone here successfully run Ubuntu on one of these? Web searches have not turned up much aside from one note that Acer does not support Linux on this machine. (Which of course does not mean it will not work.)

Any info greatly appreciated, thanks!

---

### Post by TheFu on 2014-07-17
It is best to make a list of chips used for the different aspects of the machine and search for kernel support of each.

I'm running 14.04 on an Acer C720.  The important things work, though the touchpad needs a special driver that must be manually built for every new kernel and I've not gotten any bluetooth connection working v2 or v4 clients. Wifi and usb3 are working without any hassle.  Screen is working well, sound works for about 10 suspends, but not later, until a reboot. A weekly reboot avoids this issue.  Plus I love th 8+ hrs of real-world use battery life. It is a chromebook, so less than 2lbs, SSD, and limited ports (no VGA, no ethernet port, only 1 USB3), but for a travel netbook replacement and $200, I'm happy-ish.  Wish I'd have gotten the Dell 11inch instead.

Definitely check the wireless and BT chips carefully.

---

### Post by cbraxton on 2014-07-17
Looking around some more, I found the Asus X200CA-DH21T 11.6" laptop which has features overall similar to the Acer, but reviews say it runs Linux well. The CPU is a bit older (Intel Pentium dual-core 2117U in the Asus vs. Pentium quad-core N3530 in the Acer), but online comparisons show the two CPUs to be very close in performance and power consumption. The Asus is cheaper as well, so that's looking like a good choice.

---

### Post by swanduck on 2014-07-21
I ordered the Acer Aspire E3-111-P8DW over the weekend, which appears to be the same machine sans the touch screen.  It shows up tomorrow at which point I plan to replace the HDD with an SSD and install 14.04.  I will report back on how everything looks.

---

### Post by d98jh on 2014-07-22
I ordered the V3-111p version yesterday. Also planning to replace the HDD with an SSD right away. Thinking of replacing the wifi card as well. Will keep an eye on this thread.

---

### Post by swanduck on 2014-07-22
Received the machine today.  Installed the SSD.  Booted and installed 14.04 from a USB drive.  No need to disable Secure Boot or switch away from UEFI.  I have only spent of a few minutes with the machine post install, but so far so good.

Function keys work.
Lid closure triggered suspend, but needed to hit a key on the keyboard to resume.
Bluetooth and WiFi are functional.
2 finger scrolling works.
Webcam works.
Internal microphone is functional.

So far, I am very happy with the machine. I am continuing to test, but let me know if there is anything specific I should look at.

---

### Post by d98jh on 2014-07-23
I received mine today as well. Swapped the HDD out for an SSD and replaced the wifi card with an Intel AC 7260 card.
Almost everything works out of the box. The only change I've made is to fix the Fn-keys that adjust the screen brightness according to this guide: [http://askubuntu.com/questions/180819/how-to-control-brightness-on-acer-laptop](http://askubuntu.com/questions/180819/how-to-control-brightness-on-acer-laptop).
Really happy with it so far. Would have liked the laptop to wake up from suspend when the lid is opened but that's not a major headache.

---

### Post by mr-mechano on 2014-08-01
> **swanduck said:**
> Received the machine today.  Installed the SSD.  Booted and installed 14.04 from a USB drive.  No need to disable Secure Boot or switch away from UEFI.  I have only spent of a few minutes with the machine post install, but so far so good.


Hi there,
I'm considering this machine too.

I also want to fill with an SSD. But I want to know if I'll have full Sata3 speed of +500MB/s.

Please can you check with the commands described into this guide, if it's a Sata2 or Sata3 link when a Sata3 SSD is inserted?

[http://www.cyberciti.biz/faq/linux-command-to-find-sata-harddisk-link-speed/](http://www.cyberciti.biz/faq/linux-command-to-find-sata-harddisk-link-speed/)

---

### Post by mr-mechano on 2014-08-01
> **d98jh said:**
> I received mine today as well. Swapped the HDD out for an SSD and replaced the wifi card with an Intel AC 7260 card.
Almost everything works out of the box. The only change I've made is to fix the Fn-keys that adjust the screen brightness according to this guide: [http://askubuntu.com/questions/180819/how-to-control-brightness-on-acer-laptop](http://askubuntu.com/questions/180819/how-to-control-brightness-on-acer-laptop).
Really happy with it so far. Would have liked the laptop to wake up from suspend when the lid is opened but that's not a major headache.


Hi there,
I'm considering this machine too.


I also want to fill with an SSD. But I want to know if I'll have full Sata3 speed of +500MB/s.


Please can you check with the commands described into this guide, if it's a Sata2 or Sata3 link when a Sata3 SSD is inserted?


[http://www.cyberciti.biz/faq/linux-c...sk-link-speed/](http://www.cyberciti.biz/faq/linux-c...sk-link-speed/)

---

### Post by d98jh on 2014-08-02
Seems like the chipset is only Sata2:
```

$ dmesg | grep -i sata | grep 'link up'
[    1.634047] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)

$ sudo smartctl -a /dev/sda | grep "^SATA"
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)

```

---

### Post by tobimensch2 on 2014-08-05
I'm using the same laptop on Fedora 20 with latest updates.

Please don't stone me for coming to the Ubuntu forum.

):P

I like this little laptop a lot. Most things work out-of-the-box on Fedora, too.

With the original kernel 3.11 the touchpad worked, but with the latest
3.15.7 in Fedora it doesn't.
So I'm interested, if this problem is the same on Ubuntu depending on kernel version.

But I can do without touchpad for the most part.

I've never got bluetooth working. It's recognized and I can switch it on and of
as well as enable visibility, but it never finds devices when scanning. While
my bluetooth-stick works instantly.

I guess that's a kernel problem, too.

Is bluetooth working on Ubuntu? If so, what kernel version?

Thanks guys/gals

---

### Post by d98jh on 2014-08-06
> **tobimensch2 said:**
> 
With the original kernel 3.11 the touchpad worked, but with the latest
3.15.7 in Fedora it doesn't.
So I'm interested, if this problem is the same on Ubuntu depending on kernel version.

The touchpad works for me with kernel 3.13, 3.14, 3.15 and 3.16. The only problem I've had with the latest kernels is that it stops working after suspend. Reloading the i2c_hid module remedies that.

> **tobimensch2 said:**
> 
Is bluetooth working on Ubuntu? If so, what kernel version?

Haven't tried bluetooth at all except disabling it. I can try later today.

Also, the memory card reader is not working properly for me. Does it work for you in Fedora?

---

### Post by tobimensch2 on 2014-08-06
[COLOR=#000000]Thanks for your feedback d98jh!

[/COLOR][COLOR=#000000]> [/COLOR][COLOR=#000000]The touchpad works for me with kernel 3.13, 3.14, 3.15 and 3.16. The only problem I've had with the latest kernels is that it stops working after suspend. Reloading the i2c_hid module remedies that.[/COLOR][COLOR=#000000][/COLOR][COLOR=#000000]

Does the touchscreen work, too? My theory is that maybe my touchpad doesn't work because the touchscreen does work and somehow the kernel/Xorg don't handle them both at once on Fedora.

[/COLOR][COLOR=#000000]> [/COLOR][COLOR=#000000]Also, the memory card reader is not working properly for me. Does it work for you in Fedora?[/COLOR][COLOR=#000000]

Yeah, seems to be working alright. Can access some pictures and delete them.
[/COLOR]

---

### Post by d98jh on 2014-08-06
> 
Does the touchscreen work, too? My theory is that maybe my touchpad doesn't work because the touchscreen does work and somehow the kernel/Xorg don't handle them both at once on Fedora.


Yes, the touchscreen works too.

---

### Post by d98jh on 2014-08-06
Apparently the i2c_hid module is blacklisted by default in Ubuntu 14.04 [https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/14.04#Kernel](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/14.04#Kernel)

Try blacklisting it and see if that helps.

---

### Post by d98jh on 2014-08-06
> 
Is bluetooth working on Ubuntu? If so, what kernel version?

Just tried sending a file to my phone over Bluetooth and it worked just fine. Kernel 3.13

---

### Post by tobimensch2 on 2014-08-07
> [COLOR=#000000]Just tried sending a file to my phone over Bluetooth and it worked just fine. Kernel 3.13[/COLOR]

With kernel-3.13.10 at least the touchpad works. So: Yay!

No luck with bluetooth though. Keeps not finding devices. Will try to find
help for this and/or find a bug report on Fedora sites. But at least
I know now that in theory it should be working, since it is reportedly working in Ubuntu.

---

### Post by tobimensch2 on 2014-08-07
[COLOR=#000000]Hello d98jh,

your lspci and lsusb output could be useful to debug this. In mine bluetooth doesn't seem to show up.

Greetings[/COLOR]

---

### Post by d98jh on 2014-08-07
Not sure that it will help since you probably don't have the same Intel 7260 wifi+bt card that I have but here is the output for future reference.

lspci:
```

00:00.0 Host bridge: Intel Corporation ValleyView SSA-CUnit (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation ValleyView Gen7 (rev 0e)
00:13.0 SATA controller: Intel Corporation ValleyView 6-Port SATA AHCI Controller (rev 0e)
00:14.0 USB controller: Intel Corporation ValleyView USB xHCI Host Controller (rev 0e)
00:1a.0 Encryption controller: Intel Corporation ValleyView SEC (rev 0e)
00:1b.0 Audio device: Intel Corporation ValleyView High Definition Audio Controller (rev 0e)
00:1c.0 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1c.1 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1c.2 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1f.0 ISA bridge: Intel Corporation ValleyView Power Control Unit (rev 0e)
00:1f.3 SMBus: Intel Corporation ValleyView SMBus Controller (rev 0e)
02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)

```

lsusb:
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b452 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 04f3:0430 Elan Microelectronics Corp. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by Nodens on 2014-08-13
Hey ! Received this small laptop (V3-111P-P6TC) yesterday. I swapped the hdd for a sdd and installed xubuntu 14.04. 
Almost everything worked out of the box. I had to made the small correction in grub config for brightness adjustement with fn keys, and bluetooth doesn't work. It doesn't detect any devices. 
Strangely I think I have the same lspci and lsusb output. I will post mine later to compare. 
Anyway completely satisfied of this small machine !

---

### Post by Nodens on 2014-08-13
I read back in the thread and if I don't mistakes, d98jh, you replaced the wifi card by an intel. I think that's the reason why your bluetooth work and tobimensh2 and mine not. 
Do you see an improvement by this replacement ? I imagine you made it for AC ?

---

### Post by d98jh on 2014-08-13
Yes, I definitely see some improvements. With the original card I would only get around 40 mbit download speed and with the Intel card I max out my 100mbit ISP link.

---

### Post by d98jh on 2014-08-13
I'm having some serious trouble with my touchpad though, the cursor starts jumping erratically every few minutes or so.

Have you noticed any problems?

---

### Post by Nodens on 2014-08-13
Ok so it may be a good improvement plus the bluetooth.

No problem with the touchpad but I used it less than 6hours. Will see in a week.

---

### Post by Nodens on 2014-08-18
I tried the hdmi output yesterday. But it seems to be not working. I tried an update of the intel graphics drivers without more success. Do you tried ?

---

### Post by d98jh on 2014-08-19
Yes, it works for me. What is the output of 'xrandr -q' when you connect the hdmi cable?

---

### Post by Nodens on 2014-08-21
Hey, sorry for the late answer. Finally it works ! I think I didn't fully plug the cable the first time :) Yeah !

---

### Post by richardgodbee on 2014-08-31
> **d98jh said:**
> I received mine today as well. Swapped the HDD out for an SSD and replaced the wifi card with an Intel AC 7260 card.
I'm thinking about buying a V3-111P and swapping the wireless card, except with an Intel Advanced-N 6235 (dual-band 2x2 802.11n + Bluetooth) that I already have.  Have you used yours in the 5 GHz band much?  I'm worried that the laptop's antennas were only designed for 2.4 GHz and won't perform very well when connecting to 5 GHz access points.  Thanks!

---

### Post by d98jh on 2014-09-01
> **richardgodbee said:**
> I'm thinking about buying a V3-111P and swapping the wireless card, except with an Intel Advanced-N 6235 (dual-band 2x2 802.11n + Bluetooth) that I already have.  Have you used yours in the 5 GHz band much?  I'm worried that the laptop's antennas were only designed for 2.4 GHz and won't perform very well when connecting to 5 GHz access points.  Thanks!

Yes, it connnects to the 5GHz MAC address of my router by default. As I wrote earlier it maxes out my 100Mbit ISP connection and that's fast enough for me at least. Anything specific you want me to test?

---

### Post by richardgodbee on 2014-09-11
> **d98jh said:**
> Yes, it connnects to the 5GHz MAC address of my router by default. As I wrote earlier it maxes out my 100Mbit ISP connection and that's fast enough for me at least. Anything specific you want me to test?
I'm not sure what I could have you test without having access to test equipment (a spectrum analyzer and VSWR bridge). Since it's working well for you, I guess I'll go on and buy the laptop and give it a try myself. Thanks for the reply!

---

### Post by Nodens on 2014-09-18
> **d98jh said:**
> I'm having some serious trouble with my touchpad though, the cursor starts jumping erratically every few minutes or so.

Have you noticed any problems?

Hey ! I have this problem too ! All was ok, but yesterday the cursor start jumping. If I disable the touchpad it's ok but it's not a good solution because I don't want to plug a mouse. 
Do you find something ?

---

### Post by d98jh on 2014-09-19
No, unfortunately not. I had some other issues with mine as well, so I sent it to Acer for repair.

---

### Post by Nodens on 2014-09-27
Thanks d98jh for your answer. I found your message on arch forum about the kernel option. I tried it but without succes. I updated my ubuntu on the beta 14.10. So i'm now on the new kernel 3.16. The problem is however still present. 
I tried a manjaro live usb but the problem appears too. I don't now if the problem is software of hardware. I didn't use windows so i don't now if the problem appears there too. I will propably try during the next week. 
Do you get back your netbook ? Do they change something ?

---

### Post by d98jh on 2014-09-28
I'm still waiting for them to return it. I sent it in on September 16 so I hope it doesn't take much longer.
I had problem in Windows as well. The cursor didn't jump around but froze instead.

---

### Post by Nodens on 2014-09-29
And for the return you put back the windows harddrive ? I will maybe wait that you received it to see if the problem is solved.

---

### Post by Nodens on 2014-09-30
I think i found a solution for the crazy touchpad. I didn't test it for a very long time but it seems that the problem disappears when psmouse module is blacklisted. Found on the [ArchWiki]("https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Cursor_jump").

---

### Post by d98jh on 2014-10-01
I also tried using the i2c_hid module instead of psmouse but that didn't work for me. I hope it works out better for you.

My problem seems to be both hardware and software related though since the cursor never jumped around in Windows the touchpad would simply stop working.

I finally got an update from Acer this morning that my laptop had been repaired and will be returned to me so I hope that they solved it.

---

### Post by d98jh on 2014-10-01
> **Nodens said:**
> And for the return you put back the windows harddrive ? I will maybe wait that you received it to see if the problem is solved.

Yes, I put back the harddrive and the original WLAN card before I sent it for repair.

---

### Post by Nodens on 2014-10-04
Ok I used the pc for a few days and made more test with the module. This is what run for me : 
1 : blacklist psmouse and i2c_hid (in /etc/modprobe.d/blacklist)
2 : create a file name i2c_hid in : /etc/pm/config.d
3 : edit it to add : SUSPEND_MODULES="i2c_hid"

1 is for the jumping cursor. I tried to blacklist only psmouse or only i2c_hid without effect. 
2 and 3 to use the touchpad after a suspend. 

Hope this can be useful.

---

### Post by tobimensch2 on 2014-11-15
Good news!

After using bluetooth via a dongle for many months I finally found a fix and now the original bluetooth works fine!

I searched for the device vendor/product id on google and found that someone had recently made a commit to
add acer support for 0489:e0789 . Which is our bluetooth!

This is the commit: (Thanks ananthk!)
[https://github.com/linux-wpan/linux-wpan-next/commit/d07497bfdad462799f11fecdc5a365f0ab9d1fda](https://github.com/linux-wpan/linux-wpan-next/commit/d07497bfdad462799f11fecdc5a365f0ab9d1fda)

I'm now running a vanilla mainline kernel-3.18, but I'm not sure that it's neccessary to make this work.

What you need to get from this commit are the btusb.c and ath3k.c files and compile them into kernel modules,
then you need to replace the modules that are in /lib/modules/your_kernel/kernel/drivers/bluetooth

I rebooted, but don't know if you have to. At first it still didn't work, but then I saw that ath3k for some reason wasn't loaded
at all.

After a simple modprobe ath3k something amazing happened. My device was found and my headset just works. (tm)

Hope this helps someone.

And hope this patch gets merged into the kernel sooner rather than later.

Don't know if this was mentioned here, but another problem for me was that reboot/start often ended hanging.
After I blacklisted dw_dmac it worked every time with no downside that I see so far.

So there's only one issue unsolved left. The damn touchpad.

I thought briefly it was solved by i8042.nomux=1 i8042.rest kernel parameters, but it really wasn't.
That's the last thing that doesn't work! I think it's strange that it works for longer periods and then suddenly goes crazy.
At least you can disable/enable it with FN+F7.

---

### Post by tobimensch2 on 2014-11-19
I solved some DRM issues by building the latest upstream kernel from
[http://cgit.freedesktop.org/drm-intel/](http://cgit.freedesktop.org/drm-intel/) .

I experienced some hangs with a second monitor and many DRM errors in dmesg and they're all
gone, apparently. Also seems fairly stable so far.

Also with this kernel I don't need to build custom kernel modules, since bluetooth is already working
out-of-the-box!

There's really only one problem left with Linux on this Laptop: The touchpad. :mad:

Can someone file a bugreport about that on launchpad please? Because I'm really
a Fedora user, so I can't do that, but I think we need to get developers to take a look at the issue
from all angles.

Please. Please. Pretty Please.

Besides that issue this laptop now runs 100% perfect, I mean it's really running awesome,
just the touchpad is spoiling it all. (If you want to use your laptop as a mobile device that is)

---

### Post by harctan on 2015-03-07
Hello all, I have an Acer E3-112 laptop and I experience the same problem with the touchpad cursor jumping around. The specs are Intel Celeron N2840, Intel HD Graphics, 2 GB DDR3 Memory, 500 GB HDD, Synaptics clickpad. It comes with Windows 8.1 64bit preinstalled and I dual-boot with Linux Mint Xfce 17.1 64bit. I have tried booting with i8042.nomux=1 i8042.reset kernel parameters and blacklisting i2c_hid and psmouse and although there seems to be some improvement the problem still persists. In Windows the touchpad works fine so it seems to be a software issue. I have also tried different kernels and various Linux distributions but I still get the same erratic cursor movement, usually up and down very fast until I disable and re-enable the touchpad with the shortcut keys (Fn-F7). Other than that everything works just fine (with the 3.16.0-30 kernel). Are there any updates on this problems?

---

### Post by d98jh on 2015-03-17
> **harctan said:**
> Hello all, I have an Acer E3-112 laptop and I experience the same problem with the touchpad cursor jumping around. The specs are Intel Celeron N2840, Intel HD Graphics, 2 GB DDR3 Memory, 500 GB HDD, Synaptics clickpad. It comes with Windows 8.1 64bit preinstalled and I dual-boot with Linux Mint Xfce 17.1 64bit. I have tried booting with i8042.nomux=1 i8042.reset kernel parameters and blacklisting i2c_hid and psmouse and although there seems to be some improvement the problem still persists. In Windows the touchpad works fine so it seems to be a software issue. I have also tried different kernels and various Linux distributions but I still get the same erratic cursor movement, usually up and down very fast until I disable and re-enable the touchpad with the shortcut keys (Fn-F7). Other than that everything works just fine (with the 3.16.0-30 kernel). Are there any updates on this problems?

I'm a bit ashamed to admit it but I still haven't installed Ubuntu on mine after getting it back from Acer (who replaced the touchpad). I tested the 14.04.2 live USB stick though and the touchpad didn't work at all. Didn't bother to find out why but instead went ahead and tried the latest daily 15.04 live stick and that worked great.
Couldn't tell you if the replaced touchpad is what solved it for me(seems likely though) or if it's the new driver in 15.04.

---

### Post by harctan on 2015-03-18
I just tried the latest Ubuntu 15.04 via a live USB stick on my acer aspire E3-112 and the problem with the touchpad still persists.

---

### Post by d98jh on 2015-03-19
> **harctan said:**
> I just tried the latest Ubuntu 15.04 via a live USB stick on my acer aspire E3-112 and the problem with the touchpad still persists.

Sorry to hear that. Then my best guess is that you will need to send it to Acer to replace the touchpad like I did to remedy the problem.

---

### Post by harctan on 2015-03-19
> **d98jh said:**
> Sorry to hear that. Then my best guess is that you will need to send it to Acer to replace the touchpad like I did to remedy the problem.

Thank you for the suggestion, but since the touchpad works fine in windows 8.1 which came preinstalled I doubt that acer would replace the touchpad under warranty.

---

### Post by Nodens on 2015-03-20
Hey guys ! I think I've solved the problem on mine. I read on internet that cursor jumping is due to a lack of isolation between the battery and the touchpad ([https://bbs.archlinux.org/viewtopic.php?id=185946]("https://bbs.archlinux.org/viewtopic.php?id=185946")). 
I made the reparation myself (adding electrical tape on the touchpad circuit), and since, no more jumping cursor. Bonus, the touchpad feels more adjusted.

---

### Post by harctan on 2015-03-20
Hey Nodens, I had read that post too. The person that suggested that fix experienced problems under both Linux and Windows which suggested a hardware issue. Was that the case with you too? In my laptop (aspire E3-112) the touchpad works fine under Windows 8.1 so it seems more probable to me that there may be some incompatibility with the Linux kernel. Since in my case it looks more of a software issue I'm reluctant to do any hardware tinkering yet.

---

### Post by vladislav3 on 2015-03-25
[**[COLOR=#000000]Nodens[/COLOR]**]("http://ubuntuforums.org/member.php?u=279491"),

could you please describe what exactly did you do? Did you just cover the hole through which the PCB can be seen or the entire touchpad? What kind of tape did you use? I have tried covering the PCB, but it didn't fix the problem (Acer V3-371). I believe it's a hardware problem since cursor can freeze in Windows.

---

### Post by Nodens on 2015-03-26
Hey ! I don't know if the problem persists on windows on mine because I swapped for a ssd the first day and didn't try the old dd. 
But I tried as many software solution as I can find on internet forum but without success. When I tried the tape solution, it was the last idea before sending back to Acer. 
I used electrical tape, and I cover the zone under the batterie like on the image :
[[img]http://tof.canardpc.com/preview/4e7a7a2b-96f6-4dd3-9a8f-caa4f95d80f6.jpg[/img]](http://tof.canardpc.com/view/4e7a7a2b-96f6-4dd3-9a8f-caa4f95d80f6.jpg)

---

### Post by vladislav3 on 2015-03-26
Thanks, I'll try this one too and post a result in a week or two.

---

### Post by harctan on 2015-03-28
> **Nodens said:**
> Hey ! I don't know if the problem persists on windows on mine because I swapped for a ssd the first day and didn't try the old dd. 
But I tried as many software solution as I can find on internet forum but without success. When I tried the tape solution, it was the last idea before sending back to Acer. 
I used electrical tape, and I cover the zone under the batterie like on the image :
[[IMG]http://tof.canardpc.com/preview/4e7a7a2b-96f6-4dd3-9a8f-caa4f95d80f6.jpg[/IMG]]("http://tof.canardpc.com/view/4e7a7a2b-96f6-4dd3-9a8f-caa4f95d80f6.jpg")

From the photo it looks like you placed the electrical tape on the side of the battery that is facing the bottom cover and not on the side that is facing the touchpad. Am I correct on this? I am asking because the problem is supposed to be the lack of insulation between the battery and the touchpad so it would make more sense to place the tape there.

---

### Post by xt10-20zp9 on 2015-03-29
Hi, 
i have the same V3-111P-27AC and i used to have Ubuntu in dual-boot, now I run Elementary Freya Beta 2 with Win 8.1
I started having the same problems on Linux a few days ago, the pointer would start jumping around until i disable the touchpad with the shortcut... i thought it was a Linux problem. And today that i'm using it on Windows i realized the touchpad would freeze quite frequently, for a few seconds or longer till i hit the touchpad shortcut.

I re-installed the Windows Synaptics driver and removed a bunch of Acer crapware, even if thought it should be a hardware problem.

I saw something about a touchpad fix in the latest BIOS update and this from the Acer assistance [http://acer--uk.custhelp.com/app/answers/detail/a_id/34320/~/bios-update-may-resolve-unresponsive-touchpad-in-windows-8.1](http://acer--uk.custhelp.com/app/answers/detail/a_id/34320/~/bios-update-may-resolve-unresponsive-touchpad-in-windows-8.1)

So i updated the BIOS (1.05 to 1.29 i think) but with no change.

i saw another page on Acer Assistance mentionning that since a Windows update several problems had appeared including some touchpad problems, which are unresolved for now. The advice to uninstall some Intel thing... well i isn't installed on mine anyway.

I also saw in Youtube comments and in Acer forums someone mentionning an Intel driver which oddly enough seems to be for Atoms chipset (but i know those Celeron and Pentium systems are similar to some Atoms - or at least, that's what i read somewhere.) : 

[http://community.acer.com/t5/Notebooks-Netbooks/Acer-V3-111P-touchpad-doesn-t-work/td-p/279732](http://community.acer.com/t5/Notebooks-Netbooks/Acer-V3-111P-touchpad-doesn-t-work/td-p/279732)
[https://www.youtube.com/watch?v=4y-Mgf8iK_c](https://www.youtube.com/watch?v=4y-Mgf8iK_c)

So, oddly, it seems that to have installed this driver solved my touchpad problem on Windows. And i'm wondering if that's a hardware problem now.

I was thinking of sending it to repair or trying that electrical tape thing... but for now i guess, I'll use some more on Windows today to see if the problem re-appears, but for now it's been working for a while whereas before i would get the problem every 2 or 5 minutes.

And i guess I'll reboot on Elementary OS after that to see if the problem still happens... (although i don't know if my touchpad problem on Elementary was as frequent as on Windows).

Well, anyway, this is weird. I will report back...

About the pic for the electrical tape, i guess it's meant to be on the other side like you say, that picture of the laptop comes from [http://liliputing.com/2014/07/acer-aspire-v11-fanless-touchscreen-laptop-review.html](http://liliputing.com/2014/07/acer-aspire-v11-fanless-touchscreen-laptop-review.html) 

Is the battery hard to remove to put some electrical tape? I'm used to open Macbooks to replace HDDs and RAM, but some PC laptops are a pain to open...

edit: There's a video of the disassembly of those models here, 

[https://www.youtube.com/watch?v=5OT_RnjMess](https://www.youtube.com/watch?v=5OT_RnjMess)

(Only two screws to remove the battery.)

---

### Post by xt10-20zp9 on 2015-03-31
> **Nodens said:**
> Hey ! I don't know if the problem persists on windows on mine because I swapped for a ssd the first day and didn't try the old dd. 
But I tried as many software solution as I can find on internet forum but without success. When I tried the tape solution, it was the last idea before sending back to Acer. 
I used electrical tape, and I cover the zone under the batterie like on the image :
[[IMG]http://tof.canardpc.com/preview/4e7a7a2b-96f6-4dd3-9a8f-caa4f95d80f6.jpg[/IMG]]("http://tof.canardpc.com/view/4e7a7a2b-96f6-4dd3-9a8f-caa4f95d80f6.jpg")

The problem re-appeared on Windows and i haven't used Linux/Elementary  (based on Ubuntu) a lot lately on it, to really say, but i had another  weird kind of touchpad/pointer behavior on Linux one time. Some times it  seems to work fine again tho for some time.

I would really like  to know too exactly where did you put the electrical tape to fix this... else i  might just send it to repair. (But i'm tired of dealing with after-sale  service so often lately...)

---

### Post by john389 on 2015-04-08
I've been having similar issues regarding the touchpad with an Acer V3-112. My thoughts are that is it caused by a hardware problem but they have put in some code in their Windows driver that attempts to disable the malfunctioning (so it is more visible on linux).

After today where the mouse continually went haywire I pulled my laptop apart to try and fix it. It is pretty easy to do. Just a few screws and popping off the bottom plate and removing the battery screws.

Here is what my touchpad looks like. Note the yellow tape. I thought that this yellow tape could possibly be an attempt to insulate part of the touchpad. I'm confused if this would work as the touchpad rests against the battery which is insulated anyway. Also note the two square black spacers.

[ATTACH=CONFIG]261171[/ATTACH]

I removed the yellow tape and replaced it with a decent amount of white insulation tape.

[ATTACH=CONFIG]261172[/ATTACH]

As an additional step, and something I do not recommend, I pulled the metal bump (that the touchpad hits when clicked) up a little. This is the bump by the middle screw with the circle indent. I thought that maybe this was bumping against the plate randomly and causing the jitter.

Results: mousepad hasn't gone haywire. I'll post again in a week if it is still working.

---

### Post by vladislav3 on 2015-04-08
I wonder how the insulation applied can help, there are no exposed contact pads or wires. It would be great if we can get a confirmed result, so I'm waiting for [**[COLOR=#000000]john389[/COLOR]**]("http://ubuntuforums.org/member.php?u=1978051")'s reply.

---

### Post by xt10-20zp9 on 2015-04-08
I had contacted the Acer assistance the other day, sent a message to something like "asking for a repair" and after i described the problem on Windows and Linux they directly sent me a message with the needed things to sent them the package to repair (as it's still under warranty). And i sent it today... so I'll see if i know what kind of repair they'll do.

---

### Post by xt10-20zp9 on 2015-04-10
Little update: 
Acer got the laptop this morning, and it's repaired a few hours later, ready to be shipped again, apparently. For now i don't know what they did, but at least it's fast.

---

### Post by john389 on 2015-04-12
Have had no mouse jitters so far! vladislav3 I'm also confused about the insulation making a difference. Maybe it was just that act of opening my case. I opened the case before and it did make a difference to the jitter. Definitely a hardware influenced issue.

---

### Post by vladislav3 on 2015-04-13
> **john389 said:**
> Maybe it was just that act of opening my case. I opened the case before and it did make a difference to the jitter.
That's what I'm worried about. I have did it before, but only have covered a hole in the metal plate (as shown in the picture), and it worked for about a week, but then the problem appeared again.

[ATTACH=CONFIG]261262[/ATTACH]

---

### Post by xt10-20zp9 on 2015-04-14
So I got back my V3-111P-27AC from Acer and they did replace the touchpad completely...

---

### Post by harctan on 2015-04-15
So I finally opened the case and placed electrical tape on the side of the battery that faces the touchpad. 3 days have passed since and I had no problem with the cursor going crazy so far. The problem seems to have been fixed but I will report back in a week or so for confirmation or sooner if anything changes.

---

### Post by vladislav3 on 2015-04-23
I have also added an electrical tape to the touchpad. It worked for two days, but then the problem appeared again. However, cursor is not that crazy now and the issue is not that persistent. The model is acer aspire v3-371, but touchpad looks the same and behaves exactly like described in this thread.

That being said, this fix sometimes does not work. Regarding the isolation question: it is possible the issue is mechanical rather than electrical, and adding a number of tape layers somehow helps (in my case I probably need to add some foam tape).

xt10-20zp9, do you by chance have a photo of the back side of the touchpad? Just to compare markings and components on the PCB.

---

### Post by harctan on 2015-04-29
After a week I experienced no problems with the touchpad so I would consider the problem solved for me.

---

### Post by xt10-20zp9 on 2015-05-11
[**[COLOR=#000000]vladislav3[/COLOR]**]("http://ubuntuforums.org/member.php?u=1901877"): sorry no i don't have a pic as i haven't opened it. And i don't really feel like opening it if i don't really have to... as the case and all feel really light and cheap. :/

Although i have a question, do any of you with a V3-111P or similar successfuly booted another distro from a live usb?

I really have no idea why but i suddenly got a Grub prompt and i don't know what happened. Could it be because i tried disabling SecureBoot? (I tried re-enabling it.)

And i tried disabling Secure Boot because it seems i can't boot any other distro that isn't Ubuntu or Ubuntu-based.. (haven't tried Debian)

If i need to re install i would have liked to install Manjaro-XFCE (based on Arch) but it's impossible to boot it :/ And i actually already had a problem booting a flash drive installation too, that i could boot on my Macbook. So, annoying... i don't understand why this happen.

---

### Post by xt10-20zp9 on 2015-05-25
it took me some time to reinstall Linux and I had a bad surprise. It took me some time cause i tried everything to install Manjaro and couldn't in the end (i can only boot Ubuntu/Ubuntu based distros).
I'm not sure but i think the touchpad worked slightly better on Elementary (14.04) than the Ubuntu release i tried, when it was working of course. And so once i tried to boot a live usb Ubuntu or Ubuntu-gnome since they replaced the touchpad and saw the touchpad was weird and so i decided to re install Elementary.

So, the touchpad before was working * perfectly * on Elementary, for instance i could simply click with my thumb on the bottom of the touchpad and move a window with my index finger... like it should be. And the touchpad was deactivated when i was typing so the cursor wouldn't click on anyting. But now i can't click and move a window like that, if I click with my thumb on the bottom of the touchpad and try to move a window with another finger it's impossible to move it. If i want to move a window, i have to, for instance, click with my index finger on the window, so like in the middle of touchpad and keep it clicked while i drag it around.. it's unusable :/ (and it works like it should on Windows.)

And i only use this Acer as netbook there is no way i will use/could use a mouse with it. So i guess when they replaced the touchpad they put another model in it, that requires another driver...? I guess that would explain?... I think i heard it's possible to "configure"/tweak a touchpad but i've never done it, i haven't googled yet, anyone has any pointer on what i could try to fix that problem? If it's fixable...? it kinda sucks. :/

---

### Post by chbrant7-gmail on 2015-05-30
hi, i did the tape repair and it work, thanks...

---

### Post by vladislav3 on 2015-07-21
So finally I had my notebook fixed in service. They soldered a wire from touchpad PCB ground to its metal frame and added a piece of conductive tape from touchpad frame to main frame. There already was some piece of tape which is supposed to be conductive (I guess), but looks like it becomes loose over time. So the touchpad wasn't properly grouded.

Sorry for a blurry photo (mirror: [http://i.imgur.com/ZIET5Zf.jpg](http://i.imgur.com/ZIET5Zf.jpg) ).

---

### Post by mr-mechano on 2016-06-24
> **chbrant7-gmail said:**
> hi, i did the tape repair and it work, thanks...


Me too.
Thick rubber adhesive tape and the cursors doesn't jump anymore.

There's a resonance phenomenon that cause the electricity into the battery to interfere with the trackpad.

---

