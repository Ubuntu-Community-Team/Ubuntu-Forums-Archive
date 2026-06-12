---
title: "No AMDGPU after update to kernel 5.11"
date: 2021-10-16
forum: General Help
---

### Post by dougdeep2 on 2021-10-16
After updating Ubuntu 20.04.3 LTS to kernel 5.11 from 5.8 I started noticing odd video glitches and discovered Ubuntu was now using the software renderer LLVMPIPE instead of the AMDGPU driver.  I have an AMD Radeon R7 240 that has been in use for months.  Ubuntu originally set it up using the Radeon open source driver but I got it to use the AMDGPU driver by adding “.si_support” to the grub command.
 ```

 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.si_support=0 amdgpu.si_support=1"
 
```
 The computer would show-
 ```

 inxi -Fzx
 System:    Kernel: 5.8.0-48-generic x86_64 bits: 64 compiler: N/A Desktop: Gnome 3.36.9  
            Distro: Ubuntu 20.04.3 LTS (Focal Fossa)  
 Machine:   Type: Desktop System: Hewlett-Packard product: HP Compaq dc7800 Small Form Factor v: N/A serial: <filter>  
            Mobo: Hewlett-Packard model: 0AA8h serial: <filter> BIOS: Hewlett-Packard v: 786F1 v01.35 date: 10/23/2015  
 CPU:       Topology: Quad Core model: Intel Core2 Quad Q6700 bits: 64 type: MCP arch: Core Merom rev: B L2 cache: 4096 KiB  
            flags: lm nx pae sse sse2 sse3 ssse3 bogomips: 21279  
            Speed: 1596 MHz min/max: 1596/2667 MHz Core speeds (MHz): 1: 1596 2: 1596 3: 1596 4: 1596  
 Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Oland PRO [Radeon R7 240/340] vendor: Hightech Information System  
            driver: amdgpu v: kernel bus ID: 01:00.0  
            Display: x11 server: X.Org 1.20.11 driver: ati,vesa unloaded: fbdev,modesetting,radeon resolution: 1680x1050~60Hz  
            OpenGL: renderer: AMD Radeon HD 8500 series (OLAND DRM 3.38.0 5.8.0-48-generic LLVM 12.0.0) v: 4.6 Mesa 21.0.3  
            direct render: Yes  
 
 
 lspci -k | grep -EA3 'VGA|3D|Display'
 01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Oland PRO [Radeon R7 240/340]
     Subsystem: Hightech Information System Ltd. Oland PRO [Radeon R7 240/340]
     Kernel driver in use: amdgpu
     Kernel modules: radeon, amdgpu
 
```
 
 
 After the kernel 5.11 update, the computer now shows:
 ```

 inxi -Fzx
 System:
   Kernel: 5.11.0-37-generic x86_64 bits: 64 compiler: N/A  
   Desktop: Gnome 3.36.9 Distro: Ubuntu 20.04.3 LTS (Focal Fossa)  
 Machine:
   Type: Desktop System: Hewlett-Packard  
   product: HP Compaq dc7800 Small Form Factor v: N/A serial: <filter>  
   Mobo: Hewlett-Packard model: 0AA8h serial: <filter> BIOS: Hewlett-Packard  
   v: 786F1 v01.35 date: 10/23/2015  
 CPU:
   Topology: Quad Core model: Intel Core2 Quad Q6700 bits: 64 type: MCP  
   arch: Core Merom rev: B L2 cache: 4096 KiB  
   flags: lm nx pae sse sse2 sse3 ssse3 bogomips: 21279  
   Speed: 1596 MHz min/max: 1596/2667 MHz Core speeds (MHz): 1: 1596 2: 1596  
   3: 1596 4: 1596  
 Graphics:
   Device-1: AMD Oland PRO [Radeon R7 240/340]  
   vendor: Hightech Information System driver: N/A bus ID: 01:00.0  
   Display: x11 server: X.Org 1.20.11 driver: ati,vesa  
   unloaded: fbdev,modesetting,radeon resolution: 1680x1050~N/A  
   OpenGL: renderer: llvmpipe (LLVM 12.0.0 128 bits) v: 4.5 Mesa 21.0.3  
   direct render: Yes 
 
 
 lspci -k | grep -EA3 'VGA|3D|Display'  
 01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Oland PRO [Radeon R7 240/340]
     Subsystem: Hightech Information System Ltd. Oland PRO [Radeon R7 240/340]
     Kernel modules: radeon, amdgpu
 
```
 
 
 I found that I can at least get Ubuntu to use the Radeon driver by editing out the “.si_support” from the grub command.   
 ```

 inxi -Fzx
 System:
   Kernel: 5.11.0-37-generic x86_64 bits: 64 compiler: N/A  
   Desktop: Gnome 3.36.9 Distro: Ubuntu 20.04.3 LTS (Focal Fossa)  
 Machine:
   Type: Desktop System: Hewlett-Packard  
   product: HP Compaq dc7800 Small Form Factor v: N/A serial: <filter>  
   Mobo: Hewlett-Packard model: 0AA8h serial: <filter> BIOS: Hewlett-Packard  
   v: 786F1 v01.35 date: 10/23/2015  
 CPU:
   Topology: Quad Core model: Intel Core2 Quad Q6700 bits: 64 type: MCP  
   arch: Core Merom rev: B L2 cache: 4096 KiB  
   flags: lm nx pae sse sse2 sse3 ssse3 bogomips: 21279  
   Speed: 1596 MHz min/max: 1596/2667 MHz Core speeds (MHz): 1: 1596 2: 1596  
   3: 1597 4: 1596  
 Graphics:
   Device-1: AMD Oland PRO [Radeon R7 240/340]  
   vendor: Hightech Information System driver: radeon v: kernel bus ID: 01:00.0  
   Display: x11 server: X.Org 1.20.11 driver: ati,vesa  
   unloaded: fbdev,modesetting,radeon resolution: 1680x1050~60Hz  
   OpenGL: renderer: AMD OLAND (DRM 2.50.0 5.11.0-37-generic LLVM 12.0.0) v: 4.5 Mesa 21.0.3 direct render: Yes  
 
 
 lspci -k | grep -EA3 'VGA|3D|Display'
 01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Oland PRO [Radeon R7 240/340]
     Subsystem: Hightech Information System Ltd. Oland PRO [Radeon R7 240/340]
     Kernel driver in use: radeon
     Kernel modules: radeon, amdgpu
 
```
 
 
 I would rather use the AMDGPU driver since it gives better performance with programs that change screen resolution frequently but I can live with the Radeon driver for the time being.
 
 
 Were the “.si_support” or other options for Radeon/AMDGPU drivers removed from kernel 5.11?  Does anyone know of something that now takes its place?

---

### Post by dougdeep2 on 2021-10-20
After digging through a lot of Google entries, I found the fix for amdgpu.  Someone in the Linux Mint forum was having trouble getting a newer AMD card to work and the suggestion was to look in the dmesg logs (/var/log/dmesg).  They suggested that there would be dmesg entries for the problem and, sometimes, a suggested fix.  When I checked my dmesg log I found these pertinent lines:
 ```

 [    6.165565] kernel: amdgpu 0000:01:00.0: Direct firmware load for amdgpu/oland_uvd.bin failed with error -2
 [    6.165573] kernel: amdgpu 0000:01:00.0: amdgpu: amdgpu_uvd: Can't load firmware "amdgpu/oland_uvd.bin"
 [    6.165579] kernel: [drm:amdgpu_device_ip_init [amdgpu]] *ERROR* sw_init of IP block <uvd_v3_1> failed -2
 [    6.165977] kernel: amdgpu 0000:01:00.0: amdgpu: amdgpu_device_ip_init failed
 [    6.165980] kernel: amdgpu 0000:01:00.0: amdgpu: Fatal error during GPU init
 [    6.165985] kernel: amdgpu 0000:01:00.0: amdgpu: amdgpu: finishing device.
 
```
 Looking for a firmware file on the computer called “oland_uvd.bin” yielded nothing.  An online search revealed that it is supposed to be included in the library that goes with amdgpu.  Downloading a copy from the internet (Git Umio-Yasuno / unofficial-amdgpu-firmware-repo and anduin.linuxfromscratch.org seem to be good sources) and sticking it in lib/firmware/amdgpu and then reseting the computer brought up the desktop with AMD graphics instead of LLVMPIPE.

---

### Post by oxfordstereo on 2021-10-20
I've had the same problem as you for months.  I tried your solution  using "oland_uvd.bin" from  [https://github.com/Umio-Yasuno/unofficial-amdgpu-firmware-repo/blob/main/amdgpu/oland_uvd.bin](https://github.com/Umio-Yasuno/unofficial-amdgpu-firmware-repo/blob/main/amdgpu/oland_uvd.bin)  but it did not work unfortunately.

EDIT: At first I skipped checking that log because I could not find it.  Upon closer inspection I found the log and the file my computer was missing was "tahiti_uvd.bin", so downloading that file and moving it to the proper folder fixed the issue.  Thank you!

---

