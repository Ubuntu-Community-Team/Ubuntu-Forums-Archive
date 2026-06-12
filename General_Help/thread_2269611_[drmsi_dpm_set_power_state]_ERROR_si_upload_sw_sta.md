---
title: "[drm:si_dpm_set_power_state] *ERROR* si_upload_sw_state failed"
date: 2015-03-17
forum: General Help
---

### Post by anuj_malviya on 2015-03-17
Hi All
I installed Ubuntu 14.04 version on my new laptop Lenovo G50-45. AMD Radeon processor. I am facing following problems.
1) My system hangs after some time when I saw the /var/log/.kernel.log I got
 this message "[drm:si_dpm_set_power_state] *ERROR* si_upload_sw_state failed".
2) Also I see this message " No back light controller" installed on the system.
First problem usually occurs when I am browsing thru mozilla. I have not insstalled any other browser.
 
Any one having any clues what can solve this problem. I guess this is not related with the hardware.

Regards
Anuj

---

### Post by bubi3 on 2015-03-18
I got the same on my lenovo on the console when booting. it ends in an endless loop. It does not come up. :-(. Does anybody know what this error means?

---

### Post by anuj_malviya on 2015-03-19
Posting logs for reference. 

```
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   19.555981] [drm] ring test on 4 succeeded in 4 usecs
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   19.556474] [drm] ib test on ring 0 succeeded in 0 usecs
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   19.556535] [drm] ib test on ring 1 succeeded in 0 usecs
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   19.556569] [drm] ib test on ring 2 succeeded in 0 usecs
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   19.895380] EXT4-fs (sda2): mounting ext2 file system using the ext4 subsystem
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   19.901038] EXT4-fs (sda2): mounted filesystem without journal. Opts: (null)
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   20.054966] [drm] ib test on ring 3 succeeded in 0 usecs
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   20.054992] [drm] ib test on ring 4 succeeded in 0 usecs
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   20.055794] [drm] Radeon Display Connectors
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   20.055866] radeon 0000:01:00.0: No connectors reported connected with modes
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   20.055870] [drm] Cannot find any crtc or sizes - going 1024x768
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   20.060111] [drm] fb mappable at 0xD0242000
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   20.060113] [drm] vram apper at 0xD0000000
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   20.060115] [drm] size 3145728
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   20.060117] [drm] fb depth is 24
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   20.060119] [drm]    pitch is 4096
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   20.060247] radeon 0000:01:00.0: fb1: radeondrmfb frame buffer device
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   20.079427] [drm:si_dpm_set_power_state] *ERROR* si_upload_sw_state failed
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   20.079805] [drm:radeon_acpi_init] *ERROR* Cannot find a backlight controller
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   20.079915] [drm] Initialized radeon 2.39.0 20080528 for 0000:01:00.0 on minor 1
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   21.429188] audit_printk_skb: 6 callbacks suppressed
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   21.429195] audit: type=1400 audit(1426675097.858:14): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=857 comm="apparmor_parser"
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   21.429207] audit: type=1400 audit(1426675097.858:15): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=857 comm="apparmor_parser"
Mar 18 16:08:17 Gucchi-Tulio-G50-45 kernel: [   21.429883] audit: type=1400 audit(1426675097.858:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=857 comm="apparmor_parser"
Mar 18 16:08:18 Gucchi-Tulio-G50-45 kernel: [   21.960041] Bluetooth: RFCOMM TTY layer initialized
```

[http://askubuntu.com/questions/493887/error-cannot-find-backlight-controller-for-radeon-acpi-graphics-card](http://askubuntu.com/questions/493887/error-cannot-find-backlight-controller-for-radeon-acpi-graphics-card)

Check the following post for back light controller problem. Simple setting.

Regards
Anuj

Hi All
My system configuration is AMD Radeon A8 with 8 GB Ram and Realtek Wlan card.
My system some time freezes and I have to do a hard reboot every time.
This usually happens while browsing, have tried both Mozilla and Chrome browser.
On seeing syslogs I see this message
" si_upload_sw_state failed ".

Not sure if it is related with this problem.
Regards
Anuj

---

### Post by oldos2er on 2015-03-22
Threads merged; please only create one thread for the same or similar questions, it's confusing and it dilutes the community's ability to help.

---

### Post by anuj_malviya on 2015-03-25
Hi 
For this problem need to install AMD Catalyst.
Please go through the following link/discussion from Fedora forums.
1) [https://bbs.archlinux.org/viewtopic.php?id=186388](https://bbs.archlinux.org/viewtopic.php?id=186388)
2) support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx

Though I have not done it but need to know if we can directly sudo apt-get install to check for the driver.
Regards
Anuj

Now I am stuck How do I install this driver. 
Not sure If this driver is already there in my system.
Regards
Anuj

I installed the driver and my system never recovered back from it. 
I had to do re-installation of the OS :mad:. 
Not sure If this was the correct version. I will try to check if there has been any update on the Catalyst driver.

[h=1][SIZE=1]Will try with this AMD Catalyst™ 14.9 Linux [/SIZE][/h]

[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

