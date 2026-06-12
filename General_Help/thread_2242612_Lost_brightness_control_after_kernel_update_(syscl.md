---
title: "Lost brightness control after kernel update (/sys/class/backlight/acpi_video0 missing"
date: 2014-09-02
forum: General Help
---

### Post by and.gulla on 2014-09-02
Running Ubuntu 14.04 on my Lenovo Thinkpad T530. During a kernel update I lost the ability to control my brightness and looking into my '/sys/class/backlight' folder I no longer see a 'acpi_video0' folder I used to have. I now only see a shortcut link to '/sys/devices/virtual/backlight/thinkpad_screen'. I believe this is the main reason for the loss of brightness control and am curious how to get back that 'acpi_video0' folder. Below I will attach some information regarding my setup.

xorg.conf
```
Section "Device"    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "NVS 5400M"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
    Option         "ModeValidation" "AllowNonEdidModes"
EndSection
```

/etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
```

I am using xedgers nvidia 340.32 drivers and my kernel version is currently 3.13.0-35.

I believe if I can somehow get back that 'acpi_video0' folder in my '/sys/class/backlight' directory I can fix this. Any help is appreciated.

---

