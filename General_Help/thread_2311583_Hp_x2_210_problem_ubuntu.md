---
title: "Hp x2 210 problem ubuntu"
date: 2016-01-28
forum: General Help
---

### Post by andrea100 on 2016-01-28
hi guys, i have an huge problem..1 week ago i bought this laptop detachable with win 10 pro on it, this laptop have a quad core + intel hd graphic + emmc 32gb and have an atom x5-z8300! ill tryed all the ubuntu version but every time freeze a the boot screen..ill tryed all the ubuntu release, from 14.10 to 15.10, lubuntu, kubuntu, linux mint..all of these freeze..can you explain me the problem please? i tryed to add: nomodeset, but freeze anyway....(only ubuntu 14.10 with nomodeset not freeze, but have a bug, i can't see the desktop, because have flickering... on ubuntu 15.10 with nomodeset, no detect my emmc = i can't install..and in live it freeze...who have this problem too?

---

### Post by Markus_Wolf on 2016-01-31
Hi Andrea100,
since I am interested into this new and interesting device I was looking for anybody who tried to install Ubuntu on it. So I stumbled across your post. As an Ubuntu user for many years I always wanted to have a true (and unlike Android still open) Linux system on a mobile device. So I am quite disappointed to hear that you were not successful when you tried to install Ubuntu on this device. So I have some questions that might help you to identify the problem:

- Have you tried to install the new 16.04 alpha version of Ubuntu, too? It comes with a 4.3 kernel which should support more modern hardware than kernel 4.2 of Ubuntu 15.10. You can download it from [http://cdimage.ubuntu.com/ubuntu/daily-live/current/](http://cdimage.ubuntu.com/ubuntu/daily-live/current/)

- What have you done to get the Live medium to boot? Did you modify any settings in the UEFI BIOS? (Although it is unlikely that this is related with the kernel problems later, it is just interesting to know)

- Have you tried the 64bit or the 32bit version?

---

### Post by andrea100 on 2016-02-01
> **Markus_Wolf said:**
> Hi Andrea100,
since I am interested into this new and interesting device I was looking for anybody who tried to install Ubuntu on it. So I stumbled across your post. As an Ubuntu user for many years I always wanted to have a true (and unlike Android still open) Linux system on a mobile device. So I am quite disappointed to hear that you were not successful when you tried to install Ubuntu on this device. So I have some questions that might help you to identify the problem:

- Have you tried to install the new 16.04 alpha version of Ubuntu, too? It comes with a 4.3 kernel which should support more modern hardware than kernel 4.2 of Ubuntu 15.10. You can download it from [http://cdimage.ubuntu.com/ubuntu/daily-live/current/](http://cdimage.ubuntu.com/ubuntu/daily-live/current/)

- What have you done to get the Live medium to boot? Did you modify any settings in the UEFI BIOS? (Although it is unlikely that this is related with the kernel problems later, it is just interesting to know)

- Have you tried the 64bit or the 32bit version?

with the alpha version work great without problem! this is the only working version! thanks so much man!
edit: now i don't have the battery status..can you help me to install it?

---

### Post by Markus_Wolf on 2016-02-05
Hi Andrea100,
I am happy to that you have been successfull!

Your success makes me curious about the general status of the hardware support in general and I hope you have some time to answer my questions.

- What version of Ubuntu 16.04 Alpha did you try eventually ? 64bit or 32bit?
- Did you already install it on the internal flash storage or are you still running from a USB stick.
- Is the touchscreen working properly?
- Is WIFI working?
- Is the keyboard and the touchpad of the keyboard section working?
- Is the SD card reader working?
- Does the laptop properly recovering from stand-by?

About your problem with the battery status indicator: Depending on the desktop environment you are running (I assume Canonicals Unity) the battery status indicator vanishes as soon as the battery is fully loaded. It reappears automatically when the device is running on battery and as long as the battery needs to recharge.

Markus

---

### Post by coffeecat on 2016-02-05
Support thread, not chat.

*Thread moved to **General Help**.*

---

### Post by stefanschroedlpos on 2016-03-28
As this seems to be the only support for this device running ubuntu, I want to share my expierience too, sorry for threadwarming though.

I recently installed ubuntu daily 64 bit from an usb drive after disabling secure boot in bios, running from internal storage now, as I'm typing this.
Altough I'm more a Mint-Guy, this doesn't work yet, because the device is only suitable for kernel 4 or higher.
Just a few things to note:
- Wifi works out of the box, touchscreen as well.
- Bluetooth has not been tested yed, neither SD-Card-Support or external screen support via hdmi

Minor and major (you decide;)) problems I have expierenced yet:
- Touchpad works, but no multi-touch
- No Audio (neither internal speakers nor headset) because there is no driver for the sound card device. After a bit of google, I found out that it should be a realtek RT 5640, but no workaround here yet
- No battery status is displayed (no matter if it's runnign on battery or AC-Power)
- When the laptop is closed, the screen stays on (Interestingly enough, in live mode, without having ubuntu installed, this worked)
- The device buttons next to the screen (louder etc..) don't work
- No hibernation/standby working yet

So you see, the list is long, but still I prefer ubuntu over Windows 10. The most important issue for me is the audio thing, that's #1 on my wishing list. 
Maybe all you using Ubuntu on this device could share their experience so we can move on thogether.
Greetings Stefan

---

### Post by lapartida on 2016-04-06
Thanks for the detailed information. I'm really anxious to have a try.
Did you mean that kernel 4 won't have the freeze or older kernels won't boot?
I just tried Manjaro yesterday, which was said to be 4.4 kernel, it worked at the beginning.
While I always wanted to keep windows 10, I tried to install it on the 500g hdd (it could boot if I write a live cd to it), and there  was an error said could not write something (I couldn't remember). Then I start again, and it froze when I choose the location (select the hdd).
This made me wonder if the problem was the driver for the 500g hdd, because many devices have z8300, like Rikomagic MK36SLE, claimed to work on special version of linux.

I also wonder if you could give any suggestions how to install ubuntu along with windows (I'm not sure if it's possible to share the 32g build in emmc)

---

### Post by kvalvik01 on 2017-01-21
Hi,

I got a HP x2 210 in December, processor Atom8300 with 4G RAM. I didn't have any problem installing Ubuntu 16.10 as a dual boot with Win 10. It runs like a charm, there are only a few problems (actually, pretty much the same stefanschroedlpos describes)

- no sound; the Realtek sound card is not included in the Linux kernel yet (I am using 4.9.x upgrading regularly), I gather this will be fixed when Linux 5.0 is released in Feb or so

- no power indicator; even in terminal with upower -d, it wouldn't recognize the battery.  

- no SD-card support

- when I close the lid, the screen goes off... but if I keep it closed for an extended time, it seems to be dead and requires several attempts to restart

Still, I highly recommend that little machine

---

