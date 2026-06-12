---
title: "ubuntu not loading after grub menu"
date: 2015-01-02
forum: General Help
---

### Post by Arlan on 2015-01-02
Hi there, is ubuntu incompatible with acer E5-411? I installed ubuntu on my acer e5-411. Got no problems during installation. The problem is on boot up process. Most of the time that I turn on my laptop, ubuntu would not load. What I can only see on my laptop is a blinking cursor after the GRUB menu. I tried reinstalling ubuntu for 4 times but the same problem persists. Please watch this video: [http://youtu.be/ev87BC5iaa0](http://youtu.be/ev87BC5iaa0)

---

### Post by davidchute26 on 2015-01-02
Is secure boot enabled?

---

### Post by yancek on 2015-01-02
Since you do not indicate any other operating system on the computer, we have to assume you have only Ubuntu.  If all you get is a blinking cursor, that would be an indication that the Grub bootloader was not properly installed.  Do you remember which option you selected during the install?

---

### Post by Arlan on 2015-01-02
Yes, ubuntu is the only OS installed. BTW when I purchased the laptop Windows 8.1 were pre-installed. When I installed ubuntu I select to erase windows.

---

### Post by mansonfan78 on 2015-01-02
Since you've reinstalled multiple times I doubt the bootloader was installed improperly.  This is probably either a uefi complication (which I don't really know about) or a video driver failing to load.  Video driver is easy enough to check: just set "nomodeset" in the grub options - [http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)  If that allows you into the system you could then install the proper driver from the "additional drivers" utility.

---

### Post by DuckHook on 2015-01-03
You mention that the installation process is always okay. Does this mean that you get to a LiveDVD/USB session, or do you install immediately from the boot screen?

Try booting to a Live session and then post back results of:```
sudo lspci -vk | grep -iA15 vga
```To install into UEFI computers, follow [this]("https://help.ubuntu.com/community/UEFI") guide. Even though you have nuked Windows, I recommend installing in UEFI mode notwithstanding. If you concur, then ignore the section in the guide dealing with legacy install. If UEFI does not work, then you can try legacy install as an alternative. But post results of *lspci* in any case.

---

### Post by Arlan on 2015-01-03
I get from a LiveUSB session. And also, I set the BIOS in Legacy mode before installing ubuntu. This is the result of lspci:
00:02.0 VGA compatible controller: Intel Corporation ValleyView Gen7 (rev 0e) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 087f
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at 90000000 (32-bit, non-prefetchable) [size=4M]
    Memory at 80000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 2050 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [d0] Power Management version 2
    Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Vendor Specific Information: Len=07 <?>

00:13.0 SATA controller: Intel Corporation ValleyView 6-Port SATA AHCI Controller (rev 0e) (prog-if 01 [AHCI 1.0])
    Subsystem: Acer Incorporated [ALI] Device 087f
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 104
    I/O ports at 2048 [size=8]
    I/O ports at 205c [size=4]


My laptop is now running on recovery mode.

---

### Post by DuckHook on 2015-01-04
Odd. lspci output does not show driver. Are you sure that you typed in the *-k*? You can also try:```
sudo lspci -nnk | grep -iA2 vga
```What we are trying to do is discover which driver the LiveUSB session successfully loaded to enable display, which should show us which driver to install in your regular install.

There is a distinct possibility that we might be barking up the wrong tree here and your problem could be due to something other than the video subsystem. You mention that> Most of the time that I turn on my laptop, ubuntu would not load....so, I gather that at least some of the time, it does load. If so, then it's very unlikely to be a video issue, since a broken video system would be expected to never work at all. Please clarify this. Does it sometimes load?

Do your logs tell you anything? If you can get into recovery mode, this is a further indication that video is not the issue. Therefore, in recovery mode, look through your logs for anything that looks suspicious. I'm afraid there's no painless way to go through logs as a beginner except to start at the beginning and go through them line by line. Logs are located in */var/log* and the important log for your purposes is called *syslog*. There is a handy graphical log viewer in Ubuntu called "System Log" and I encourage all new users to get familiar with it (periodically reviewing your logs is good security practice). You can narrow your search by confining it to the dates and times when you last tried to load Ubuntu unsuccessfully. You are looking for lines that say "error" or "warning", or for the last entries before the system freezes.

Note: you cannot just look at the end of the log. Your successful login to recovery mode will have generated a whole logging session that takes up the last parts of *syslog*, so you must look for earlier entries pertaining to the failed login attempts.

---

### Post by oldfred on 2015-01-04
My now old laptop shows this right after capabilities.

    Kernel driver in use: i915
    Kernel modules: intelfb, i915


And it looks like you have Intel video, but then is driver not working. There is really only one Intel driver, but sometimes it needs boot parameters to specify correct mode.

Try these entries. Add the same way as nomodeset. If you do not get grub menu, with only one system hold shift key from BIOS until grub menu appears, or if UEFI press escape key during UEFI menu.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.

Instead of nomodeset try each of these to see if any works. Be sure if using the example for screen size you use your screen size not the example shown.

      
 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

---

