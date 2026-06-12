---
title: "GRUB boots into rescue mode, unknown filesystem"
date: 2017-10-26
forum: General Help
---

### Post by getsetgo on 2017-10-26
Hello! Long story short, GRUB keeps booting into rescue mode and saying "unknown filesystem." This began happening after I tried to switch from the KDE edition of Manjaro to the xfce edition. So I tried installing Debian and Xubuntu instead, but with the same result for both. I've been doing manual partitioning during installations since I have a separate /home folder. I currently have a separate boot partition as well, as I believe someone suggested it when I came to the IRC for help a month or so ago. 

Tried [https://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue](https://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue) but once I get to "insmod normal" I get "error: no such partition." Tried [https://wiki.manjaro.org/index.php/Restore_the_GRUB_Bootloader](https://wiki.manjaro.org/index.php/Restore_the_GRUB_Bootloader) but it doesn't recognize the EFI partition as being EFI.  

Here's my inxi info (ran the command from Manjaro live media):

    System:    Host: manjaro Kernel: 4.9.50-1-MANJARO x86_64 bits: 64 gcc: 7.2.0
               Desktop: N/A Distro: Manjaro Linux
    Machine:   Device: portable System: Dell product: Inspiron 7547 serial: N/A
               Mobo: Dell model: 0AM670 v: A00 serial: N/A
               UEFI: Dell v: A03 date: 10/27/2014
    Battery    BAT0: charge: 7.3 Wh 100.0% condition: 7.3/44.5 Wh (16%)
               model: SIMPLO Dell status: Full
    CPU:       Dual core Intel Core i7-4510U (-HT-MCP-) 
               arch: Haswell rev.1 cache: 4096 KB
               flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 10379
               clock speeds: max: 3100 MHz 1: 2302 MHz 2: 1999 MHz 3: 1999 MHz
               4: 2076 MHz
    Graphics:  Card: Intel Haswell-ULT Integrated Graphics Controller
               bus-ID: 00:02.0
               Display Server: N/A drivers: intel (unloaded: modesetting)
               tty size: 80x24
    Audio:     Card-1 Intel 8 Series HD Audio Controller
               driver: snd_hda_intel bus-ID: 00:1b.0
               Card-2 Intel Haswell-ULT HD Audio Controller
               driver: snd_hda_intel bus-ID: 00:03.0
               Sound: Advanced Linux Sound Architecture v: k4.9.50-1-MANJARO
    Network:   Card: Intel Wireless 3160 driver: iwlwifi bus-ID: 07:00.0
               IF: wlp7s0 state: up mac: d0:7e:35:4b:ed:53
    Drives:    HDD Total Size: 1008.3GB (53.6% used)
               ID-1: /dev/sda model: TOSHIBA_MQ02ABF1 size: 1000.2GB
               ID-2: USB /dev/sdb model: innostor size: 8.1GB
    Partition: ID-1: / size: 5.8G used: 100M (2%) fs: overlay dev: N/A
    Sensors:   System Temperatures: cpu: 53.0C mobo: 27.8C
               Fan Speeds (in rpm): cpu: N/A
    Info:      Processes: 203 Uptime: 39 min Memory: 2186.0/7893.2MB
               Init: systemd Gcc sys: 7.2.0
               Client: Shell (bash 4.4.121) inxi: 2.3.38

---

### Post by oldfred on 2017-10-27
So what Linux are you wanting to use. We have sub-forums for other Linux.

Usually best to not have a separate /boot partition. Some distributions use LVM which does have a separate /boot partition. But you cannot share a /boot partition as that leads to conflicts.
If you are installing in UEFI mode then you can share the ESP - efi system partition.

Many discussions on sharing /home. You may end up with settings in one install changing another installs. But if totally different configuration/desktops then it may work. I normally suggest having a /mnt/data partition so you have data that can be easily shared, but then settings are still in /home for each install. When all data is in a data partition /home is so small it can just be in /.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

