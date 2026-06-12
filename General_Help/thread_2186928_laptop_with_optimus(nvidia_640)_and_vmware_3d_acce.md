---
title: "laptop with optimus(nvidia 640) and vmware 3d accel??"
date: 2013-11-09
forum: General Help
---

### Post by tougeattackitr on 2013-11-09
hello i want to run vmware with 3d accell i tryed to use optirun vmware but vm(windows 7) wont start with error "mks unexpected signal 6"
> 00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 640M LE] (rev ff)
its posible to disable onboard intel card and use my nvidia card only?(my bios doesnt support it i think)

i tried also o install nvidia 319 drivers but i dont know how to enable only the nvidia card and i get into fallback

i tried everything i found on web without success :(

---

### Post by Linuxisfast on 2013-11-10
Remove bumblebee, install nvidia-319-updates linux-headers-generic and nvidia-prime your nvidia gpu will be on all the time and used for rendering and Intel will only be used for display. You will have little higher temps and battery consumption.

---

### Post by tougeattackitr on 2013-11-10
i tryed this with nvidia-xconfig but when i log my resolution is 640x480 and in nvidia settings it says  that i do not apear to be using thee nvidia x driver

---

