---
title: "Shutdown menu - no Suspend option"
date: 2006-11-23
forum: General Help
---

### Post by r.cannell on 2006-11-23
My shutdown menu does not show a Suspend option, despite the computer supporting it. When using XP, Standby works OK.

Has anyone any advice on how to fix this?

Thanks
Rob

---

### Post by altaaa on 2006-11-23
Go to System -> Administration -> Services.

Scroll down in the list; are [FONT="Courier New"]Power Management (acpid)[/FONT] and [FONT="Courier New"]Power Management (apmd)[/FONT] selected?

---

### Post by r.cannell on 2006-11-24
Neither of these items are even on the services list!   I presume I need to add them - but how is it done?

Rob

---

### Post by altaaa on 2006-11-26
Rob,

It could be that you don't have the acpi packages installed.

To check on this, open up a terminal and type:

```
sudo aptitude search acpi
```

Here's my output when I run this command:

```
sudo aptitude search acpi
i   acpi                            - displays information on ACPI devices      
i   acpi-support                    - a collection of useful events for acpi    
i   acpid                           - Utilities for using ACPI power management 
p   acpidump                        - utilities to dump system's ACPI tables to 
p   acpitool                        - a small, convenient command-line ACPI clie
p   sylpheed-claws-gtk2-acpi-notifi - Laptop's Mail LED control for Sylpheed-Cla
p   wmacpi                          - An ACPI battery monitor for WindowMaker   
p   wmacpiload                      - an app for monitoring CPU temp and battery
p   yacpi                           - ncurses based acpi monitor for text mode
```  

Note the first column, it says "i" when the package is installed.

If your output says you don't have the packages, try something like this:

```
sudo apt-get install acpi acpid acpi-support
```

The packages should start automatically upon restart.

I got this from this thread:
[http://ubuntuforums.org/showthread.php?t=274277](http://ubuntuforums.org/showthread.php?t=274277)

APM is sort of like an "older version" of ACPI. ACPI should be sufficient for stuff like hibernate and suspend.

---

### Post by r.cannell on 2006-11-26
My output is identical to yours except that the line beginning "sylpheed-claws" is not there at all.

However, ACPI is installed. Is there a way to configure it and get suspend working?

---

### Post by xopher on 2006-11-26
Make sure you have **gnome-power-manager** running too.

---

### Post by r.cannell on 2006-11-26
Gnome power manager is running - but when I typed "gnome-power-manager --verbose --no-daemon" one of the last lines said that a non-critical error had been encountered; perhaps I had better look into this.

---

### Post by redleafong on 2006-11-26
This is how I make the "suspend" option show up:

system -> preferences -> power management, click the "action" list and there is one "suspend" item. Select that item and it will ask you to confirm enabling the "suspend" mode. After doing this there is a "suspend" button when I click "log off" button.

Hope this helps...

---

### Post by r.cannell on 2006-11-26
When I try System, Preferences, Power Management, the dialogue box has two tabs - "General" and "Running on AC".  Under "Running on AC" there are two boxes "sleep type when inactive" and "sleep button action" - both are det to Suspend. These are the only references to Suspend that I can find. I do not get an "action " list anywhere that I can find.

---

### Post by altaaa on 2006-11-26
What exactly are you getting when you run gnome-power-manager --verbose --no-daemon?

---

### Post by r.cannell on 2006-11-27
This is the output of gnome power manager --verbose  --no daemons:


[gpm_debug_init] gpm-debug.c:130 (17:28:44):     Verbose debugging enabled
[gpm_hash_new_devices_cache] gpm-hal-monitor.c:630 (17:28:44):   creating cache
[gpm_hal_has_power_management] gpm-hal.c:132 (17:28:44):         Power management type : acpi
[gpm_hash_new_kind_cache] gpm-power.c:1302 (17:28:44):   creating cache
[gpm_hash_new_device_cache] gpm-power.c:1328 (17:28:44):         creating cache
[gpm_hal_is_on_ac] gpm-hal.c:80 (17:28:44):      Couldn't obtain list of ac_adapters
[gpm_power_set_on_ac] gpm-power.c:1018 (17:28:44):       emitting ac-state-changed : 1
[gpm_hal_device_get_bool] gpm-hal.c:381 (17:28:44):      No device with id /org/freedesktop/Hal/devices/acpi_LID
[gpm_brightness_init] gpm-brightness.c:135 (17:28:44):   No devices of capability laptop_panel
[gpm_idle_set_check_cpu] gpm-idle.c:206 (17:28:44):      Setting the CPU load check to 1
[gpm_manager_init] gpm-manager.c:1897 (17:28:44):        creating new tray icon
[gpm_dpms_set_enabled] gpm-dpms-x11.c:422 (17:28:44):    setting DPMS enabled: 1[x11_sync_server_dpms_settings] gpm-dpms-x11.c:117 (17:28:44):   Syncing DPMS settings enabled=1 timeouts=0 0 0
[x11_sync_server_dpms_settings] gpm-dpms-x11.c:117 (17:28:44):   Syncing DPMS settings enabled=1 timeouts=0 0 0
[gpm_brightness_level_save] gpm-brightness.c:363 (17:28:44):     Saving brightness as 100%
[gpm_hal_is_laptop] gpm-hal.c:114 (17:28:44):    This machine is not identified as a laptop.system.formfactor is unknown.
[gpm_hal_enable_power_save] gpm-hal.c:334 (17:28:44):    We are not a laptop, so not even trying
[gpm_screensaver_enable_throttle] gpm-screensaver.c:123 (17:28:44):      setThrottleEnabled : 0
[gpm_idle_set_system_timeout] gpm-idle.c:272 (17:28:44):         Setting system idle timeout: 0
[x11_sync_server_dpms_settings] gpm-dpms-x11.c:117 (17:28:44):   Syncing DPMS settings enabled=1 timeouts=0 0 0
[gpm_manager_init] gpm-manager.c:1952 (17:28:44):        Using per-time notification policy
[gpm_manager_init] gpm-manager.c:1961 (17:28:44):        Using a supressed policy timeout of 5 seconds
*** WARNING ***
[main] gpm-main.c:238 (17:28:44):        Power Manager is already running in this session.
GNOME Power Manager has encountered a non-critical warning.
Consult [http://bugzilla.gnome.org/buglist.cgi?product=gnome-power-manager](http://bugzilla.gnome.org/buglist.cgi?product=gnome-power-manager) for any known issues or a possible fix.
Please file a bug with this complete message if not present


Does this help?

---

### Post by altaaa on 2006-11-27
I would try this one anyway:

```
sudo apt-get install acpi acpid acpi-support
```

and also, open up a terminal and issue the command

```
dmesg
```

and check there if there are any power-management related entries...

Do you have a PC or a laptop?


I'm not sure I can help you with this, as I'm not that good with linux :)

---

### Post by redleafong on 2006-11-27
> **altaaa said:**
> What exactly are you getting when you run gnome-power-manager --verbose --no-daemon?

It should be in the "running on AC" tab. There should be an "Actions" field...

---

### Post by r.cannell on 2006-11-28
altaaa - 
Did the apt-get install and got a message saying that I already have the latest versions.
Did dmesg and got the following references to ACPI:

[17179573.868000] ACPI wakeup devices:
[17179573.868000] SLPB PCI0 HUB0 USB0 USB1 UAR1 UAR2
[17179573.868000]ACPI: (supports S0 S1 S4 S5)

[17179575.328000] ACPI: Fan [FAN] (on)
[17179575.332000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179575.332000] ACPI: Processor [CPU0] (supports 2 throttling states)
[17179575.336000] ACPI: Thermal Zone [THRM] (22 C)

[17179579.472000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 169

[17179579.580000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 177
[17179579.472000] PCI: Setting latency timer of device 0000:00:1f.2 to 64


[17179579.580000] PCI: Setting latency timer of device 0000:00:1f.4 to 64

[17179579.896000] ACPI: PCI Interrupt 0000:02:00.2[C] -> GSI 18 (level, low) -> IRQ 201
[17179579.896000] PCI: Via IRQ fixup for 0000:02:00.2, from 11 to 9

[17179580.000000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 18 (level, low) -> IRQ 201
[17179580.000000] PCI: Via IRQ fixup for 0000:02:02.0, from 11 to 9

[17179596.528000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 17 (level, low) -> IRQ 193

[17179596.528000] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 21 (level, low) -> IRQ 209

[17179608.448000] ACPI: Power Button (FF) [PWRF]
[17179608.448000] ACPI: Power Button (CM) [PWRB]
[17179608.448000] ACPI: Sleep Button (CM) [SLPB]


Does any of this mean anything to you?

What does the dmesg command mean? I saw a couple of entries in there that might help me with a network card problem. Do you know where I can find more information about this?


Oh, the computer is a desktop PC.



redleafong - 

On the "Running on AC" tab there is no "Actions" field. It sounds as though if I could make it appear I would have my problem solved.

---

### Post by altaaa on 2006-11-29
To see what a command is all about, open the reference manual for that command.

In a terminal, type:

```
man dmesg
```

and read the documentation that appears. From this page I read:

```
The program helps users to print out their bootup messages.
```

This works for a whole lot of commands. Just try it out.

I'm sorry but I have run out of options to help you troubleshoot this problem thanks to my limited knowledge of linux...

Oh, one more thing: boot up the ubuntu live cd and see if you have suspend and hibernate options there...

---

### Post by r.cannell on 2006-11-29
OK I'll try those things - as you have probably gathered, I am new to Linux and still learning some of the basics. Thanks for your help.

---

### Post by altaaa on 2006-11-29
No problem -- I am also new with Linux ;)

---

