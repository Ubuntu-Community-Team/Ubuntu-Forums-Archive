---
title: "Laptop won't shutdown, won't sleep"
date: 2023-12-20
forum: General Help
---

### Post by ced-vdb on 2023-12-20
My laptop does not want to shut down nor go to sleep. When I go in the menu and press shutdown nothing happens. When I try to close the lid the screen goes black but the pc is very much busy, if I come back to it an hour later it is going to be warm with fans running and I cannot wake it up. I have to hard shut down multiple times a day (pressing the shut down button for 6 seconds)

I tried multiple solutions in the grub file with no avail. I've no clue how to debug this which does not help. I believe this issue is related to my graphic card and its driver.

Here is my system info: [https://termbin.com/nbtw](https://termbin.com/nbtw)
Here is my grub file: 

```


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
GRUB_CMDLINE_LINUX=""

```

---

### Post by MAFoElffen on 2023-12-20
The URL you posted to the report is invalid... Please recheck that with the ~/system-info-link.log. If you check that file, that file should have logged where it uploaded the report to.

Is there a reason why you are using "acpi=force" as a boot parameter?

---

### Post by ced-vdb on 2023-12-20
I edited the link, should be good now.

I believe the "acpi=force" was for trying to fix an issue where the laptop was going to sleep, but upon wake up it would go back to sleep after 10 seconds, non stop.

Note that in the termbin there is this line which might be relevant:

```
BOOT_IMAGE=/boot/vmlinuz-6.5.0-14-generic root=UUID=some-uuid ro quiet splash acpi=force vt.handoff=7


```

---

### Post by MAFoElffen on 2023-12-20
As you are running Mantic, the 6.5 series kernel, and having this issue... First, please go to this bug report and join as affected: [https://bugs.launchpad.net/ubuntu/+bug/2036987](https://bugs.launchpad.net/ubuntu/+bug/2036987)

try to add "noapic" as a boot parameter and test to see what happens...

---

### Post by MAFoElffen on 2023-12-20
Ensure your BIOS is up to date... I see that mentioned, when I look up this issue with this laptop...

Could you please show the output of this within CODE Tags?
```

systemd-inhibit --list --no-pager

```

---

### Post by ced-vdb on 2023-12-20
Thanks, I've added noapic so now my grub line looks is

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force noapic"

```

will try it shortly.

The result of the command is

```

~:$ systemd-inhibit --list --no-pager
WHO                          UID  USER   PID  COMM            WHAT                                                     WHY                                     MODE 
ModemManager                 0    root   1116 ModemManager    sleep                                                    ModemManager needs to reset devices     delay
NetworkManager               0    root   1051 NetworkManager  sleep                                                    NetworkManager needs to turn off netwo&#8230; delay
UPower                       0    root   1841 upowerd         sleep                                                    Pause device polling                    delay
Unattended Upgrades Shutdown 0    root   1388 unattended-upgr shutdown                                                 Stop ongoing upgrades or perform upgra&#8230; delay
GNOME Shell                  1000 cedvdb 2649 gnome-shell     sleep                                                    GNOME needs to lock the screen          delay
cedvdb                       1000 cedvdb 2810 gsd-media-keys  handle-power-key:handle-suspend-key:handle-hibernate-key GNOME handling keypresses               block
cedvdb                       1000 cedvdb 2810 gsd-media-keys  sleep                                                    GNOME handling keypresses               delay
cedvdb                       1000 cedvdb 2811 gsd-power       sleep                                                    GNOME needs to lock the screen          delay

```

---

### Post by ced-vdb on 2023-12-20
After trying the grub line in my above comment, my trackpad was not working.

IE this:

```


[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force noapic"
[/COLOR]

```


Will try the following but at this point i'm just doing trial and error.


```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

```

---

### Post by MAFoElffen on 2023-12-20
I don't see anything in that output that is any different than my own laptop...

I checked with Razer to see if your BIOS version was the latest, and since the report says yours is 1.03... That is reported as the latest BIOS version.

---

