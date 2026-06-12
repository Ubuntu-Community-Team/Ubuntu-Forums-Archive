---
title: "Can't get Ubuntu to open"
date: 2007-10-21
forum: General Help
---

### Post by thomasyen on 2007-10-21
Hello,
I'm a Windows XP/Ubuntu 7.10 dual boot user. A few weeks ago, my Windows system crashed repeatedly because of a worm, and so I had my Windows C drive formatted. However, after the format had been done, I found that I could no longer access Ubuntu. I installed Ubuntu on a different partition from the ones Windows used, so I can't figure out why I can't access it (by access I mean to boot under Ubuntu). Now I can only boot my computer under Windows. I have tried to fix this problem by reinstalling Ubuntu, but it can only be installed on a clean partition. I then tried to install Ubuntu Studio on the partition Ubuntu originally used, but I had no success. Does anyone have any idea how to fix this? Thank you...

My computer specs:

Processor Information:
    Vendor:  GenuineIntel
    Speed: 2807 Mhz
    2 logical processors
    1 physical processor
    HyperThreading:  Supported
    RDTSC:  Supported
    CMOV:  Supported
    FCMOV:  Supported
    SSE:  Supported
    SSE2:  Supported
    3DNOW:  Unsupported

Windows Version:
    Windows XP (32 bit)
    NTFS:  Supported

Video Card:
    Driver:  NVIDIA GeForce 7300 GT
    DirectX Driver Name:  nv4_disp.dll
    Driver Version:  6.14.11.6371
    DirectX Driver Version:  6.14.11.6371
    Driver Date: 16 Sept 2007
    Desktop Color Depth: 32 bits per pixel
    Monitor Refresh Rate: 60 Hz
    DirectX Card: NVIDIA GeForce 7300 GT
    VendorID:  0x10de
    DeviceID:  0x2e2
    Number of Monitors:  1
    Number of Video Cards:  1
    No SLI or Crossfire Detected
    Primary Display Resolution:  1024 x 768
    Desktop Resolution: 1024 x 768
    Primary Display Size: 13.39" x 10.04"  (16.73" diag)
                                            34.0cm x 25.5cm  (42.5cm diag)
    Primary Bus: AGP 8x
    Primary AGP GART: 64 MB
    Primary VRAM: 256 MB
    Primary Monitor Vendor:  BenQ
    Primary Monitor Model:  BenQ FP731
    Supported MSAA Modes:  2x 4x     

Sound card:
    Audio device: SoundMAX Digital Audio

Memory:
    RAM:  1022 Mb

Miscellaneous:
    UI Language:  English
    Media Type:  DVD
    Total Hard Disk Space Available:  229671 Mb
    Largest Free Hard Disk Block:  53216 Mb 

*Other questions:
1. Before the format, I had my Ubuntu updated to Gutsy, but after the update I could no longer play videos or activate Firefox. Any ideas?
2. When I tried to install Ubuntu Studio, I checked to see which partition I could install to. However, I found that the partition sizes the installer provided were different from the ones provided by Windows. I am quite confused. 
3. I added up the total size of the partitions that could be used by Windows and found it to be 220 GB.  I know my drive is a 320 GB drive, so I'm wondering what happened to the other 100 GB. (The partition that I provided for my original installation of Ubuntu is 20 GB.) Can anyone help me out?

---

### Post by MegaSvensk on 2007-10-21
Try this in a terminal in an Ubuntu live cd:
```
grub
find boot/grub/stage1
root (hdx.x) (you fill in the x's with whatever numbers the "find" command shows.)
setup (hdx.x)
```

Then reboot and hopefully Grub will show you working Ubuntu and Windows boot options.

---

### Post by thomasyen on 2007-10-21
I tried it out, and the terminal replied that the file could not be found (when I got to the second line)...

---

### Post by zvacet on 2007-10-21
[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub]("http://ubuntuforums.org/showthread.php?t=24113&highlight=grub")

---

### Post by MegaSvensk on 2007-10-21
Did you run Grub as sudo? I forgot to write that.

Also, it should be "setup (hdx)" not x.x .

---

### Post by thomasyen on 2007-10-25
I didn't use sudo, but I was logged in as an administrator. Does it make a difference?

---

### Post by thomasyen on 2007-10-27
Thanks guys, I solved my problem (by reinstalling the whole system).

---

