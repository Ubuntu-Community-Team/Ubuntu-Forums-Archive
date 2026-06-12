---
title: "High wakeups/sec + high power consumption"
date: 2020-04-02
forum: General Help
---

### Post by senuketo on 2020-04-02
Hi,
I've been trying for a long time to find out the **low battery time** of my laptop: **X1 carbon 7 gen**.
Advertised up to 9 hours when I get about 3 or less. 
[COLOR=#000000][FONT=LatoMedium]Linux support is not that good for this model so this might be one of the problems.[/FONT][/COLOR]

> [COLOR=#000000][FONT=LatoMedium]*&#9679; Processor: 10th Gen Intel® Core&#8482; i7-10710U (1.10GHz, up to 4.70GHz with Turbo Boost, 6 Cores, 12MB Cache)*[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]*&#9679; Operating System: Windows 10 Pro 64*[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]*&#9679; Display Type: 14.0" FHD (1920 x 1080) IPS, anti-glare with Privacy Guard, 400 nits*[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]*&#9679; Memory: 16GB LPDDR3 2133MHz (Soldered)*[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]*&#9679; Hard Drive: 1TB SSD PCIe*[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]*&#9679; Warranty: 1 Year Depot or Carry-in*[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]*&#9679; Graphics: Integrated Intel® UHD Graphics*[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]*&#9679; Camera: IR & 720p HD*[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]*&#9679; Fingerprint Reader: Fingerprint Reader*[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]*&#9679; Keyboard: Backlit - US English*[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium][I]&#9679; Wireless: Intel® 9560 802.11AC (2 x 2) & Bluetooth® 5.0
[/I][/FONT][/COLOR]


> **Linux** <user> 5.3.0-40-generic #32~18.04.1-Ubuntu SMP Mon Feb 3 14:05:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


[COLOR=#000000][FONT=LatoMedium]This is what I did till now:[/FONT][/COLOR]

[COLOR=#000000][FONT=LatoMedium]**Firmware**[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]fwupdmrg enable-remote lvfs-testing[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]fwupdmrg get-devices[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]fwupdmrg refresh[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]fwupdmrg get-updates[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]fwupdmrg update[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]fwupdmrg disable-remote lvfs-testing[/FONT][/COLOR]

[COLOR=#000000][FONT=LatoMedium]**TLP**[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]Install tlp: [https://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html](https://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html)[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]CPU_SCALING_GOVERNOR_ON_BAT = powersave[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]CPU_ENERGY_PERF_POLICY_ON_BAT = balance_power
[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]others are default
[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]sudo apt install acpi-call-dkms[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]sudo apt install tp-smapi-dkms #but that's not supported[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]sudo tlp recalibrate -calibrates the battery(discharge/charge cycle)[/FONT][/COLOR]

[COLOR=#000000][FONT=LatoMedium]**Undervolt & Throttling**[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]Install [https://github.com/erpalma/throttled](https://github.com/erpalma/throttled)[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]Because of throttling CPU at 85C (now it's at 95C)[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]Undervolt offsets: CORE: -100.00 mV | GPU: -150.00 mV | CACHE: -100.00 mV | UNCORE: -100.00 mV | ANALOGIO: 0.00 mV[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium][BATTERY] Thermal: OK - Power: OK - Current: OK - Cross-domain (e.g. GPU): OK || VCore: 607 mV - Package: 1.9 W - Graphics: 0.6 W - DRAM: 0.3 W [/FONT][/COLOR]

[COLOR=#000000][FONT=LatoMedium]Get battery **watt consumption** command:[/FONT][/COLOR]
[COLOR=#000000][FONT=LatoMedium]system_profiler SPPowerDataType | grep "(m[AV])" | awk '{ print $3 }' | tr ' ' ' ' | awk '{ print $1*$2/1000000 }'

[B]Powertop
[/B]Installed and calibrated - not sure if it's that accurate
[/FONT][/COLOR]
Following data is without any apps loaded, just powertop.


> The battery reports a discharge rate of 7.59 W
Summary: 1067,1 wakeups/second, 0,0 GPU ops/seconds, 0,0 VFS ops/sec and 17,9% CPU use


Power est. Usage Events/s Category Description
3.39 W 0,8 pkts/s Device Network interface: wifi0 (iwlwifi)
2.00 W 0,0 pkts/s Device Network interface: eth0 (e1000e)
450 mW 5,0% Device Display backlight
288 mW 64,4 ms/s 160,9 Process [PID 2145] /usr/bin/gnome-shell
274 mW 1,1 ms/s 200,2 Interrupt [17] idma64.1
241 mW 2,4 ms/s 175,4 Timer tick_sched_timer


- **ethernet** device is consuming **2 watts** when it's **not** even **plugged** in.
- very **high wakeups/s**econd.
- after I **disable** both **network devices** (using commands bellow) power **consumption doesn't fall** that much 
--- Am I turning it physically off? 
--- If not is there a way?


#disable ethernet & wifi devices
> sudo ifconfig wifi0 down
sudo ifconfig eth0 down


> The battery reports a discharge rate of 6.04 W
Summary: 713,6 wakeups/second, 0,0 GPU ops/seconds, 0,0 VFS ops/sec and 7,2% CPU use


Power est. Usage Events/s Category Description
601 mW 5,0% Device Display backlight
303 mW 2,3 ms/s 214,6 Interrupt [17] idma64.1
244 mW 4,2 ms/s 171,4 Process [PID 623] [irq/164-SYNA800]
156 mW 30,2 ms/s 77,6 Process [PID 2145] /usr/bin/gnome-shell
131 mW 1,5 ms/s 92,5 Timer tick_sched_timer


Still quite high wakeups/second. 
So I've run eventstat as instructed here: [https://wiki.ubuntu.com/Kernel/PowerManagement/IdentifyingIssues](https://wiki.ubuntu.com/Kernel/PowerManagement/IdentifyingIssues)


**Eventstat**
#show top 20 wakeup processes grouped in 10 seconds - twice
> sudo eventstat -n 20 10 2


>  Event/s PID Task Init Function 
30.01 2145 gnome-shell hrtimer_wakeup 
23.79 6266 pool hrtimer_wakeup 
12.65 2011 Xorg it_real_fn 
10.94 3084 [kworker/u12:9] hrtimer_wakeup 
8.23 2145 gnome-shell tick_sched_timer 
5.52 3661 gnome-terminal- hrtimer_wakeup 
1.20 2011 Xorg hrtimer_wakeup 
1.00 1481 gsd-color hrtimer_wakeup 
1.00 2298 gsd-color hrtimer_wakeup 
0.80 2011 Xorg tick_sched_timer 
0.50 1046 gmain hrtimer_wakeup 
0.40 5738 powertop hrtimer_wakeup 
0.40 1258 gnome-shell tick_sched_timer 
0.30 1442 gmain hrtimer_wakeup 
0.30 2500 gmain hrtimer_wakeup 
0.30 1083 gmain hrtimer_wakeup 
0.30 3084 [kworker/u12:9] tick_sched_timer 
0.20 1396 rtkit-daemon hrtimer_wakeup 
0.20 2498 gmain hrtimer_wakeup 
0.20 1397 rtkit-daemon hrtimer_wakeup 
993 Total events, 99.67 events/sec (kernel: 11.24, userspace: 88.43)


Event/s PID Task Init Function 
59.11 2011 Xorg it_real_fn 
45.73 2145 gnome-shell hrtimer_wakeup 
38.34 2011 Xorg hrtimer_wakeup 
23.66 3661 gnome-terminal- hrtimer_wakeup 
20.67 6266 pool hrtimer_wakeup 
11.08 5738 powertop tick_sched_timer 
8.49 2145 gnome-shell tick_sched_timer 
6.79 6414 [kworker/u12:3] hrtimer_wakeup 
3.10 2011 Xorg tick_sched_timer 
2.30 3661 gnome-terminal- tick_sched_timer 
1.60 623 [irq/164-SYNA8] tick_sched_timer 
0.90 1481 gsd-color hrtimer_wakeup 
0.90 2018 InputThread tick_sched_timer 
0.90 2298 gsd-color hrtimer_wakeup 
0.60 2018 InputThread timerfd_tmrproc 
0.50 2416 libinput-debug- tick_sched_timer 
0.30 2187 gdbus tick_sched_timer 
0.30 1 systemd tick_sched_timer 
0.20 5188 [kworker/4:1] tick_sched_timer 
0.20 2185 ibus-daemon tick_sched_timer 
2276 Total events, 227.24 events/sec (kernel: 8.79, userspace: 218.45)


I've witnessed something strange. The first time I disabled the ethernet device it disappeared from powertop but the wifi device jumped with the same amount. Then I disabled the wifi, and then all it's power consumption went into the display. As if some unknown process device was just changing houses. Cannot reproduce it now but when killing processes/devices, consumption doesn't fall the same amount.

Idle with screen at 0%, wifi ON for this laptop should be around 2 watts as mentioned here:
[https://www.ultrabookreview.com/31104-lenovo-thinkpad-x1-carbon-7th-gen-review/](https://www.ultrabookreview.com/31104-lenovo-thinkpad-x1-carbon-7th-gen-review/). Different processor, but should be the same ball park.
Also cannot turn off the display backlight completely. Lowest setting is like 20%.

What would be a proper way to continue debugging what's going on?

---

### Post by daniewicz on 2020-04-02
Is powertop running as a service on startup? Have you set all of the "tunables" in powertop to "good"

---

### Post by senuketo on 2020-04-03
Hey,
 no, powertop is not set to be ran on startup. Tunables on batt are all good except for "VM writeback timeout".
[COLOR=#242729][FONT=Consolas]cat /proc/sys/vm/dirty_writeback_centisecs
6000
[/FONT][/COLOR]meaning 60 seconds. Powertop suggests 1500 - 15 seconds. Did that and it's now 1500.

No differance. Wifi consumes 3.5W and ethernet 2.4W

in /etc/tlp.conf I've set WIFI power saving mode on for BaTT
WIFI_PWR_ON_BAT=on

---

### Post by senuketo on 2020-04-03
Now the display shows excessive consumption.

> The battery reports a discharge rate of 8.94 W
Summary: 454,8 wakeups/second,  0,0 GPU ops/seconds, 0,0 VFS ops/sec and 4,7% CPU


Power est.              Usage       Events/s    Category       Description
  4.09 W     40,0%                      Device         Display backlight
  3.31 W      0,1 pkts/s                Device         Network interface: wlp0s20f
  2.60 W      0,0 pkts/s                Device         Network interface: enp0s31f
 13.6 mW      0,8 ms/s     144,8        Interrupt      [17] idma64.1
 6.94 mW    645,8 µs/s      73,6        Timer          tick_sched_timer

Lowered brightness:

> The battery reports a discharge rate of 8.78 W
Summary: 1186,5 wakeups/second,  0,0 GPU ops/seconds, 0,0 VFS ops/sec and 29,1% CP


Power est.              Usage       Events/s    Category       Description
  3.37 W      0,0 pkts/s                Device         Network interface: enp0s31f
  2.10 W      2,4 pkts/s                Device         Network interface: wlp0s20f
  704 mW      5,0%                      Device         Display backlight
 33.8 mW      5,5 ms/s     250,8        Timer          tick_sched_timer




Not much differance.

---

### Post by senuketo on 2020-04-03
Cannot see the GPU in the Device Stats tab.
It must be using some power.

> The battery reports a discharge rate of 7.89 W


Power est.    Usage     Device name
  2.61 W     30,0%        Display backlight
  2.00 W      0,0 pkts/s  Network interface: enp0s31f6 (e1000e)
  1.69 W     10,9%        CPU core
  1.25 W      0,0 pkts/s  Network interface: wlp0s20f3 (iwlwifi)
  1.03 W     61,8%        Audio codec hwC0D0: Realtek
  291 mW     10,9%        DRAM
 71.7 mW    100,0%        Radio device: iwlwifi
 52.7 mW     10,9%        CPU misc
    0 mW      0,0%        USB device: xHCI Host Controller
    0 mW      0,0%        Radio device: thinkpad_acpi
    0 mW      0,0%        USB device: Integrated Camera (Chicony Electronics Co.,Ltd.)
    0 mW      0,0%        USB device: xHCI Host Controller
    0 mW      0,0%        USB device: xHCI Host Controller
    0 mW      0,0%        USB device: xHCI Host Controller
    0 mW      0,0%        USB device: usb-device-06cb-00bd
            100,0%        PCI Device: Intel Corporation Device 0d4f
            100,0%        PCI Device: Intel Corporation Device 9bca
            100,0%        PCI Device: Intel Corporation Device 02f0
            100,0%        PCI Device: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
            100,0%        PCI Device: Intel Corporation Device 02b0
            100,0%        PCI Device: Intel Corporation SSD Pro 7600p/760p/E 6100p Series
             61,9%        PCI Device: Intel Corporation Device 02c8
             46,8%        PCI Device: Intel Corporation Device 02e9
             43,1%        runtime-i2c_designware.1
             34,2%        PCI Device: Intel Corporation Device 02b4
             28,5%        PCI Device: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016]
             28,4%        PCI Device: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016]
             28,4%        PCI Device: Intel Corporation JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016]
             28,3%        PCI Device: Intel Corporation JHL6540 Thunderbolt 3 NHI (C step) [Alpine Ridge 4C 2016]
             28,3%        PCI Device: Intel Corporation JHL6540 Thunderbolt 3 USB Controller (C step) [Alpine Ridge 4C 2016]
             28,1%        PCI Device: Intel Corporation Device 02a4
             28,0%        PCI Device: Intel Corporation Device 02a3
             28,0%        PCI Device: Intel Corporation Device 0284




---

### Post by daniewicz on 2020-04-03
Do you have the latest BIOS?

---

### Post by senuketo on 2020-04-03
I was on 1.13 bios version.
Ran fwupdmgr and it updated to 1.16 

**sudo dmidecode -t bios**

> BIOS Information
    Vendor: LENOVO
    Version: N2QET22W (1.16 )
    BIOS Revision: 1.16
    Firmware Revision: 1.8



Aren't these be the last BIOS versions?
[https://pcsupport.lenovo.com/bg/en/products/laptops-and-netbooks/thinkpad-x-series-laptops/thinkpad-x1-carbon-7th-gen-type-20qd-20qe/downloads/ds540232](https://pcsupport.lenovo.com/bg/en/products/laptops-and-netbooks/thinkpad-x-series-laptops/thinkpad-x1-carbon-7th-gen-type-20qd-20qe/downloads/ds540232)
Shouldn't it update to 1.30? Also I can see they support Ubuntu 16, only. A bit confused. Am I on the wrong page?

Consumption is same. Difference is that the Ethernet device consumption got added to the WiFi device. I guess it's not possible the WiFi to consume 5 W.

> The battery reports a discharge rate of 8.44 W
Summary: 523,8 wakeups/second,  0,0 GPU ops/seconds, 0,0 VFS ops/sec and 4,9% CPU use


Power est.              Usage       Events/s    Category       Description
  4.80 W      0,0 pkts/s                Device         Network interface: wlp0s20f3 (iwlwifi)
  1.00 W     20,0%                      Device         Display backlight
  479 mW      1,0 ms/s     209,9        Interrupt      [17] idma64.1
  154 mW    635,4 µs/s      67,5        Timer          tick_sched_timer
  126 mW     29,8 ms/s      55,3        Process        [PID 2207] /usr/bin/gnome-shell
  123 mW      0,9 ms/s      54,1        Process        [PID 699] [irq/165-SYNA800]
 59.8 mW      0,0 pkts/s                Device         Network interface: enp0s31f6 (e1000e)
 54.0 mW    236,3 µs/s      23,7        Process        [PID 11] [rcu_sched]
 48.5 mW     94,3 µs/s      21,3        kWork          gen6_pm_rps_work


---

### Post by daniewicz on 2020-04-03
Just to give you something to compare to. My old MacBook Pro running Mageia XFCE. It is possible for Wifi to consume 5 W!

```
The battery reports a discharge rate of 12.5 W
The power consumed was 274 J
The estimated remaining time is 4 hours, 37 minutes

Summary: 116.7 wakeups/second,  0.0 GPU ops/seconds, 0.0 VFS ops/sec and 2.6% CPU use

Power est.              Usage       Events/s    Category       Description
  5.84 W      0.0 pkts/s                Device         Network interface: wlp3s0 (wl)
  929 mW      0.9 ms/s      47.0        Timer          tick_sched_timer
  338 mW    179.5 us/s      17.2        kWork          dbs_work_handler
  318 mW      1.0 ms/s      15.9        Interrupt      [6] tasklet(softirq)
  212 mW    182.9 us/s      10.7        Process        [PID 10] [rcu_sched]
 63.1 mW     60.4 us/s       3.2        Process        [PID 596] [usb-storage]
 62.0 mW      1.5 ms/s       2.7        Process        [PID 1938] /usr/lib64/xfce4/panel/wrapper-2.0
 59.0 mW     28.4 us/s       3.0        Timer          ehci_hrtimer_func
 37.5 mW     44.3 us/s       1.9        Interrupt      [22] ehci_hcd:usb2
 34.2 mW      4.5 ms/s      0.30        Process        [PID 1973] /usr/bin/perl /usr/bin/net_applet
 33.1 mW    124.6 us/s       1.6        Timer          hrtimer_wakeup
 30.2 mW    118.5 us/s       1.5        Process        [PID 1895] xfwm4 --display :0.0 --sm-client-i
 22.1 mW     84.4 us/s       1.1        kWork          gc_worker
 21.2 mW    102.4 us/s       1.0        kWork          os_execute_work_item
 18.7 mW     12.3 us/s       0.9        kWork          pci_pme_list_scan
 18.7 mW      7.9 us/s       0.9        kWork          sync_hw_clock
 18.6 mW      0.0 us/s       0.9        kWork          disk_events_workfn
 11.0 mW     38.1 us/s       0.5        Interrupt      [4] block(softirq)
 9.88 mW     11.9 us/s       0.5        Interrupt      [26] ahci[0000:00:0b.0]

```

---

### Post by senuketo on 2020-04-04
Thanks, daniewicz! Were you downloading a torrent, idling, browsing webpages?
I agree it's possible to consume 5 W but if it's in idle without even a browser loaded it shouldn't be that much, right?

How can I power it down completely? This doesn't seem to do the work: [COLOR=#000000][I]sudo ifconfig wifi0 down

[/I][/COLOR]

---

### Post by daniewicz on 2020-04-04
My laptop was idling when I collected the data above.

---

### Post by senuketo on 2020-04-04
Changed my repository from the local one(nearest one) to a general one. 
Ran update/upgrade and lots more upgradables appeared. 
/Was looking for a way to try 5.3.0-46-generic kernel/
Now I'm with kernel -46 which broke my WiFi, bluetooth and audio output is quite bad, maybe the subwoofer is broken.


Started powertop and it was getting to 3.5 W at idle, minimum screen brightness, no apps. - Interesting, getting there.


so I did the following to fix the WiFi:


> 
git clone [https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git](https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git)
cd backport-iwlwifi/
make defconfig-iwlwifi-public
sed -i 's/CPTCFG_IWLMVM_VENDOR_CMDS=y/# CPTCFG_IWLMVM_VENDOR_CMDS is not set/' .config
make -j4
sudo make install
sudo modprobe iwlwifi



After reboot WiFi is back. Having problems with the bluetooth though.
[B]Brighntess at minimum, no apps, WiFi On - 3.7 W
[/B]
> The battery reports a discharge rate of 3.70 W
Summary: 240,9 wakeups/second,  0,0 GPU ops/seconds, 0,0 VFS ops/sec and 3,6% CP


Power est.              Usage       Events/s    Category       Description
  3.09 W      0,0%                      Device         Display backlight
  1.11 W      0,0 pkts/s                Device         Network interface: enp0s3
  803 mW      0,1 pkts/s                Device         Network interface: wlp0s2
  130 mW    682,7 µs/s      63,7        Timer          tick_sched_timer
  102 mW     21,2 ms/s      42,1        Process        [PID 2164] /usr/bin/gnome
 50.2 mW    295,2 µs/s      24,6        Process        [PID 11] [rcu_sched]



Much happier with the results. Almost twice as little consumption at idle.


[B]Brightness about 30%, Chrome with 13 tabs, WiFi ON, text editor and Slack only 5.5 W:
[/B]

> 
The battery reports a discharge rate of 5.38 W
Summary: 1252,0 wakeups/second,  0,0 GPU ops/seconds, 0,0 VFS ops/sec and 25,4%


Power est.              Usage       Events/s    Category       Description
  3.30 W      5,0%                      Device         Display backlight
  909 mW      1,0 pkts/s                Device         Network interface: wlp0s2
  780 mW      0,0 pkts/s                Device         Network interface: enp0s3
  480 mW      4,0 ms/s     245,5        Timer          tick_sched_timer
  374 mW      0,8 ms/s     191,9        Interrupt      [17] idma64.1
  312 mW      1,4 ms/s     152,8        Process        [PID 3048] /opt/google/ch
  177 mW     49,9 ms/s      59,6        Process        [PID 2164] /usr/bin/gnome
  153 mW      2,6 ms/s      77,9        Process        [PID 704] [irq/164-SYNA80


[B]Much much better.
[/B]
Still pretty high number of wakeups/second. If you direct me on how to find who's the culprit, would be great. Tried a couple of things but they didn't help much as mentioned in the first post.

---

### Post by senuketo on 2020-04-04
Tried the previous kernel-30, again 8 W idle. 
So it's the kernel.

---

### Post by daniewicz on 2020-04-04
Sounds like progress to me!

---

### Post by senuketo on 2020-04-04
Yes, definitely!
Could it be the new kernel just broke some devices I'm not seeing :D

Also just saw that because of the daylight I couldn't see that the keyboard backlight was on.
Without it consumption fell to 2.7 W (soul ejaculation).

With average consumption under normal use 6 W with a 52Wh battery I can reach about 8.5h. Naish!

---

