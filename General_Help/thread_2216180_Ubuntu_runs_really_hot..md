---
title: "Ubuntu runs really hot."
date: 2014-04-10
forum: General Help
---

### Post by st18009 on 2014-04-10
Hello. I have a tried many distros of linux and they all seem to have the same issue. My laptop runs hot on all of them ( ubuntu, linux, mint, zorin . . . etc ).
 

 I have a Toshiba satellite L305 – S5919   2.2 Ghz processor ( celeron ) and 2 GB of ram.

 Im currently using ubuntu 12.0.4

 

 I installed powertop on it and got some results.
 I mean it runs so hot that it will keep my house warm mid winter.

 I have a dual boot and have windows 8.1 set as primary OS ( it runs cool ) .



Over view

Summary: 1035.2 wakeups/second,  0.0 GPU ops/seconds, 0.0 VFS ops/sec and 10.5%

                Usage       Events/s    Category       Description
              2.0 ms/s     941.5        Timer          menu_hrtimer_notify
            100.0%                      Device         Audio codec hwC0D1: LSI
            100.0%                      Device         Audio codec hwC0D0: Realt
             60.1 ms/s      11.8        Process        /usr/lib/firefox/firefox
             11.4 ms/s       7.9        Process        compiz
            384.1 µs/s      21.7        Timer          hrtimer_wakeup
            295.8 µs/s      15.8        kWork          ieee80211_iface_work
            642.7 µs/s      12.8        Interrupt      [45] i915
              2.7 ms/s      10.9        Interrupt      [6] tasklet(softirq)
             12.1 ms/s       4.9        Process        /usr/bin/X :0 -auth /var/
              4.3 ms/s       3.0        Process        gnome-terminal
              5.9 ms/s      0.00        Process        powertop
            174.0 µs/s       1.0        Process        syndaemon -i 2.0 -K -R -t
            470.6 µs/s       1.0        Timer          tick_sched_timer
              2.8 ms/s      0.00        Interrupt      [17] ath
             37.2 µs/s       1.0        Process        [rcu_sched]
              6.1 µs/s       1.0        kWork          flush_to_ldisc



Idle Stats

          Package   |            CPU 0
POLL        0.0%    | POLL        0.0%    0.0 ms
C1         75.0%    | C1         75.0%    0.2 ms
C2          3.9%    | C2          3.9%    0.0 ms


Frequency Stats


            Package |            CPU 0
Idle       100.0%   | Idle       100.0%



Device Stats


    Usage     Device name
            100.0%        Audio codec hwC0D1: LSI
            100.0%        Audio codec hwC0D0: Realtek
              3.4%        CPU use
            100.0%        Display backlight
              0.0 ops/s   GPU
            100.0%        PCI Device: Realtek Semiconductor Co., Ltd. RTL8101E/R
            100.0%        PCI Device: Intel Corporation 82801IBM/IEM (ICH9M/ICH9
            100.0%        PCI Device: Intel Corporation 82801I (ICH9 Family) SMB
            100.0%        PCI Device: Intel Corporation 82801I (ICH9 Family) USB
            100.0%        Radio device: ath5k
            100.0%        PCI Device: Intel Corporation Mobile 4 Series Chipset
            100.0%        PCI Device: Intel Corporation Mobile 4 Series Chipset
            100.0%        PCI Device: Intel Corporation Mobile 4 Series Chipset
            100.0%        PCI Device: Intel Corporation 82801I (ICH9 Family) USB
            100.0%        PCI Device: Intel Corporation 82801I (ICH9 Family) USB
            100.0%        PCI Device: Intel Corporation ICH9M LPC Interface Cont
            100.0%        PCI Device: Atheros Communications Inc. AR242x / AR542
            100.0%        PCI Device: Intel Corporation 82801I (ICH9 Family) USB

<ESC> Exit |                                                                    



Tunables

                      
   Bad           Enable SATA link power management for /dev/sda
   Bad           NMI watchdog should be turned off
   Bad           VM writeback timeout
   Bad           Enable Audio codec power management
   Bad           Runtime PM for PCI Device Atheros Communications Inc. AR242x /
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family
   Bad           Runtime PM for PCI Device Intel Corporation Mobile 4 Series Chi
   Bad           Runtime PM for PCI Device Intel Corporation Mobile 4 Series Chi
   Bad           Runtime PM for PCI Device Intel Corporation Mobile 4 Series Chi
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family
   Bad           Runtime PM for PCI Device Realtek Semiconductor Co., Ltd. RTL81
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family
   Bad           Runtime PM for PCI Device Intel Corporation 82801IBM/IEM (ICH9M
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family

Thanks in advance.

---

### Post by trag on 2014-04-11
Use advanced power manager TLP to cool things down
sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tlp-rdw

---

