---
title: "Laptop not suspending when lid is closed - Xubuntu 13.10"
date: 2014-01-05
forum: General Help
---

### Post by victorcl2 on 2014-01-05
I installed Xubuntu 13.10 on an old Sony Vaio laptop and so far it has been running great. There were a bunch of hardware problems I had to fix; however, I cannot seem to figure out how to get the system to suspend when I close my laptop lid. I read a bunch of threads on similar issues but none of them fixed the problem. I even updated the kernel to 3.12.6 hoping it would fix it but it did not.
There were a lot of threads talking about acpi events and how the lid files (lid.sh, lidbtn.sh, etc) had to be modified. However, /etc/acpi/events/lid, /etc/acpi/lid.sh, and any files related to the lid does not exist in my system. I am not sure if this is relevant because I read somewhere that acpid is not really used for power management in Ubuntu anymore, but uses pm-utils.
So far I have been clicking the suspend icon or use pm-suspend before closing my lid. Having it automatically suspend upon closing the lid will be nice.

---

### Post by grier-devon on 2014-01-06
Have you tried sudo vim /etc/systemd/logind.conf  and remove the # before "HandleLidSwitch=suspend"

---

### Post by zemega on 2014-01-06
That is some of the qualm I had with Xubuntu. Which leads me to install Ubuntu first, then instal xubuntu-desktop.

---

### Post by victorcl2 on 2014-01-06
Yeah, I did try removing the # before "HandleLidSwitch=suspend" and it did not fix the problem. At the end, I might just install Ubuntu and see if it has the same problem.

---

### Post by Toz on 2014-01-06
Is the lid being recognized?
```
dmesg | grep -i lid
```

Have you tried changing the "When laptop lid is closed" setting to "Suspend" in "Settings Manager -> Power Manager -> [ On A/C | On Battery ]? 
Note: You may need to do this in conjunction with editing /etc/systemd/logind.conf but changing:
> #HandleLidSwitch=suspend
...to read:
```
HandleLidSwitch=ignore
```
...(to allow xfce4-power-manager to handle lid events).

---

### Post by victorcl2 on 2014-01-06
Yeah, the lid seems to be recognized; I got this:

[    1.441220] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.443105] ACPI: Lid Switch [LID0]
[    8.128473] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8

And the setting for the Power Manager was the first thing I tried. Also, changing to HandelLidSwitch=ignore did not work either. I think I have tried all possible suggestions I have found from searches.

---

### Post by Toz on 2014-01-06
Do lid events get recognized? You should have a state file in /proc/acpi/button/lid/LID0 that shows the state of the lid. From a terminal window, run:
```
while true; do cat /proc/acpi/button/lid/LID0/state ; sleep 3; done
```
...then close the lid, wait, and re-open the lid. The results of the script should show the lid state change from open to closed to open again.

My run (note: my lid is called LID, your is called LID0):
> $ while true; do cat /proc/acpi/button/lid/LID/state ; sleep 3; done
state:      open
state:      open
state:      closed
state:      open
state:      open


---

### Post by victorcl2 on 2014-01-06
Yes. It recognizes.

The results for LID0 shows:

state:      open
state:      closed
state:      open
state:      open

So the lid events does get recognized and changes from open to closed.

---

### Post by Toz on 2014-01-06
Interesting. Just to confirm, did you create any files in /etc/acpi?


Can you try running xfce4-power-manager in debug mode? First, you need to kill the existing process:
```
killall xfce4-power-manager
```
...then start it up in debug mode:
```
xfce4-power-manager --debug
```
...then close, wait and re-open the lid. Post back the debug statements that are generated relating to lid actions.

To reset things to normal, Ctrl+C to kill power-manager in debug mode and:
```
xfce4-power-manager &
```
...to restart in daemon mode.


And one more thing:
```
apt-cache policy pm-utils
```
...is it installed?

---

### Post by victorcl2 on 2014-01-06
Thanks Toz for all your help.

I did not create any files in /etc/acpi. Everything listed is from the default install:

```
-rwxr-xr-x 1 root root  391 Apr 30  2013 asus-keyboard-backlight.sh
-rwxr-xr-x 1 root root  180 Apr 30  2013 asus-wireless.sh
drwxr-xr-x 2 root root 4096 Jan  5 17:35 events
-rwxr-xr-x 1 root root  608 Apr 30  2013 ibm-wireless.sh
-rwxr-xr-x 1 root root 2176 Aug 16 07:54 powerbtn.sh
-rwxr-xr-x 1 root root  455 Apr 30  2013 tosh-wireless.sh
-rwxr-xr-x 1 root root  238 Apr 30  2013 undock.sh
```


I ran the debug mode; however, there does not seem to be any statements related to the lid. even when I closed the lid.

```
$ xfce4-power-manager --debug
TRACE[xfpm-main.c:203] xfpm_start(): Starting the power manager
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for general-notification
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for lock-screen-suspend-hibernate
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for power-save-on-battery
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for enable-cpu-freq-control
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for critical-power-level
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for show-brightness-popup
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for change-brightness-on-key-events
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for show-tray-icon
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for hibernate-button-action
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for sleep-button-action
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for brightness-level-on-ac
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for brightness-level-on-battery
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for dpms-enabled
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for dpms-on-ac-sleep
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for dpms-on-ac-off
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for dpms-on-battery-sleep
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for dpms-on-battery-off
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for dpms-sleep-mode
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for inactivity-on-battery
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for inactivity-sleep-mode
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for brightness-on-ac
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for brightness-on-battery
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for spin-down-on-ac
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for spin-down-on-battery
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for spin-down-on-ac-timeout
TRACE[xfpm-xfconf.c:156] xfpm_xfconf_load(): Using default configuration for spin-down-on-battery-timeout

(xfce4-power-manager:1928): xfce4-power-manager-WARNING **: Unable to create proxy for 'org.freedesktop.ConsoleKit'
TRACE[xfpm-power.c:1055] xfpm_power_get_power_devices(): Power device detected at : /org/freedesktop/UPower/devices/line_power_ACAD
TRACE[xfpm-power.c:1002] xfpm_power_add_device():  device added: ((XfpmDeviceType) XFPM_DEVICE_TYPE_LINE_POWER)
TRACE[xfpm-power.c:1055] xfpm_power_get_power_devices(): Power device detected at : /org/freedesktop/UPower/devices/battery_BAT1
TRACE[xfpm-power.c:1002] xfpm_power_add_device():  device added: ((XfpmDeviceType) XFPM_DEVICE_TYPE_BATTERY)
TRACE[xfpm-power.c:1013] xfpm_power_add_device(): Battery device detected at : /org/freedesktop/UPower/devices/battery_BAT1: ((XfpmDeviceType) XFPM_DEVICE_TYPE_BATTERY)
TRACE[xfpm-button.c:179] xfpm_button_xevent_key(): Grabbed key 124 : ((XfpmButtonKey) BUTTON_POWER_OFF)

(xfce4-power-manager:1928): xfce4-power-manager-WARNING **: could not map keysym 1008ffa8 to keycode

TRACE[xfpm-button.c:179] xfpm_button_xevent_key(): Grabbed key 213 : ((XfpmButtonKey) BUTTON_HIBERNATE)
TRACE[xfpm-button.c:179] xfpm_button_xevent_key(): Grabbed key 150 : ((XfpmButtonKey) BUTTON_SLEEP)
TRACE[xfpm-button.c:179] xfpm_button_xevent_key(): Grabbed key 233 : ((XfpmButtonKey) BUTTON_MON_BRIGHTNESS_UP)
TRACE[xfpm-button.c:179] xfpm_button_xevent_key(): Grabbed key 232 : ((XfpmButtonKey) BUTTON_MON_BRIGHTNESS_DOWN)
TRACE[xfpm-button.c:179] xfpm_button_xevent_key(): Grabbed key 244 : ((XfpmButtonKey) BUTTON_BATTERY)
TRACE[xfpm-battery.c:150] xfpm_battery_refresh_visible(): visible=TRUE: ((XfpmShowIcon) SHOW_ICON_WHEN_BATTERY_PRESENT)
TRACE[xfpm-battery.c:286] xfpm_battery_refresh_icon(): Battery state 1
TRACE[xfpm-power.c:1149] xfpm_power_refresh_adaptor_visible(): Tray icon configuration: : ((XfpmShowIcon) SHOW_ICON_WHEN_BATTERY_PRESENT)
TRACE[xfpm-power.c:1113] xfpm_power_hide_adapter_icon(): Hide adaptor icon
TRACE[xfpm-polkit.c:368] xfpm_polkit_init_data(): Using unix session polkit subject
TRACE[xfpm-polkit.c:455] xfpm_polkit_check_auth_intern(): Action=org.freedesktop.upower.suspend is authorized=TRUE
TRACE[xfpm-polkit.c:455] xfpm_polkit_check_auth_intern(): Action=org.freedesktop.upower.hibernate is authorized=FALSE
TRACE[xfpm-power.c:1149] xfpm_power_refresh_adaptor_visible(): Tray icon configuration: : ((XfpmShowIcon) SHOW_ICON_WHEN_BATTERY_PRESENT)
TRACE[xfpm-power.c:1113] xfpm_power_hide_adapter_icon(): Hide adaptor icon

(xfce4-power-manager:1928): xfce4-power-manager-WARNING **: 'CheckAuthorization' failed with Action org.freedesktop.udisks.drive-set-spindown is not registered
TRACE[xfpm-polkit.c:455] xfpm_polkit_check_auth_intern(): Action=org.freedesktop.udisks.drive-set-spindown is authorized=FALSE
TRACE[xfpm-disks.c:170] xfpm_disks_get_is_auth_to_spin(): Is auth to spin down disks : 0
TRACE[xfpm-backlight.c:232] xfpm_backlight_brightness_on_ac_settings_changed(): Alarm on ac timeout changed 9
TRACE[xfpm-backlight.c:253] xfpm_backlight_brightness_on_battery_settings_changed(): Alarm on battery timeout changed 120
TRACE[xfpm-battery.c:286] xfpm_battery_refresh_icon(): Battery state 1
TRACE[xfpm-power.c:1149] xfpm_power_refresh_adaptor_visible(): Tray icon configuration: : ((XfpmShowIcon) SHOW_ICON_WHEN_BATTERY_PRESENT)
TRACE[xfpm-power.c:1113] xfpm_power_hide_adapter_icon(): Hide adaptor icon
TRACE[xfpm-battery.c:286] xfpm_battery_refresh_icon(): Battery state 1
TRACE[xfpm-power.c:1149] xfpm_power_refresh_adaptor_visible(): Tray icon configuration: : ((XfpmShowIcon) SHOW_ICON_WHEN_BATTERY_PRESENT)
TRACE[xfpm-power.c:1113] xfpm_power_hide_adapter_icon(): Hide adaptor icon
TRACE[xfpm-polkit.c:238] xfpm_polkit_free_data(): Destroying Polkit data
TRACE[xfpm-battery.c:286] xfpm_battery_refresh_icon(): Battery state 1
TRACE[xfpm-power.c:1149] xfpm_power_refresh_adaptor_visible(): Tray icon configuration: : ((XfpmShowIcon) SHOW_ICON_WHEN_BATTERY_PRESENT)
TRACE[xfpm-power.c:1113] xfpm_power_hide_adapter_icon(): Hide adaptor icon
TRACE[xfpm-battery.c:286] xfpm_battery_refresh_icon(): Battery state 1
```


And here is what I got from "apt-cache policy pm-utils":

```
$ apt-cache policy pm-utils
pm-utils:
  Installed: 1.4.1-12ubuntu1
  Candidate: 1.4.1-12ubuntu1
  Version table:
 *** 1.4.1-12ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by Toz on 2014-01-06
*I added code tags to your post so that its easier to read. To add code tags, put your code inbetween **[noparse]```
 
```[/noparse]** tags.*

xfce4-power-manager is not picking up your lid actions. For comparisons sake, here is my debug log that shows the lid actions:
```
TRACE[xfpm-manager.c:317] xfpm_manager_lid_changed_cb(): LID close event: ((XfpmLidTriggerAction) LID_TRIGGER_SUSPEND)
TRACE[xfpm-power.c:1190] xfpm_power_refresh_adaptor_visible(): Tray icon configuration: : ((XfpmShowIcon) SHOW_ICON_WHEN_BATTERY_PRESENT)
TRACE[xfpm-power.c:1155] xfpm_power_hide_adapter_icon(): Hide adaptor icon
TRACE[xfpm-manager.c:344] xfpm_manager_lid_changed_cb(): LID opened: ((XfpmLidTriggerAction) LID_TRIGGER_SUSPEND)
```

What is the exact model of your Sony laptop?
What version of xfce4-power-manager do you have:
```
xfce4-power-manager -V
```
Can you post back the complete contents of /etc/systemd/logind.conf?

---

### Post by victorcl2 on 2014-01-06
This is a Sony Vaio VGN-SZ74L/B, It is an old laptop from Korea that was given to me. It original came with Windows Vista but even Windows drivers no longer exist for this model. Sony is no longer providing support for this model, which is why I installed Xubuntu. :)

Here is the output for xfce4-power-manager
```

$ xfce4-power-manager -V

Xfce Power Manager 1.2.0

Part of the Xfce Goodies Project
http://goodies.xfce.org

Licensed under the GNU GPL.

```

And the contents of logind.conf
```

$ cat /etc/systemd/logind.conf
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
#
# See logind.conf(5) for details

[Login]
#NAutoVTs=6
#ReserveVT=6
#KillUserProcesses=no
#KillOnlyUsers=
#KillExcludeUsers=root
#Controllers=
#ResetControllers=cpu
#InhibitDelayMaxSec=5
#HandlePowerKey=poweroff
#HandleSuspendKey=suspend
#HandleHibernateKey=hibernate
HandleLidSwitch=ignore
#PowerKeyIgnoreInhibited=no
#SuspendKeyIgnoreInhibited=no
#HibernateKeyIgnoreInhibited=no
#LidSwitchIgnoreInhibited=yes
#IdleAction=ignore
#IdleActionSec=30min

```

Btw, I removed the optical drive and installed a second hard drive in an optical caddy. But I do not think a second hard drive would prevent the system from suspending.

---

### Post by Toz on 2014-01-06
For some reason, xfce4-power-manager isn't recognizing your lid actions. I've found this [other similar bug report]("https://bugzilla.xfce.org/show_bug.cgi?id=9704"), but there doesn't appear to be an action on it. 

Can I have a look at your complete dmesg log file?
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

And finally, are there any Lid settings in your bios?

---

### Post by victorcl2 on 2014-01-07
Here is the dmesg log with the link:

```

$ pastebinit /var/log/dmesg
[http://paste.ubuntu.com/6707399/](http://paste.ubuntu.com/6707399/)

```

There are no Lid settings in the bios. Thanks to Sony, the bios is so restricted that the only options available are the ones to change the boot order.

---

### Post by Toz on 2014-01-07
Try running:
```
acpi_listen
```
...in a terminal window, then closing the lid and reopening it. Post back the messages that are displayed.

Is acpid installed?
```
apt-cache policy acpid
```

---

### Post by victorcl2 on 2014-01-07
acpi_listen does not display any message when I close/open the lid. Even the when I press the power button nothing happens.

A message displays when I press the S1 button: (this Sony Vaio has a S1 and S2 button which are programmable buttons)
```

acpi_listen
button/prog1 PROG1 00000080 00000000 K

```
I am guessing acpi_listen is not working properly?

acpid is installed.
```

$ apt-cache policy acpid
acpid:
  Installed: 1:2.0.18-1ubuntu2
  Candidate: 1:2.0.18-1ubuntu2
  Version table:
 *** 1:2.0.18-1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Toz on 2014-01-07
It appears that your lid event is not being recognized at the kernel level, not the power-manager-level. 

Can we try some kernel parameters to see if we can get acpi to recognize them. Follow the "Temporarily Add a Kernel Boot Parameter for Testing" instructions at the [Kernel Boot Parameters Wiki page]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") and test out the following paramaters:

[B]acpi_ois=Linux
acpi_osi=[/B]

Test them out one at a time and post back the results of:
```
cat /proc/cmdline
```
...as well as whether:
```
acpi_listen
```
...recognizes the lid event.

If this doesn't work, you may want to see if a bios update is available.

EDIT: Before the bios update, also try unloading the sony-laptop module:
```
sudo modprobe -r sony-laptop
```
...and test with acpi_listen again (in case the module is interfering).

---

### Post by victorcl2 on 2014-01-07
I tested out the parameters but I am not sure what the results is suppose to show. This is what I got.

**acpi_osi=Linux**
```

$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.12.6-031206-generic root=UUID=d3c31e52-3e37-4c4b-97dd-d94f7fa7c41d ro quiet splash acpi_osi=Linux

```

**acpi_osi=**
```

$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.12.6-031206-generic root=UUID=d3c31e52-3e37-4c4b-97dd-d94f7fa7c41d ro quiet splash acpi_osi=

```

acpi_listen did not recognize the lid, and unloading the sony-laptop module did not fix it either.

The laptop might be the problem. Also, it already has the latest bios (from 2008) installed.

I'm going to test out Ubuntu 13.10 to see if lid suspend works.

---

### Post by victorcl2 on 2014-01-08
Toz, I installed Ubuntu 13.10, but I had major display issues. Ubuntu loads with a scrambled display making it unsuable, another thing to troubleshoot. In the meantime, I have Mint 16 Cinnamon up and running; I wanted to test out a non-Xfce distro. However, the lid suspend problem also exist in Mint which got me really thinking if it is the laptop. I will continue to investigate and experiment on this problem.

---

### Post by zemega on 2014-01-08
An odd answer, probably the switch to inform the lid close event is not functioning? Have you taken a look at your BIOS or UEFI as well?

---

