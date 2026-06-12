---
title: "ubuntu 17.10 freezes. Logs show no clue."
date: 2018-01-22
forum: General Help
---

### Post by vincentLin on 2018-01-22
I have been using ubuntu for several years now. Desktop and server versions. I would say the experience was quite good. In all the aspects: user friendly interface, abundance of software choices, stability... Somehow in 2017 I got a different feelings about it. I am using a Lenovo ThinkCentre with 17.04 and later 17.10 desktop. Most complains are about not being stable, frequent freezes when you have to cold start the computer to bring it back to life. And the inability to efficiently troubleshoot. Googled that problem a lot and though many stated that Linux in general writes lots of info about itself in simple text files and I searched them,  I was not able to find any hints of what could possible lead my computer to a state that only a restart could help. Hardware configuration has not changed much, additional RAM and a new SSD. But those were more like attempts to fix the freezing problems. I added them after I started to troubleshoot. Same kind of hardware is used for 16.04 LTS server. And I have no problems with it. Tried to switch Unity and Gnome (two versions) desktops with no difference. Same results.

Anybody experienced similar problems? It is very frustrating. It only happens when the comp is left idle. It may be 30 min or longer but always it turns into a solid brick after being unused, never while being used. As I said, I found no leads in the log files. They just get stopped and start register new records after a cold reboot.

Any ideas are welcomed. 
Thanks.

---

### Post by #&amp;thj^% on 2018-01-22
Sorry to hear "you" are seeing such regressions.:(
I on the other hand have not had any problems, smooth sailing.
```
Machine:   Device: laptop System: LENOVO product: 2349M88 v: ThinkPad T430 serial: N/A
           Mobo: LENOVO model: 2349M88 serial: N/A
           UEFI [Legacy]: LENOVO v: G1ETB2WW (2.72 ) date: 01/31/2017

```
Intel Graphics:
```
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller
           Display Server: x11 (X.Org 1.19.6 )
           drivers: intel (unloaded: modesetting,fbdev,vesa)
           Resolution: 1600x900@59.98hz
           OpenGL: renderer: Mesa DRI Intel Ivybridge Mobile
           version: 4.2 Mesa 17.3.2

```
Just need some more information when this happens to you if possible.

---

### Post by vincentLin on 2018-01-22
Did you mean these specs?
    description: Desktop Computer
    product: 5067A81 (To be filled by O.E.M.)
    vendor: LENOVO
    version: Lenovo Product
    serial: 1234567
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 smp vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=desktop family=To be filled by O.E.M. keyboard_password=enabled power-on_password=disabled sku=To be filled by O.E.M.

       *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:28 memory:fe000000-fe3fffff memory:d0000000-dfffffff ioport:f000(size=64) memory:c0000-dffff

---

### Post by ajgreeny on 2018-01-22
Let's see the output of command ```
inxi -F
``` which will show us a lot more about your hardware and its specs.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by vincentLin on 2018-01-23
here it is:
```

System:    Host: ubuDesktop Kernel: 4.13.0-25-generic x86_64 bits: 64 Desktop: Gnome 3.26.2
           Distro: Ubuntu 17.10
Machine:   Device: desktop System: LENOVO product: 5067A81 v: Lenovo Product serial: N/A
           Mobo: LENOVO model: N/A serial: N/A BIOS: LENOVO v: 9HKT58AUS date: 06/10/2014
Battery    hidpp__0: charge: N/A condition: NA/NA Wh
           hidpp__1: charge: N/A condition: NA/NA Wh
CPU:       Quad core Intel Core i5-2400S (-MCP-) cache: 6144 KB
           clock speeds: max: 3300 MHz 1: 2494 MHz 2: 2494 MHz 3: 2494 MHz 4: 2494 MHz
Graphics:  Card: Intel 2nd Generation Core Integrated Graphics Controller
           Display Server: x11 (X.Org 1.19.5 ) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel Sandybridge Desktop version: 3.3 Mesa 17.2.4
Audio:     Card-1 Intel 6 Series/C200 Series Family High Def. Audio Controller driver: snd_hda_intel
           Card-2 Logitech Webcam C270 driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.13.0-25-generic
Network:   Card: Intel 82579LM Gigabit Network Connection driver: e1000e
           IF: eno1 state: up speed: 100 Mbps duplex: full mac: 44:37:e6:47:07:37
Drives:    HDD Total Size: 740.2GB (11.5% used)
           ID-1: /dev/sda model: KINGSTON_SA400S3 size: 240.1GB
           ID-2: /dev/sdb model: WDC_WD5000AZRX size: 500.1GB
Partition: ID-1: / size: 20G used: 9.0G (49%) fs: ext4 dev: /dev/sda2
           ID-2: swap-1 size: 2.15GB used: 0.00GB (0%) fs: swap dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 33.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 252 Uptime: 37 min Memory: 2081.4/11835.4MB Client: Shell (bash) inxi: 2.3.37 

```

---

### Post by ajgreeny on 2018-01-23
Is the system more stable if you boot from an earlier kernel from grub?

---

### Post by vincentLin on 2018-01-23
not really. I started to notice this when upgraded from 16.04 LTS to 17.04, then to 17.10. I believe there were kernel upgrades since 16.04 to 17.x. So I went through all of them with no improvement. 

I couldn't find any errors recorded in the logs. my screensaver is set to kick in after 30 mins and since I don't see the screensaver in most cases when it freezes I think it happens before 30 mins expire.

---

### Post by #&amp;thj^% on 2018-01-23
That was my first guess is that you upgraded to 17.10.
My guess here is that some of the junk from upgrading to 2 versions higher possibly. (.conf files)
Have you recently ran:
```
sudo apt autoremove
```
If your worried about anything getting removed that you don't want removed, just paste back the content shown from the terminal.(from the autoremove command)

---

### Post by vincentLin on 2018-01-23
that I did several times. didn't help.

---

### Post by #&amp;thj^% on 2018-01-23
well we could all just guess here all day and never get to the real culprit at hand.
Try running a **"Current"** Live install CD/USB for a few hours then to see if there is any noticeable difference.

---

### Post by VMC on 2018-01-23
Any errors show up on journal:
```
journalctl -p err 
```

---

### Post by vincentLin on 2018-01-28
I started to play int-radio in the background now, all the time. So far that keeps the desktop from get stuck, even when inactive for a long period. Will see for how long.
When, or if, it freezes again -- I'll use the "journalctl -p err"  and show the output here.
Thanks.

---

