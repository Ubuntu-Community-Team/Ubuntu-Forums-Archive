---
title: "Kubuntu 17 is slow after expanding root partition. Please Help."
date: 2017-10-03
forum: General Help
---

### Post by surender7790 on 2017-10-03
I am using Kubuntu for several months and root partition got full so I expanded it using instruction on the internet. UsinKubuntutu live USB.
It takes almost 2-3 minutes to boot. Please Help guys. I am new to this community.
Here is my systemd-analyze blame output screenshot:

---

### Post by DuckHook on 2017-10-03
Welcome to the forums, surender7790:

[LIST]
[*]What instructions did you use and from where?
[*]What did you do? (Step by step.)
[*]What was the boot speed before?
[*]What does the boot process tell you? (You can suppress the splash screen by hitting <Shift> or <Esc> during bootup—I turn the splash screen off altogether in GRUB so that I can see the loading process properly)
[*]What do your logs tell you, esp *dmesg*
[/LIST]

---

### Post by surender7790 on 2017-10-04
i used this method. [https://askubuntu.com/a/492066](https://askubuntu.com/a/492066) 
I made a live cd of ubuntu 17 and resized the root partition.
Speed before was barely 20 sec.


```
[FONT=arial]
[/FONT][  OK  ] Started Tell Plymouth To Write Out Runtime Data. 
[  OK  ] Started Load/Save RF Kill Switch Status. 
[  OK  ] Started Show Plymouth Boot Screen. 
[FAILED] Failed to start AppArmor initialization. 
See 'systemctl status apparmor.service' for details. 
[ TIME ] Timed out waiting for device dev-disk-by\x2duuid-d531ccc4\x2dedfb\x2d4fdf\x2d83c7\x2d34e5fd9acfec.device. 
[DEPEND] Dependency failed for /dev/disk/by-uuid/d531ccc4-edfb-4fdf-83c7-34e5fd9acfec. 
[DEPEND] Dependency failed for Swap. 
[  OK  ] Reached target System Initialization. 
        Starting Docker Socket for the API. 
[  OK  ] Started CUPS Scheduler. 
[  OK  ] Listening on UUID daemon activation socket. 
[  OK  ] Started ACPI Events Check. 
[  OK  ] Reached target Paths. 
[  OK  ] Listening on Virtual machine log manager socket. 
[  OK  ] Started Timer to automatically refresh installed snaps. 
[  OK  ] Started Message of the Day. 
[  OK  ] Started Clean PHP session files every 30 mins. 
[  OK  ] Started Daily Cleanup of Temporary Directories. 
[  OK  ] Listening on D-Bus System Message Bus Socket. 
[  OK  ] Listening on CUPS Scheduler. 
[  OK  ] Listening on ACPID Listen Socket. 
[  OK  ] Listening on Virtual machine lock manager socket. 
        Starting Socket activation forsnappy daemon. 
[  OK  ] Listening on Avahi mDNS/DNS-SD Stack Activation Socket. 
[  OK  ] Started Timer to automatically fetch and run repair assertions. 
[  OK  ] Listening on Docker Socket for the API. 
[  OK  ] Listening on Socket activation for snappy daemon. 
[  OK  ] Reached target Sockets. 
[  OK  ] Reached target Basic System. 
        Starting LSB: Chrome Remote Desktop service... 
        Starting Initialize hardware monitoring sensors... 
        Starting Avahi mDNS/DNS-SD Stack... 
[  OK  ] Started Regular background program processing daemon. 
        Starting Restore /etc/resolv.conf if the system crashed before theppp link was shut down... 
[  OK  ] Started Set the CPU Frequency Scaling governor. 
[  OK  ] Started ACPI event daemon. 
        Starting LSB: automatic crash report generation... 
[  OK  ] Started CUPS Scheduler. 
        Starting Detect the available GPUs and deal with any system changes... 
        Starting Modem Manager... 
        Starting LSB: Record successful boot for GRUB... 
        Starting Cleanphp session files... 
        Starting Automatically fetch and run repair assertions... 
        Starting LSB: daemon to balance interrupts for SMP systems... 
[  OK  ] Started D-Bus System Message Bus. 
[  OK  ] Started Avahi mDNS/DNS-SD Stack. 
[  OK  ] Started Make remote CUPS printers available locally. 
        Starting Network Manager... 
        Starting Accounts Service... 
        Starting Login Service... 
        Starting Save/Restore Sound Card State... 
        Starting Snappy daemon... 
        Starting System Logging Service... 
        Starting Thermal Daemon Service... 
        Starting Bluetooth service... 
[  OK  ] Started Restore /etc/resolv.conf if the system crashed before the ppp link was shut down. 
[  OK  ] Started Detect the available GPUs and deal with any system changes. 
[  OK  ] Started Automatically fetch and run repair assertions. 
[  OK  ] Started Initialize hardware monitoring sensors. 
[  OK  ] Started Login Service. 
[  OK  ] Started Save/Restore Sound Card State. 
[  OK  ] Started System Logging Service. 
[  OK  ] Started Thermal Daemon Service. 
[  OK  ] Started Bluetooth service. 
[  OK  ] Reached target Bluetooth. 
        Starting Hostname Service... 
[  OK  ] Started LSB: automatic crash report generation. 
[  OK  ] Started LSB: daemon to balance interrupts for SMP systems. 
        Starting Authorization Manager... 
[  OK  ] Started LSB: Record successful boot for GRUB. 
[  OK  ] Started Hostname Service. 
[  OK  ] Started LSB: Chrome Remote Desktop service. 
[  OK  ] Started Authorization Manager. 
[  OK  ] Started Network Manager. 
[  OK  ] Reached target Network. 
[  OK  ] Started High-performance, schema-free document-oriented database. 
        Starting The Apache HTTP Server... 
        Starting Virtualization daemon... 
        Starting Permit User Sessions... 
[  OK  ] Started Unattended Upgrades Shutdown. 
        Starting MySQL Community Server... 
        Starting Network Name Resolution... 
        Starting Network Manager Wait Online... 
[  OK  ] Started Permit User Sessions. 
        Starting Simple Desktop Display Manager... 
        Starting Set console scheme... 
        Starting Terminate Plymouth Boot Screen... 
[  OK  ] Started Simple Desktop Display Manager.

```

this is my boot.log

---

### Post by QIII on 2017-10-04
surender7790:

Please do not post large images.  Use the attachment functionality (the paper clip in the menu bar) to add images.  Large images can cause problems for those with slow internet connections and may cost extra money for those with data limits.  Please attach your image again using the attachment functionality.

Please use the default font and color.  Enclose terminal output in code tags rather than quote tags.  I have removed your boot.log.  Please replace it with default font and color enclosed in code tags.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

