---
title: "[pulseaudio] bluez5-util.c: GetManagedObjects() failed:"
date: 2020-06-11
forum: General Help
---

### Post by w2co on 2020-06-11
Has anyone had this recurring problem lately? Ubuntu 18.04 was running perfectly up to this past week.
And here it is again today, I believe there was a kernel update just before this all started.

From log:
[pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)

Does anyone know what to do to get rid of this system error? We don't run anything Bluetooth, 
Already removed anything that may e bluetooth related as well, including Pulseaudio itself!

Thanks in advance for any replies,
W2CO

---

### Post by norobro on 2020-06-11
> **w2co said:**
> Already removed anything that may e bluetooth related as well, including Pulseaudio itself!I don't think you would be seeing that error if you have removed pulseaudio.

Try:```
sudo apt-get remove pulseaudio-module-bluetooth
```

---

### Post by w2co on 2020-06-13
Yes pulseaudio is removed however that bluetooth module may still be active. Thanks I will try..

---

### Post by w2co on 2020-06-13
Well did that and rebooted, still has that system problem detected popup soon after reaching the desktop. I noticed upon doing a "dmesg" there are a few warnings concerning ACPI..

[   10.728054] ACPI Warning: SystemIO range 0x0000000000001828-0x000000000000182F conflicts with OpRegion 0x0000000000001800-0x000000000000187F (\PMIO) (20190703/utaddress-213)
[   10.728058] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.728065] ACPI Warning: SystemIO range 0x0000000000001C40-0x0000000000001C4F conflicts with OpRegion 0x0000000000001C00-0x0000000000001FFF (\GPR) (20190703/utaddress-213)
[   10.728067] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.728068] ACPI Warning: SystemIO range 0x0000000000001C30-0x0000000000001C3F conflicts with OpRegion 0x0000000000001C00-0x0000000000001C3F (\GPRL) (20190703/utaddress-213)
[   10.728069] ACPI Warning: SystemIO range 0x0000000000001C30-0x0000000000001C3F conflicts with OpRegion 0x0000000000001C00-0x0000000000001FFF (\GPR) (20190703/utaddress-213)
[   10.728071] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.728071] ACPI Warning: SystemIO range 0x0000000000001C00-0x0000000000001C2F conflicts with OpRegion 0x0000000000001C00-0x0000000000001C3F (\GPRL) (20190703/utaddress-213)
[   10.728073] ACPI Warning: SystemIO range 0x0000000000001C00-0x0000000000001C2F conflicts with OpRegion 0x0000000000001C00-0x0000000000001FFF (\GPR) (20190703/utaddress-213)
[   10.728075] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver

What is ACPI?

The system is still stable, I have found others saying to just ignore it. I can't ignore it, comes up after every boot now.
When I have people over who run windoz, it's embarrassing

---

### Post by w2co on 2020-06-13
Ok I found what ACPI is.. The Advanced Configuration and Power Interface (ACPI) specification was developed to establish industry common interfaces enabling robust operating system (OS) directed motherboard device configuration and power management of both devices and entire systems. ACPI is the key element in OS-directed configuration and Power Management

This is a small list and summary of ACPI kernel modules:

    ac (power connector status)
    asus-laptop (useful on ASUS/medion laptops)
    battery (battery status)
    bay (bay status)
    button (catch button events, like LID or POWER BUTTON)
    container (container status)
    dock (docking station status)
    fan (fan status)
    i2c_ec (EC SMBUs driver)
    thinkpad_acpi (useful on Lenovo Thinkpad laptops)
    processor (processor status)
    sbs (smart battery status)
    thermal (status of thermal sensors)
    toshiba_acpi (useful for Toshiba laptops)
    video (status of video devices)
The only module we have appears to be the battery monitor.

The ICH GPIO driver fails to load because the hardware is already claimed by ACPI.

It's  also highly likely that we don't care about southbridge GPIOs. They are  typically used by BIOS and ACPI to control stuff on the motherboard.
On another thread, they said by installing the latest headers solved it. 

 					
I think they just had new headers in the latest update, 18.04.4 still there. 
I can forget about this except for the pop up system warning...

---

