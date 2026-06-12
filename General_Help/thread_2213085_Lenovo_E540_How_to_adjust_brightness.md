---
title: "Lenovo E540: How to adjust brightness?"
date: 2014-03-24
forum: General Help
---

### Post by Hugo_Gerdmar on 2014-03-24
Hi.

I've got the same problem with my Lenovo E540. Tried to create the 20-intel.conf file in /usr/share/X11/xorg.conf.d but that did'nt work. Even tried the solution with editing grub to all the possibillities i've read about on different places online. 
From the beggining i couldn't use the hotkeys for adjusting the brightness but now the keys respond (f5 for down and f6 for up without FnLk) but i can only make one up/down but the brightness dosen't change. 

When googeling around I found out that my system only got i shortcut in /sys/share/backlight and that one is called Thinkpad_screen. Does that mean that I dont got any drivers installed for my graphic card? 

I've allso tried to use Xbacklight without succes. 

My Ubuntuversion is Ubuntu studio 13.10. 

I don't want to steal the thread but I run the script u listed Toz and this is the results:

```
BOOT_IMAGE=/boot/vmlinuz-3.2.0-60-lowlatency root=UUID=80e1966c-a998-43b6-bd59-f85612bc6a42 ro acpi_osi=Linux quiet splash acpi_backlight=vendor
```

```
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
    Subsystem: Lenovo Device 502a
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
```

```
/sys/class/backlight/thinkpad_screen
5
4
7

```

If you could help I'd be so glad. Tried different solutions since two days back but nothing works.

---

### Post by Toz on 2014-03-24
Hello and welcome to the forums. I've moved your post to its own thread.


>  Tried to create the 20-intel.conf file in /usr/share/X11/xorg.conf.d but that did'nt work.
It won't work for a couple of reasons: 1) its not supported by the kernel you are using, and 2) you don't currently have an intel_backlight interface (redundant due to #1).

Can you post back the results of this command so I can see what video driver you are using?
```
lspci -k | grep -iA2 VGA
```


Why are you using a non-standard kernel (low-latency)?


Can you change the grub parameters so that you are _not_ using "acpi_backlight=vendor", reboot and post back the results of these commands again?
```
cat /proc/cmdline
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

---

### Post by Hugo_Gerdmar on 2014-03-25
Hi!

Thank you for the help. Good with my own thread.  Then I know about the xorg.conf.d. The reason why I have a low-latency kernel is because i wan't to work with music in Ubuntu Studio. I want to record music with my computer and if theres a latency it becomes impossible. I don't know if Ubuntu Studio is the best way but it seemd like a good idea to try. 

Is it harder to begin with a non-standard kernel first time with Linux?

I tried the commands and this is the result

lspci -k | grep -iA2 VGA
```
 00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
    Subsystem: Lenovo Device 502a
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
```


cat /proc/cmdline
```
BOOT_IMAGE=/boot/vmlinuz-3.2.0-60-lowlatency root=UUID=80e1966c-a998-43b6-bd59-f85612bc6a42 ro quiet splash
```

for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/*
```
cat: /sys/class/backlight/*/brightness: Filen eller katalogen finns inte (Doesn't exist in swedish)
cat: /sys/class/backlight/*/actual_brightness: Filen eller katalogen finns inte
cat: /sys/class/backlight/*/max_brightness: Filen eller katalogen finns inte
```

The new results. Can you understand whats happening?

---

### Post by Toz on 2014-03-25
Interesting. Doesn't look like you're using the intel driver. Can we confirm?
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

If you're not using the intel driver, there is a good chance you are using the basic VESA driver. This will be the reason for no backlight interfaces.

---

### Post by Hugo_Gerdmar on 2014-03-26
Hm, strange. 

```
Programmet "pastebinit" är för närvarande inte installerat.  Du kan installera det genom att ange:
sudo apt-get install pastebinit 


```

pastebinit wasn't installed. I installed it and ran the script again
[URL="http://paste.ubuntu.com/7157817/"]
http://paste.ubuntu.com/7157817/[/URL]

---

### Post by Toz on 2014-03-26
> **Hugo_Gerdmar said:**
> Hm, strange. 

```
Programmet "pastebinit" är för närvarande inte installerat.  Du kan installera det genom att ange:
sudo apt-get install pastebinit 


```

pastebinit wasn't installed. I installed it and ran the script again
[URL="http://paste.ubuntu.com/7157817/"]
http://paste.ubuntu.com/7157817/[/URL]

Yes, you are using the VESA driver, not the intel driver. My first suggestion would be to try the stock kernel to see if you get the intel driver to load with backlight control. If it works, you're issue would be with the lowlatency kernel.

Is this one of those laptops with two video cards (intel and nvidia)?

---

### Post by Hugo_Gerdmar on 2014-03-26
This is one of those laptops with two video card. Read something about bumblebee but don't really get what it's about. Tried to install it and use it but without success. Didn't try for a very long time since I get this answers by you.   If i'd like to try stock kernel, do I have to reinstall a new OS? A "normal" Ubuntudist?

---

### Post by Toz on 2014-03-26
If this laptop has discreet graphics, you have a couple of options:

1. If you don't want to configure bumblebee, look to see if you can disable the nvidia card fully in the bios. System should then be able to pick up only the intel card.
2. Get bumblee working.

You may run into an issue with the lowlatency kernel, mostly because it is an old kernel and bumblebee will probably work better with a newer kernel.

Unfortunately, I have no experience with bumblebee so I won't be able to offer any assistance. Your best bet would be to create a new thread asking for assistance with it and hopefully someone else will pick it up and help.

> I have to reinstall a new OS? A "normal" Ubuntudist?
You shouldn't have to do a full reinstall - you should be able to configure it using the system as it is (however, the kernel may need to be changed).

---

