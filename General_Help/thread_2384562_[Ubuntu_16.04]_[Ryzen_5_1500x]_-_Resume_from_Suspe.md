---
title: "[Ubuntu 16.04] [Ryzen 5 1500x] - Resume from Suspend Resets BIOS"
date: 2018-02-08
forum: General Help
---

### Post by chosenbeans on 2018-02-08
Hello, been using Ubuntu since 6.10 and have spent the last 11 years learning *Linux in general. Last October I build a Ryzen system and have had issues with every distribution since then (even those without SystemD). From random reboots on Void Linux ([thread here]("https://forum.voidlinux.eu/t/computer-arbitrarily-reboots/4274")) to strange slow reboots in Linux Mint (solved by disabling "Cool & Quiet"). Now I have another issue which seems to span all up-to-date Ubuntu 16.04 systems.   

[SIZE=6]User Perspective [/SIZE] 

From the graphical shutdown options (insert desktop environment here) and choosing the "suspend" or "sleep" option, the system suspends without a problem. It's only upon resuming that the problem occurs. ...

Pressing spacebar to resume the system, the screen turns on and shows the brand logo. Then the screen turns black and the machine reboots. After the machine reboots, it then it shuts off for 3 seconds before turning on again. This time the BIOS screen appears before rebooting a 3rd time. After this I can get into the BIOS to find all my settings are reset. 

[SIZE=6]Machine Components:[/SIZE]

[LIST]
[*] Motherboard: [ASRock AB350 Pro4]("https://www.asrock.com/MB/AMD/AB350%20Pro4/index.asp#Specification")
[*] CPU: [Ryzen 5 1500x]("https://en.wikichip.org/wiki/amd/ryzen_5/1500x")
[*] Memory:  [Crucial 8GB CT8G4DFD824A]("https://www.newegg.com/Product/Product.aspx?Item=N82E16820156131")
[*] Storage: [Crucial BX300 240GB SSD]("http://www.crucial.com/usa/en/ct240bx300ssd1")
[*] PSU: [CORSAIR CX750M]("https://www.newegg.com/Product/Product.aspx?Item=N82E16817139216")
[*] GPU: [Sapphire Radeon NITRO+ RX 580 4GB]("http://sapphirenitro.sapphiretech.com/en/580-4.html#specifications")
[/LIST]


[SIZE=6]OS Specs:[/SIZE]

   ```
 
    System:    Host: konqi Kernel: 4.13.0-32-generic x86_64 (64 bit) Desktop: N/A Distro: neon 16.04 xenial
    Machine:   Mobo: ASRock model: AB350 Pro4 serial: M80-A8029800073
           Bios: American Megatrends v: P4.40 date: 01/05/2018
    CPU:       Quad core AMD Ryzen 5 1500X (-HT-MCP-) cache: 2048 KB 
           clock speeds: max: 3493 MHz 1: 3493 MHz 2: 3493 MHz 3: 3493 MHz 4: 3493 MHz 5: 3493 MHz 6: 3493 MHz
           7: 3493 MHz 8: 3493 MHz
    Graphics:  Card: Advanced Micro Devices [AMD/ATI] Device 67df
           Display Server: X.org 1.19.5 drivers: ati (unloaded: fbdev,vesa,radeon)
           tty size: 262x68 Advanced Data: N/A for root
    Audio:     Card-1 Advanced Micro Devices [AMD] Device 1457 driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] Device aaf0 driver: snd_hda_intel
           Card-3 Texas Instruments PCM2900 Audio Codec driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.13.0-32-generic
    Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
           IF: enp10s0 state: up speed: 1000 Mbps duplex: full mac: 70:85:c2:58:e7:7d
    Drives:    HDD Total Size: 3490.7GB (0.8% used) ID-1: /dev/sda model: Samsung_SSD_850 size: 250.1GB
           ID-2: USB /dev/sdb model: Expansion+_Desk size: 3000.6GB
           ID-3: /dev/sdc model: CT240BX300SSD1 size: 240.1GB
    Partition: ID-1: / size: 198G used: 28G (15%) fs: ext4 dev: /dev/sdc1
    RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
    Sensors:   System Temperatures: cpu: No active sensors found. Have you configured your sensors yet? mobo: N/A gpu: 27.0
    Info:      Processes: 225 Uptime: 59 min Memory: 1831.7/7973.1MB Client: Shell (sudo) inxi: 2.2.35 
```

[SIZE=6]Logs: 
[/SIZE]
[/var/log/pm-suspend.log]("https://gist.github.com/silvernode/c24256b3b7ae58b11a3a437d6052f65c")

If anybody can help, I would be very pleased since this is a big problem for the way I work. Thank you.

---

### Post by QIII on 2018-02-08
Hello!

While you wait for an OS-related answer, you might explore a hardware solution on the ASRock forums.  I'm having intermittent problems shutting down my 1950x on an ASRock X399 Taichi.  I suspect an OS/hardware miscommunication that may be related to the ongoing UEFI/BIOS issues with the Ryzen boards.

---

### Post by mörgæs on 2018-02-08
Have you tried 18.04 in a live boot to see if there is any difference?

---

### Post by chosenbeans on 2018-02-08
> **QIII said:**
> Hello!

While you wait for an OS-related answer, you might explore a hardware solution on the ASRock forums.  I'm having intermittent problems shutting down my 1950x on an ASRock X399 Taichi.  I suspect an OS/hardware miscommunication that may be related to the ongoing UEFI/BIOS issues with the Ryzen boards.


I'll check that out thanks.



> Have you tried 18.04 in a live boot to see if there is any difference? 


I haven't tried 18.04 yet but I think that's a good idea.

---

### Post by chosenbeans on 2018-02-11
ACPI was disabled so I ran ```
sudo systemctl enable acpid
``` and rebooted. Now suspend functions as expected. We will see if it lasts but for now I will mark this as solved.

---

