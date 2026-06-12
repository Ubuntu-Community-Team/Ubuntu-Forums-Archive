---
title: "Kubuntu screen brightness and wireless problems upgrading to saucy"
date: 2013-10-17
forum: General Help
---

### Post by emperortux on 2013-10-17
Upon upgrading from Kubuntu 13.04 to 13.10, I am no longer able to change the brightness via KDE system settings or the battery monitor widget. Upon editing my /etc/default/grub to ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
```I am able to modify brightness via keyboard controls but not via system settings or the battery monitor widget. 
Brightness appears to be at 100% on startup. /sys/class/backlight contains thinkpad_screen and intel_backlight. xbacklight does not change when given commands such as xbacklight -set 50.
Additionally, I periodically get the error notification "Wireless Interface wlan0 failed to activate - Authorization Supplicant timed out."
I am using a Lenovo Thinkpad T430s with Nvidia Optimus graphics and an Intel wireless card. All settings worked fine before the upgrade.

---

### Post by varunendra on 2013-10-18
> **emperortux said:**
> ..I am able to modify brightness via keyboard controls but not via system settings or the battery monitor widget. 
Brightness appears to be at 100% on startup.

Please run the following script when it is at 100% -
```
for i in `ls /sys/class/backlight/`; do echo -e "\n $i"; cat /sys/class/backlight/$i/{brightness,max_brightness,actual_brightness}; done
```
Then decrease the brightness by one step using key controls, and run it again.

Lastly, decrease it to minimum and run the script for a third time.

Copy-paste the outputs of all three times here in your next post and we may try a few things depending upon the change/no-change that may occur.

And have you also tried the "acpi_osi=" parameter before "acpi_backlight=vendor" ? I'd suggest to try it if you haven't already. Also, "acpi_osi=linux" if the first form doesn't help. Of course run "sudo update-grub" command each time after making a change in the default file, then reboot to see its effect.

**PS:** For the wireless issue, you should start a different thread in Networking & Wireless section of the forums

---

### Post by bapoumba on 2013-10-18
Moved to General Help.

---

