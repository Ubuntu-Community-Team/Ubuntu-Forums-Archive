---
title: "Setup custom resolution on extended monitor"
date: 2023-02-06
forum: General Help
---

### Post by milesrosario on 2023-02-06
Hi there, my problem is that I was running Ubuntu 21.10 with 2 extended monitors without any trouble but now after installing Ubuntu 22.04 from scratch one of the extended monitors (a DELL connected through DisplayPort) doesn't allow me to select resolution 1920x1080, it's stuck at 1024x768 (4:3) and shown as "Unknown Display" on Settings>Displays. The other extended screen (a Philips) is working fine on HDMI showing the desired resolution of 1920x1080 (16:9) as well as the right name/ID. The built-in dsplay of the Laptop (HP Elitebook) is as well working fine with 1920x1080 (16:9).

 $ xrandr -qScreen 0: minimum 16 x 16, current 4864 x 1080, maximum 32767 x 32767
XWAYLAND0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      59.92*+
   800x600       59.86  
   640x480       59.38  
   320x240       59.52  
   720x480       59.71  
   640x400       59.95  
   320x200       58.96  
   1024x576      59.90  
   864x486       59.92  
   720x400       59.55  
   640x350       59.77  
XWAYLAND1 connected 1920x1080+1024+0 (normal left inverted right x axis y axis) 530mm x 300mm
   1920x1080     59.96*+
   1440x1080     59.99  
   1400x1050     59.98  
   1280x1024     59.89  
   1280x960      59.94  
   1152x864      59.96  
   1024x768      59.92  
   800x600       59.86  
   640x480       59.38  
   320x240       59.52  
   1680x1050     59.95  
   1440x900      59.89  
   1280x800      59.81  
   720x480       59.71  
   640x400       59.95  
   320x200       58.96  
   1600x900      59.95  
   1368x768      59.88  
   1280x720      59.86  
   1024x576      59.90  
   864x486       59.92  
   720x400       59.55  
   640x350       59.77  
XWAYLAND2 connected primary 1920x1080+2944+0 (normal left inverted right x axis y axis) 290mm x 170mm
   1920x1080     59.96*+
   1440x1080     59.99  
   1400x1050     59.98  
   1280x1024     59.89  
   1280x960      59.94  
   1152x864      59.96  
   1024x768      59.92  
   800x600       59.86  
   640x480       59.38  
   320x240       59.52  
   1680x1050     59.95  
   1440x900      59.89  
   1280x800      59.99  
   720x480       59.71  
   640x400       59.95  
   320x200       58.96  
   1600x900      59.95  
   1368x768      59.88  
   1280x720      59.86  
   1024x576      59.90  
   864x486       59.92  
   720x400       59.55  
   640x350       59.77 


$ inxi -Gx
Graphics:
  Device-1: AMD Renoir vendor: Hewlett-Packard driver: amdgpu v: kernel
    bus-ID: 03:00.0
  Device-2: Luxvisions Innotech HP HD Camera type: USB driver: uvcvideo
    bus-ID: 3-4:3
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell v: 42.5 driver: gpu: amdgpu resolution:
    1: 1024x768~60Hz 2: 1920x1080~60Hz 3: 1920x1080~60Hz
  OpenGL: renderer: RENOIR (renoir LLVM 15.0.6 DRM 3.42 5.15.0-58-generic)
    v: 4.6 Mesa 22.2.5 direct render: Yes


Any ideas how to fix this?

---

### Post by milesrosario on 2023-02-08
Problem solved by editing /etc/default/grub by appending to the entry GRUB_CMDLINE_LINUX_DEFAULT video={PORT_ID}:{RESOLUTION}@{REFRESH_FREQUENCY} as follows:

*GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=DP-3:1920x1080@60"*

---

