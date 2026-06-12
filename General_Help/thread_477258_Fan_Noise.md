---
title: "Fan Noise"
date: 2007-06-18
forum: General Help
---

### Post by lyosha on 2007-06-18
hi .. i am pretty new to linux and i am using dual boot : XP/UBUNTU  .  My FAN makes a lot of noise during LINUX session...XP can not hear it at all :) I  have seen a lot of posts there with the same problems but on leptop, i am talking about PC .

uname -a

 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

lspci

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
04:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)

+ Zalman 7700 PCU FAN

can you please help me ? i appreciate your future answers ..thanx :)**[B][B][B][B][B][COLOR="DarkRed"][/COLOR]**[/B][/B][/B][/B][/B]

---

### Post by Crafty Kisses on 2007-06-18
> **lyosha said:**
> hi .. i am pretty new to linux and i am using dual boot : XP/UBUNTU  .  My FAN makes a lot of noise during LINUX session...XP can not hear it at all :) I  have seen a lot of posts there with the same problems but on leptop, i am talking about PC .

uname -a

 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

lspci

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
04:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)

+ Zalman 7700 PCU FAN

can you please help me ? i appreciate your future answers ..thanx :)**[B][B][B][B][B]**[/B][/B][/B][/B][/B]
To my knowledge the fan has nothing to do with the OS, you might want to buy a can of compressed air and blow the dust out.

---

### Post by Major_Kong on 2007-06-18
Is the fan temperature controlled ?

---

### Post by lyosha on 2007-06-18
> **Codename said:**
> To my knowledge the fan has nothing to do with the OS, you might want to buy a can of compressed air and blow the dust out.

am gonna try :)

> **Major_Kong said:**
> Is the fan temperature controlled ?

what do u mean ? controlled by me? no :)

---

### Post by Major_Kong on 2007-06-18
Some fans run faster or slower according to the temperature.

What's your processor ? Does it have Power Saving/Frequency Scaling Features ?

Read this -> [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)

---

### Post by lyosha on 2007-06-18
i have P4 3.2 with HT ...is it safe to run all these commands or just leave it ?  :)

---

### Post by Major_Kong on 2007-06-18
Only the commands specific to your processor.

If you're unsure, run this command: cat /proc/cpuinfo 

and post the output.


PS: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_control_fan_speed_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_control_fan_speed_.28lm-sensors.29) - Check this out too.

---

