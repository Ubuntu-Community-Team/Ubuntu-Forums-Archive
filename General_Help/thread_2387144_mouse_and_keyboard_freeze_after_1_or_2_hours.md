---
title: "mouse and keyboard freeze after 1 or 2 hours"
date: 2018-03-15
forum: General Help
---

### Post by lonewohlf42 on 2018-03-15
Hi, since changing to Ubuntu 17.10 gnome my mouse and keyboard freeze after about 1 to 2 hours. The computer is still running but can't use mouse or keyboard. If I reboot in Unity there is no problem. This is a bug in gnome. the only way to regain control is through a hard reboot. Does anyone have any suggestions on how to solve this problem. I tried to disconnect and reconnect the mouse on the usb port but no success. The num-lock and cap-lock keys don't respond either.

---

### Post by #&amp;thj^% on 2018-03-15
Hardware specs might help here, as there are differences that matter here.
install "inxi" if not already installed.
```
sudo apt install inxi
```
and post back the retrun>>>using code tags:
```
sudo inxi -Fm
```

---

### Post by lonewohlf42 on 2018-03-15
System:    Host: xion Kernel: 4.13.0-37-generic x86_64 bits: 64
           Console: tty 0 Distro: Ubuntu 17.10
Machine:   Device: desktop Mobo: ASUSTeK model: M5A99X EVO R2.0 v: Rev 1.xx serial: 131219693001020
           BIOS: American Megatrends v: 2501 date: 04/03/2014
CPU:       Octa core AMD FX-8350 Eight-Core (-MCP-) cache: 16384 KB
           clock speeds: max: 4000 MHz 1: 1400 MHz 2: 1400 MHz 3: 1400 MHz
           4: 1400 MHz 5: 1400 MHz 6: 1400 MHz 7: 1400 MHz 8: 1400 MHz
Memory:    Array-1 capacity: 32 GB devices: 4 EC: None
           Device-1: DIMM0 size: 4 GB speed: 800 MT/s type: DDR3
           Device-2: DIMM1 size: 4 GB speed: 800 MT/s type: DDR3
           Device-3: DIMM2 size: 4 GB speed: 800 MT/s type: DDR3
           Device-4: DIMM3 size: 4 GB speed: 800 MT/s type: DDR3
Graphics:  Card: NVIDIA GK107 [GeForce GT 640]
           Display Server: X.Org 1.19.5
           drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1280x1024@60.02hz, 1920x1080@60.00hz
           OpenGL: renderer: NVE7 version: 4.3 Mesa 17.2.8
Audio:     Card-1 NVIDIA GK107 HDMI Audio Controller driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.13.0-37-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: eth0 state: up speed: 1000 Mbps duplex: full
           mac: e0:3f:49:12:42:e1
Drives:    HDD Total Size: 4640.9GB (51.8% used)
           ID-1: /dev/sda model: ST2000DM001 size: 2000.4GB
           ID-2: USB /dev/sdb model: My_Passport_0748 size: 2000.4GB
           ID-3: USB /dev/sdc model: 00AACS size: 640.1GB
Partition: ID-1: / size: 1.8T used: 726G (43%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 17.08GB used: 0.00GB (0%)
           fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 17.0C mobo: N/A gpu: 39.0
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 326 Uptime: 13:49 Memory: 3077.8/15941.6MB
           Client: Shell (sudo) inxi: 2.3.37

---

### Post by #&amp;thj^% on 2018-03-15
:D What no Code tags? ;)
Are you using Wayland instead of X11 session then?
To see:
```
echo $XDG_SESSION_TYPE
```
The reason I ask the nvidia-driver could help, but not if you prefer the wayland session.

---

### Post by lonewohlf42 on 2018-03-15
I had to reboot the computer and this time I booted in X11. echo session type know says x11.

---

### Post by lonewohlf42 on 2018-03-15
I don't know if this will fix the problem only time will tell. Does Wayland have problems with it?

---

### Post by lonewohlf42 on 2018-03-15
I don't know how to use code tags.

---

### Post by #&amp;thj^% on 2018-03-15
> **lonewohlf42 said:**
> I had to reboot the computer and this time I booted in X11. echo session type know says x11.

See how it goes on that session then, and if the same behavior is shown, you may want to add the Nvidia Driver to the mix.
**Please Note**: Nvidia and Wayland won't play nicely with each other, and may also remove the option to login to a Wayland Session.
MHO here X11 rocks>>> Wayland not so much.:(>>>If you decide this is a better experience for you, we can disable Wayland.
So let me know, and take your time to decide. ;)

---

### Post by lonewohlf42 on 2018-03-15
OK thanks for the help. I will run this for the day and see what happens and let you know.

---

