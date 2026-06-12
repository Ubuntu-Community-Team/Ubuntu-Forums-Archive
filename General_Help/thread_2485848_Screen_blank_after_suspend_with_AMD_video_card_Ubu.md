---
title: "Screen blank after suspend with AMD video card Ubuntu 22.04.2"
date: 2023-04-11
forum: General Help
---

### Post by fimy on 2023-04-11
My screen does not come back after suspend. I have seen people describing this with NVIDIA cards, but I have AMD. This had not happened for ~3 weeks since I built my PC, but started in the last couple of days after I installed MATE. Obviously I suspected MATE had altered something, so I uninstalled it, but the problem persists. For now I have changed my settings so my computer (desktop) does not go to sleep automatically. Curious if anyone else has had this problem.

Here is the result of lshw -c video

*-display UNCLAIMED       
       description: VGA compatible controller
       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: e7
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: iomemory:400-3ff iomemory:420-41f memory:4000000000-41ffffffff memory:4200000000-42001fffff ioport:7000(size=256) memory:86200000-8623ffff memory:86240000-8625ffff
  *-graphics
       product: EFI VGA
       physical id: 2
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=1920,1080

Side note: I tried originally to install the amdgpu drivers provided by  AMD, but ran into dependency errors and ended up uninstalling them. But  this was a few weeks ago and did not cause this error at the time.

---

### Post by MAFoElffen on 2023-04-12
Hmmm. Unclaimed for AMD?

Please post the ouput of:
```

sudo dmesg | grep -i 'amdgpu\|radeon'
sudo lsmod | grep -i 'amd\|radeon'
echo $XDG_SESSION_TYPE
grep . /sys/module/*_idle/parameters/max_cstate
ls /sys/module/*_idle/parameters/max_cstate

```

---

### Post by fimy on 2023-04-13
Below is the output. The first two commands did not yield anything.

$ sudo dmesg | grep -i 'amdgpu\|radeon'
$ sudo lsmod | grep -i 'amd\|radeon'
$ echo $XDG_SESSION_TYPE
x11
$ grep . /sys/module/*_idle/parameters/max_cstate
9
$ ls /sys/module/*_idle/parameters/max_cstate
/sys/module/intel_idle/parameters/max_cstate

---

### Post by fimy on 2023-04-13
Update: I seem to have fixed the problem. By following this [post]("https://askubuntu.com/questions/1441373/swap-xorg-video-driver-from-amdgpu-to-radeon") I ran 
```
sudo modprobe amdgpu
```
This caused an error and logged me out, but when I logged back, dmesg was now showing the amdgpu drivers. I also ran lshw -c video to confirm, and the display was no longer unclaimed, and configuration was showing driver=amdgpu. Most importantly, the computer comes back from suspension with the display working. All good for now. Thank you.

---

### Post by MAFoElffen on 2023-04-13
Exactly what I was going to suggest if the amdgpu driver were not loaded. LOL.

Glad that it is now working for you. If it has any other problems, please feel free to post more on this. There is a Kernel Boot parameter you can add "if needed".

Test it a bit to make sure if it is resolved.

If this is now solved to your satisfaction, then please use the "Thread Tools" link at the upper right of the page to mark this as Solved.

---

### Post by fimy on 2023-04-13
It's not quite resolved. Overnight I had the power settings set to suspend automatically, and when I tried to reawaken the computer I ran into the problem again. Somehow the config seems to have reverted. I ran lshw -c video, and it showed the display was once again unclaimed. Running modprobe amdgpu gave me the same result as before: logged me out, but when I got back in the display was claimed, and the amdgpu driver was loaded. Is there some step that I need to take so the config is saved? I don't know why it would revert like that.

---

### Post by MAFoElffen on 2023-04-13
The whole answer that covers everything:
Please do this:
```

sudo nano /etc/default/grub

```
Change this line to this:
```

GRUB_CMDLINE_LINUX_DEFAULT="-- quiet splash[COLOR=#ff0000] intel_idle.max_cstate=4[/COLOR]"

```
Save and exit, then...
```

sudo update-grub
sudo modprobe amdgpu
sudo update-initramfs -u
sudo echo "amdgpu" >> /etc/module-load.d/modules.conf
sudo reboot

```

---

### Post by fimy on 2023-04-13
Thank you for your help on this. I ran these commands, but I got a list of possible firmware missing after sudo update-initramfs -u. After reboot, I run into the same problem. Current output right after reboot from ```
$ sudo lshw -c video
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: e7
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: iomemory:400-3ff iomemory:420-41f memory:4000000000-41ffffffff memory:4200000000-42001fffff ioport:7000(size=256) memory:86200000-8623ffff memory:86240000-8625ffff
  *-graphics
       product: EFI VGA
       physical id: 2
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=1920,1080
```

---

### Post by MAFoElffen on 2023-04-14
> **fimy said:**
> I ran these commands, but I got a list of possible firmware missing after sudo update-initramfs -u. 

And what did the list say? That may be helpful to know what the error said...

---

### Post by fimy on 2023-04-14
Thank you. Here is the list:
W: Possible missing firmware /lib/firmware/amdgpu/ip_discovery.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega10_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sienna_cichlid_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi12_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/aldebaran_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_0_toc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sienna_cichlid_mes1.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sienna_cichlid_mes.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi10_mes.bin for module amdgpu
grep: /usr/share/plymouth/themes/ubuntu-mate-logo/ubuntu-mate-logo.plymouth: No such file or directory
W: plymouth module (/usr/lib/x86_64-linux-gnu/plymouth//.so) missing, skipping that theme.

---

### Post by MAFoElffen on 2023-04-16
If you have the HWE stack installed and are running 5.19.x kernels, then do
```

sudo apt install --renistall linux-firmware

```

---

