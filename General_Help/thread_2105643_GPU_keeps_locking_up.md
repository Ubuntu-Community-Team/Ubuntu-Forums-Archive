---
title: "GPU keeps locking up"
date: 2013-01-16
forum: General Help
---

### Post by Trazzt on 2013-01-16
Hello,

My Ubuntu 12.04 64 bit keeps freezing randomly. I think it's because of GPU lockups, because all the symptoms stated in [this wiki]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze") match my problems. 


[LIST]
[*] The freezing occurs repeatedly, about once every 30 minutes.
[*]I first noticed it when I started to open multiple applications, like browsing with firefox and typing text to launch programs through the Unity launcher
[*]The errors seems to occurs under medium to heavy system load, running multiple applications at a time. Sometimes I experience this when I'm just browing the web with firefox
[/LIST]
Specs:
Acer L100 mini pc

Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
Graphics card: On-board NVIDIA 6150 LE
RAM: Corsair 2x1gb 

Other info: The lockups occur with Nvidia drivers and with nouveau drivers (don't know if drivers are relevant in this issue). With other distro's, like Arch Linux, I never had lockups.


Any help would be appreciated

Greetings, 

Trazzt

Dmesg.txt: [http://pastebin.com/xu2atYTE](http://pastebin.com/xu2atYTE)
X.org log full: [http://pastebin.com/1J7vDWWC](http://pastebin.com/1J7vDWWC)

---

### Post by Trazzt on 2013-01-18
bump

---

### Post by bogan on 2013-01-18
Hi!, **Trazzt**,

The most likely cause of problems after a similar time are either overheating or memory faults.

Check all fans and and mesh screens are are clean, and fans running. Blow out whole case with clean dry air - aerosole - and ensure CPU cooler is correctly bedded.

Remove one memory card at a time and check if lockups still occur. Run Post and Memtest.

Try booting from a LiveCD/USB and see if the same happens with the same and also  earlier versions of ubuntu.

Chao!, **bogan.**

---

### Post by Trazzt on 2013-01-18
Thanks bogan for the reply. I ran a memtest with the 2 ram modules in slot, it came out clean.
I've had this problem ever since i've used ubuntu. My first experience with ubuntu was with ubuntu 9.10. It had the same issues as the ones I'm having now. I'll try your suggestions and report back later.

---

### Post by Trazzt on 2013-01-18
I've found the solution in **[COLOR=Red][this thread]("http://ubuntuforums.org/showthread.php?p=12461927")[/COLOR]** I needed to edit this line in the GRUB2 bootloader ```
$vt_handoff
``` to ```
$vt_handoff irqpoll noapic acpi=off
``` Look at my post on how to make the grub alteration permanent.

---

