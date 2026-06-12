---
title: "Suspend not working as intended on Razer Blade Stealth running Xubuntu 16.04"
date: 2016-11-15
forum: General Help
---

### Post by pm5k2 on 2016-11-15
Hi, I've scoured the web for some answers and while some of the one's I've found on google, here or on reddit seemed like they would help, none did.

**[THE ISSUE]**
When I open the power manager application, I have an option of what to do when the Lid is closed. I chose this as "suspend".
The problem occurs when I then close the lid.
Upon closing the laptop goes into suspend, then when I open the lid, I get a black screen. If I then close the lid again and open it RIGHT AWAY,
the laptop wakes up from suspend.

[B][SOME RELEVANT INFO]

[/B]CPU i7-7500u (kaby) Intel HD 620 Graphics
Xubuntu 16.04
Proprietary driver for Intel enabled
I also downloaded and installed the drivers via Intel's "Graphics Update Tool"

uname -a (**I have updated the kernel in hopes it might solve the issue)**
Linux pcname 4.7.0-040700-generic #201608021801 SMP Tue Aug 2 22:03:09 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[B][I TRIED]
[/B]uncommenting** #HandleLidSwitch=suspend **inside of **/etc/systemd/logind.conf** and restarting the logind service
Although it is unclear to me as to whether I should also open the power manager app and switch the lid actions to something other than suspend?

I also tried doing it via acpi:
**lid.sh.post** script inside **/etc/acpi/local (chmod 755 on that script too) **with:
```

#!/bin/bash
if grep -q closed /proc/acpi/button/lid/*/state
then
    /usr/sbin/pm-suspend
fi

It also didn't work.

Interestingly enough if I log into the first virtual console and issue a pm-suspend, then resume and switch to the 7th console (where my GUI was), it woke normally.
Not sure if this helps pin down the problem any more?


```

[B][CONCLUSION]
[/B]I am at my wit's end.. I just want this bastard to suspend and resume normally...
I don't know a whole lot about the suspend process, so if anyone needs me to post more info, please let me know.
I tried to post as much in advance as I can.

---

### Post by irongolem0982 on 2016-11-15
Do you have an external display you can connect it to? if yes then connect it and set the lid to do nothing on close. then close the lid and run the acpi script again and see if it offers different output.

Look around in /sys/class and /sys/devices for anything that looks like a lid switch folder and get back to me (maybe "ls" in those directories and screenie)

make sure you have the latest drivers:

```
sudo update-pciids
sudo apt-get update
```

then look in apps/additional drivers for any chipset or display drivers 

Good Luck!!!

---

### Post by pm5k2 on 2016-11-16
**ls inside /sys/class**

```

ata_device  bdi        devcoredump    dmi             firmware  hwmon        input     mei       nd       phy           ppp           regulator    scsi_disk     spi_master  usbmisc       vtconsole
ata_link    block      devfreq        drm             gpio      i2c-adapter  iommu     mem       net      powercap      printer       rfkill       scsi_generic  thermal     vc            watchdog
ata_port    bluetooth  devfreq-event  drm_dp_aux_dev  graphics  i2c-dev      leds      misc      nvme     power_supply  pwm           rtc          scsi_host     tpm         video4linux   wmi
backlight   bsg        dma            extcon          hidraw    ieee80211    mdio_bus  mmc_host  pci_bus  ppdev         rapidio_port  scsi_device  sound         tty         virtio-ports

```
[B]ls inside /sys/devices

[/B]```

breakpoint  cpu  intel_bts  intel_pt  isa  LNXSYSTM:00  msr  pci0000:00  platform  pnp0  software  system  tracepoint  virtual

```

Running the commands you proposed got me nowhere.

Also here's a paste of my syslog entries which should have suspend in there (i.e. what happens when I close the lid)
[http://pastebin.com/raw/DCjBZMJx](http://pastebin.com/raw/DCjBZMJx)

---

### Post by irongolem0982 on 2016-11-16
do you have a live cd or usb on hand? if you do try suspend in there and see if it behaves the same. 

what is the output of this:
```
cat /proc/acpi/button/lid/LID0/state
```

and you don't get the silly behavior when you just wake it via power button or keypress?


I would really like to help you but this is kind of confusing so we are both learning here :P

---

