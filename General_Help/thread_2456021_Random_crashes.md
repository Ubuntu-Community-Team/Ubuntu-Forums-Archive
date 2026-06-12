---
title: "Random crashes"
date: 2021-01-02
forum: General Help
---

### Post by dome78 on 2021-01-02
Hi everyone,
I use ubuntu 20.04. Sometimes I have experienced random crashes in two circumstances:
- when i play 3d games 
- when i play videos with mpv or vlc

The screen freezes (mouse and keyboard don't work), the monitor turns black for some seconds, afterwards the screen becomes visible again, but freezed. 
I believe the problem is the video card.
What log file can I view to understand the cause after the crash?
Thanks

---

### Post by dino99 on 2021-01-02
crash file is stored into /var/crash/

to know what have happened, you can watch the 'journalctl -b' output into a terminal: red lines are errors, yellow ones ares warnings and can be mostly ignored.

---

### Post by TheFu on 2021-01-02
Check the system logs.  Google "ubuntu log files" if you need help with that.

If you think it is a video card problem, which is very reasonable, perhaps stating the exact model of card and showing the currently loaded drivers would be helpful?
**inxi -G** command will provide that information. For example:
```
$ inxi -G
Graphics:  Card: NVIDIA GP108 [**GeForce GT 1030**]
           Display Server: X.Org 1.19.6 driver: **nvidia**
           Resolution: 1920x1200@59.95hz
           GLX Renderer: GeForce GT 1030/PCIe/SSE2
           GLX Version: 4.6.0 **NVIDIA 430.64**
```
helpful information for troubleshooting needs, but the log files should have more.

Have you patched the system this week, fully?
**sudo apt update && sudo apt full-upgrade**

---

### Post by dome78 on 2021-01-03
Graphics:
  Device-1: AMD Curacao XT / Trinidad XT [Radeon R7 370 / R9 270X/370X] 
  driver: radeon v: kernel 
  Display: x11 server: X.Org 1.20.8 driver: radeon 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: AMD PITCAIRN (DRM 2.50.0 5.4.0-58-generic LLVM 10.0.0) 
  v: 4.5 Mesa 20.0.8 

Card model: radeon R9 270X


> **TheFu said:**
> Check the system logs.  Google "ubuntu log files" if you need help with that.

If you think it is a video card problem, which is very reasonable, perhaps stating the exact model of card and showing the currently loaded drivers would be helpful?
**inxi -G** command will provide that information. For example:
```
$ inxi -G
Graphics:  Card: NVIDIA GP108 [**GeForce GT 1030**]
           Display Server: X.Org 1.19.6 driver: **nvidia**
           Resolution: 1920x1200@59.95hz
           GLX Renderer: GeForce GT 1030/PCIe/SSE2
           GLX Version: 4.6.0 **NVIDIA 430.64**
```
helpful information for troubleshooting needs, but the log files should have more.

Have you patched the system this week, fully?
**sudo apt update && sudo apt full-upgrade**

---

### Post by dome78 on 2021-01-13
I have read the  journalctl result and this seems the begin of the problem:

radeon 0000:26:00.0: ring 5 stalled for more than 10240msec
radeon 0000:26:00.0: ring 0 stalled for more than 10504msec
radeon 0000:26:00.0: GPU lockup (current fence id 0x0000000000b31af9 last fence id 0x0000000000b31b38 on ring 0)
radeon 0000:26:00.0: GPU lockup (current fence id 0x0000000000000d08 last fence id 0x0000000000000d0b on ring 5)
radeon 0000:26:00.0: scheduling IB failed (-35).
[drm:radeon_gem_va_ioctl [radeon]] *ERROR* Couldn't update BO_VA (-35)
radeon 0000:26:00.0: scheduling IB failed (-35).
[drm:radeon_gem_va_ioctl [radeon]] *ERROR* Couldn't update BO_VA (-35)
radeon 0000:26:00.0: scheduling IB failed (-35).
[drm:radeon_gem_va_ioctl [radeon]] *ERROR* Couldn't update BO_VA (-35)
radeon 0000:26:00.0: scheduling IB failed (-35).
[drm:radeon_gem_va_ioctl [radeon]] *ERROR* Couldn't update BO_VA (-35)
radeon 0000:26:00.0: scheduling IB failed (-35).
[drm:radeon_gem_va_ioctl [radeon]] *ERROR* Couldn't update BO_VA (-35)
 radeon 0000:26:00.0: scheduling IB failed (-35).

(loop of the 2 last lines)

After that, this error appears in loop
radeon: Failed to deallocate virtual address for buffer:etc. etc.

---

### Post by dome78 on 2021-03-18
I solved: I installed mpv from official site (the default repository is old)

---

### Post by TheFu on 2021-03-18
> **dome78 said:**
> I solved: I installed mpv from official site (the default repository is old)

Great!

Please use the "Thread Tools" button near the top of this page to mark this thread as solved. This helps the community find working solutions to problems.  Excellent on posting the errors as well as what you believe the core issue was. Thanks!

---

