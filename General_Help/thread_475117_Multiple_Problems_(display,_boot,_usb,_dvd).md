---
title: "Multiple Problems (display, boot, usb, dvd)"
date: 2007-06-15
forum: General Help
---

### Post by mailbox on 2007-06-15
Thanks in advance to anyone who goes for even one of these.


**First:** my lcd's native resolution is 1920x1600, and I have xorg.conf set up like so (not the entire xorg.conf, just the part i thought relevant):```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7900 GTX]"
    Monitor        "FPD2485W"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1680x1680" "1600x1200" "1440x1440" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```However, whenever I boot up (into Xfce), the resolution is set to 1600x1200, and I have to use nvidia-settings to set it to 1920x1200. It never stays that way. Interestingly enough, though, GDM is running at 1920x1200, but Xfce-desktop isn't, so I assume it's an Xfce problem, but nobody on IRC seems to think that Xfce controls screen resolution.


**Secondly:** Also every time I boot, I get the following message (not the real message, this is from the log. the real message drops me into some maintenance shell, or something, which it says i can exit with control-d. if i use ctrl-d to get out, everything else seems to boot fine):```
Log of fsck -C -R -A -a 
Fri Jun 15 15:36:43 2007

fsck 1.40-WIP (14-Nov-2006)
/dev/sda3: clean, 47056/34619392 files, 44868439/69216052 blocks
Failed to open the device 'UUID=fbc83355-d65b-4ebb-82ea-b8ef80dccfb4': No such file or directory


fsck died with exit status 8

Fri Jun 15 15:36:43 2007
----------------
```ls -l /dev/disk/by-uuid returns: ```
total 0
lrwxrwxrwx 1 root root 10 2007-06-15 15:36 65691683-d670-4bf2-8c20-7dd53aeca33c -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-06-15 15:36 8a70e45d-b0b3-4dd2-9764-26c0e355e999 -> ../../hdc1
lrwxrwxrwx 1 root root 10 2007-06-15 15:36 e649e940-77c6-4783-851a-6e6e61ea1402 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-06-15 15:36 f01ffea6-511a-4027-88cd-42c5c7630df8 -> ../../sda3
``` and I didn't edit any of this on my own, so i'm not sure at all where that UUID came from.



**Third:** If I have a USB device plugged in (thumb drive, camera, even a hub), my box stops booting and dies with the following: ```
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ACPI: PCI Interrupt link [LUB0] enabled at IRQ 21
ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUB0] -> GSI 21 (level, low) -> IRQ 50
ohci_hdc 0000:00:0b.0: OHCI Host Controller
ohci_hdc 0000:00:0b.0: new USB bus registered, assigned bus number 1
```Like I said, when it gets to this point, it will die and halt boot. If I boot without anything usb plugged in, it will boot fine (excepting, of course, the aforementioned problem).


**Fourth:** My DVD drive isn't being detected properly.
I had a CDRW in there before (same place on the ide cable, same jumper settings - master); I pulled that out and put a DVDRW in there, and Sound Juicer tells me there aren't any CDROM drives to read from. The drive does have CDROM reading capabilities, and (at the moment) I'm not worried about watching DVD's on it; I just want to rip this Basshunter album. The old drive is in a second box now (had to go back to windows... for ONE program :frown: ), so I can't move it back here.

---

### Post by mailbox on 2007-06-15
anyone? anything?

---

### Post by mailbox on 2007-06-21
bump =/

---

