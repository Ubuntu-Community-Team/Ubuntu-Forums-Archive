---
title: "High disk temperature in ubuntu low in Mageia Linux!"
date: 2013-11-02
forum: General Help
---

### Post by TusharG on 2013-11-02
I'm tryign to use various Ubuntu versions full time on my HP Pavilion dv6-2150us laptop. However the big problem that I have noticed is that the hard disk gets very very hot in Ubuntu. The problem still continues ever since I first used Ubuntu 10.04 to all the way upto Ubuntu 13.10. The same laptop works perfectly fine under Windows 7. I've dual boot. (The air vents are clean no issues there) The disk temperature under Windows 7 remains in range of 44 to 48. Under Ubuntu it varies between 50 to 55! I have tried Ubuntu, xUbuntu, lubuntu and kubuntu. None of the ubuntu versions could cool down my disk drive. I have tried every Ubuntu version on this laptop. I've also tried Fedora 17,18,19, Linux mint 13,14,15 and debian 6 & 7. They all have same problem! 
   After trying few more linux distros I finally found a Linux distro that keeps my laptop dirve really cool... its Mageia 3 !!! At the end of the Mageia 3 installation I saw message saying "thing to configure acpi...." just before the reboot and installation of OS was completed. In Mageia the disk temerature remains around 42 degrees and max it goes upto 48 when accessed disk for too long but it comes down again after sometime. 
   How do I debug what Mageia is doing that Ubuntu is not doing? 
Here are the hardware details of my laptop with lspci output [http://tushargok.blogspot.in/2013/07/laptop-hardware-details-of-hp-pavilion.html](http://tushargok.blogspot.in/2013/07/laptop-hardware-details-of-hp-pavilion.html)
During my search on this topic I found lot more users with similar problem and specially users of Western Digital Disk drive users have more problems. 
There is also a bug in launchpad 394826 which talks about acpi is causing disk drives to be hotter by whooping 10 degrees if power connector is connected and if it is removed the disk temerature comes down I have notied the similar behaviour on my laptop. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/394826](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/394826)

Can someone guide me how I should debug on Mageia 3 to find out what are they doing to keep the disk temperature down?

The Mageia 3 kernel version is 3.8.13.4-desktop586-1.mga3
I'm using hddtemp /dev/sda command to monitor disk temperature.

---

### Post by TusharG on 2013-11-04
Can someone tell me how do I change following parameters while on AC power supply?

DISK_APM_LEVEL_ON_AC="254 254" to "128 128" ?
SATA_LINKPWR_ON_AC=max_performance to min_power ?
PCIE_ASPM_ON_AC=performance to powersave ? 
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor  = ondemand to powersave ?
/sys/class/scsi_host/host0/link_power_management_policy  = max_performance to powersave ?


I've installed 13.10 and have installed TLP as well. However high disk temperature is still noticied! Here are key output of tlp-stat


+++ Configured Settings: /etc/default/tlp
TLP_ENABLE=1
DISK_IDLE_SECS_ON_AC=0
DISK_IDLE_SECS_ON_BAT=2
MAX_LOST_WORK_SECS_ON_AC=15
MAX_LOST_WORK_SECS_ON_BAT=60
SCHED_POWERSAVE_ON_AC=0
SCHED_POWERSAVE_ON_BAT=1
NMI_WATCHDOG=0
DISK_DEVICES="sda sdb"
DISK_APM_LEVEL_ON_AC="254 254"
DISK_APM_LEVEL_ON_BAT="128 128"
SATA_LINKPWR_ON_AC=max_performance
SATA_LINKPWR_ON_BAT=min_power
PCIE_ASPM_ON_AC=performance
PCIE_ASPM_ON_BAT=powersave
RADEON_POWER_PROFILE_ON_AC=high
RADEON_POWER_PROFILE_ON_BAT=low
RADEON_DPM_STATE_ON_AC=performance
RADEON_DPM_STATE_ON_BAT=battery
RADEON_DPM_PERF_LEVEL_ON_AC=auto
RADEON_DPM_PERF_LEVEL_ON_BAT=auto
WIFI_PWR_ON_AC=1
WIFI_PWR_ON_BAT=5
WOL_DISABLE=Y
SOUND_POWER_SAVE=1
SOUND_POWER_SAVE_CONTROLLER=Y
BAY_POWEROFF_ON_BAT=0
BAY_DEVICE="sr0"
RUNTIME_PM_ON_AC=on
RUNTIME_PM_ON_BAT=auto
RUNTIME_PM_ALL=0
USB_AUTOSUSPEND=1
USB_BLACKLIST_WWAN=1
RESTORE_DEVICE_STATE_ON_STARTUP=0


+++ Processor
CPU Model      = Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz

/sys/devices/system/cpu/cpu0/cpufreq/scaling_driver    = acpi-cpufreq
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq  =   933000 [kHz]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq  =  2133000 [kHz]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies = 2133000 1999000 1866000 1733000 1599000 1466000 1333000 1199000 1066000 933000 [kHz]

/sys/devices/system/cpu/cpu1/cpufreq/scaling_driver    = acpi-cpufreq
/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq  =   933000 [kHz]
/sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq  =  2133000 [kHz]
/sys/devices/system/cpu/cpu1/cpufreq/scaling_available_frequencies = 2133000 1999000 1866000 1733000 1599000 1466000 1333000 1199000 1066000 933000 [kHz]

/sys/devices/system/cpu/cpu2/cpufreq/scaling_driver    = acpi-cpufreq
/sys/devices/system/cpu/cpu2/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu2/cpufreq/scaling_min_freq  =   933000 [kHz]
/sys/devices/system/cpu/cpu2/cpufreq/scaling_max_freq  =  2133000 [kHz]
/sys/devices/system/cpu/cpu2/cpufreq/scaling_available_frequencies = 2133000 1999000 1866000 1733000 1599000 1466000 1333000 1199000 1066000 933000 [kHz]

/sys/devices/system/cpu/cpu3/cpufreq/scaling_driver    = acpi-cpufreq
/sys/devices/system/cpu/cpu3/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu3/cpufreq/scaling_min_freq  =   933000 [kHz]
/sys/devices/system/cpu/cpu3/cpufreq/scaling_max_freq  =  2133000 [kHz]
/sys/devices/system/cpu/cpu3/cpufreq/scaling_available_frequencies = 2133000 1999000 1866000 1733000 1599000 1466000 1333000 1199000 1066000 933000 [kHz]
+++ System Info
System         = Hewlett-Packard 049D210000241210000020000 HP Pavilion dv6 Notebook PC
BIOS           = F.1C
Release        = Ubuntu 13.10
Kernel         = 3.11.0-12-generic x86_64
/proc/cmdline  = BOOT_IMAGE=/boot/vmlinuz-3.11.0-12-generic root=UUID=d0151eb5-db34-4b23-85fc-de36515dd7f2 ro quiet splash pcie_aspm=force vt.handoff=7


+++ Temperatures
CPU temp               =    53 [°C]
Fan speed              = (not available)

+++ Storage Devices
/dev/sda:
          Model     = WDC WD3200BEKT-60V5T1                   
          Firmware  = 12.01A12
          APM Level = 254
          Status    = active/idle
          scheduler = deadline

        SMART info:
            4 Start_Stop_Count          =     7347 
            5 Reallocated_Sector_Ct     =        0 
            9 Power_On_Hours            =     7163 [h]
          190 Airflow_Temperature_Cel   =       50 [°C]
          193 Load_Cycle_Count          =    76881 
          194 Temperature_Celsius       =       50    [°C]


+++ SATA Aggressive Link Power Management
/sys/class/scsi_host/host0/link_power_management_policy  = max_performance
/sys/class/scsi_host/host1/link_power_management_policy  = max_performance
/sys/class/scsi_host/host2/link_power_management_policy  = max_performance
/sys/class/scsi_host/host3/link_power_management_policy  = max_performance
/sys/class/scsi_host/host4/link_power_management_policy  = max_performance
/sys/class/scsi_host/host5/link_power_management_policy  = max_performance

+++ PCIe Active State Power Management
/sys/module/pcie_aspm/parameters/policy = performance

---

### Post by TusharG on 2013-11-04
I think I managed to bring down the disk temperature! modified all the values in /etc/default/tlp.
Posting the tlp file here for further reference for other peoples help. 



# ------------------------------------------------------------------------------
# tlp - Parameters for power save

# Hint: some features are disabled by default, remove the leading # to enable them

# Set to 0 to disable/1 to enable TLP                      
TLP_ENABLE=1                                               
                                                            
# Seconds laptop mode has to to wait after the disk goes idle before doing a sync.
# Non-zero value enables, zero disables laptop mode.         
DISK_IDLE_SECS_ON_AC=0                                        
DISK_IDLE_SECS_ON_BAT=2                                        
                                                               
# Dirty page values (timeouts in secs).                          
MAX_LOST_WORK_SECS_ON_AC=15                                         
MAX_LOST_WORK_SECS_ON_BAT=60                                            
                                                                                     
# Select a cpu frequency scaling governor: ondemand/powersave/performance/conservative        
# Important:                                                                                     
# - You *must* disable your distribution's governor settings or conflicts will occur
# - ondemand is sufficient for *almost all* workloads, you should know what you're doing!
CPU_SCALING_GOVERNOR_ON_AC=powersave
CPU_SCALING_GOVERNOR_ON_BAT=powersave

# Set the min/max frequency available for the scaling governor.
# Possible values strongly depend on your cpu. For available frequencies see
# tlp-stat output, Section "+++ Processor".
# Hint: Parameters are disabled by default, remove the leading # to enable them,
#       otherwise kernel default values are used.
CPU_SCALING_MIN_FREQ_ON_AC=933000
CPU_SCALING_MAX_FREQ_ON_AC=1999000
CPU_SCALING_MIN_FREQ_ON_BAT=933000
CPU_SCALING_MAX_FREQ_ON_BAT=1999000

# Set the cpu "turbo boost" feature: 0=disable / 1=allow
# Requires an Intel Core i processor and kernel 3.7 or later.
# Important:
# - This may conflict with your distribution's governor settings
# - A value of 1 does *not* activate boosting, it just allows it
CPU_BOOST_ON_AC=0
CPU_BOOST_ON_BAT=0

# Minimize number of used cpu cores/hyper-threads under light load conditions
SCHED_POWERSAVE_ON_AC=1
SCHED_POWERSAVE_ON_BAT=1

# Kernel NMI Watchdog
# 0=disable (default, saves power) / 1=enable (for kernel debugging only)
NMI_WATCHDOG=0

# Change CPU voltages aka "undervolting" - Kernel with PHC patch required
# Freq:voltage pairs are written to /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
# CAUTION: only use this, if you thoroughly understand what you are doing!
#PHC_CONTROLS="F:V F:V F:V F:V"

# Hard disk devices, separate multiple devices with spaces (default: sda).
# Devices can be specified by disk id too (lookup with: tlp diskid).
DISK_DEVICES="sda sdb"

# Hard disk advanced power management level: 1(max saving)..254(off)
# Levels 1..127 may spin down the disk.
# Separate values for multiple devices with spaces.
DISK_APM_LEVEL_ON_AC="128 128"
DISK_APM_LEVEL_ON_BAT="128 128"

# Hard disk spin down timeout:
# 0:        spin down disabled
# 1..240:   timeouts from 5s to 20min (in units of 5s)
# 241..251: timeouts from 30min to 5.5 hours (in units of 30min)
# (see 'man hdparm' for details)
DISK_SPINDOWN_TIMEOUT_ON_AC="60 60"
DISK_SPINDOWN_TIMEOUT_ON_BAT="60 60"

# Select io scheduler for the disk devices: noop/deadline/cfq (Default: cfq)
# Separate values for multiple devices with spaces.
#DISK_IOSCHED="cfq cfq"

# SATA aggressive link power management (ALPM):
# min_power/medium_power/max_performance
SATA_LINKPWR_ON_AC=min_power
SATA_LINKPWR_ON_BAT=min_power

# PCI Express Active State Power Management (PCIe ASPM):
# default/performance/powersave
# Hint: needs kernel boot option pcie_aspm=force on some machines
PCIE_ASPM_ON_AC=powersave
PCIE_ASPM_ON_BAT=powersave

# Radeon graphics clock speed (profile method): low/mid/high/auto/default
# auto = mid on BAT, high on AC; default = use hardware defaults
# (Kernel >= 2.6.35 only, not with fglrx driver!)
RADEON_POWER_PROFILE_ON_AC=high
RADEON_POWER_PROFILE_ON_BAT=low

# New radeon dynamic power management method (dpm): battery/performance
# (Kernel >= 3.11 only, requires boot option radeon.dpm=1)
RADEON_DPM_STATE_ON_AC=performance
RADEON_DPM_STATE_ON_BAT=battery

# New radeon dpm performance level: auto/low/high (auto is recommended)
RADEON_DPM_PERF_LEVEL_ON_AC=auto
RADEON_DPM_PERF_LEVEL_ON_BAT=auto

# WiFi power saving mode: 1=disable/5=enable
# (Linux 2.6.32 and later, some adapters only!)
WIFI_PWR_ON_AC=1
WIFI_PWR_ON_BAT=5

# Disable wake on lan: Y/N
WOL_DISABLE=Y

# Enable audio power saving for Intel HDA, AC97 devices (timeout in secs).
# A value of 0 disables / >=1 enables power save.
SOUND_POWER_SAVE=1
# Disable controller too (HDA only): Y/N
SOUND_POWER_SAVE_CONTROLLER=Y

# Set to 1 to power off optical drive in UltraBay (ThinkPads only)
# when running on battery. A value of 0 disables this Feature (Default).
# Drive can be powered on again by releasing (and reinserting) the
# eject lever or by pressing the disc eject button on newer models.
# Note: an UltraBay hard disk is never powered off.
BAY_POWEROFF_ON_BAT=0
# Optical drive device to power off (default sr0)
BAY_DEVICE="sr0"

# Runtime Power Management for pci(e) bus devices
# (Kernel >= 2.6.35 only): on=disable/auto=enable
RUNTIME_PM_ON_AC=on
RUNTIME_PM_ON_BAT=auto

# Runtime PM for *all* pci(e) bus devices, expect backlisted ones:
# 0=disable / 1=enable
# Warning: experimental option, could cause system instabilities
RUNTIME_PM_ALL=0

# Exclude pci(e) device adresses the following list from Runtime PM
# (separate with spaces). Use lspci to get the adresses (1st column).
#RUNTIME_PM_BLACKLIST="bb:dd.f 11:22.3 44:55.6"

# Set to 0 to disable/1 to enable usb autosuspend feature
USB_AUTOSUSPEND=1

# Devices from the following list are excluded from usb autosuspend
# (separate with spaces). Use lsusb to get the ids.
# Note: input devices (usbhid) are excluded automatically
#USB_BLACKLIST="1111:2222 3333:4444"

# WWAN devices are excluded from usb autosuspend:
# 0=do not exclude / 1=exclude
# Note: works for ids 05c6:* 0bdb:* 1199:* only
USB_BLACKLIST_WWAN=1

# Set to 1 to disable autosuspend before shutdown/0 to do nothing
# (workaround for usb devices that cause shutdown problems)
#USB_AUTOSUSPEND_DISABLE_ON_SHUTDOWN=1

# Restore radio device state (bluetooth, wifi, wwan) from previous shutdown
# on system startup: 0=disable/1=enable
# Hint: the parameters DEVICES_TO_DISABLE/ENABLE_ON_STARTUP/SHUTDOWN below
#       are ignored when this is enabled!
RESTORE_DEVICE_STATE_ON_STARTUP=0

# Radio devices to disable on startup: bluetooth wifi wwan
#DEVICES_TO_DISABLE_ON_STARTUP="bluetooth wifi wwan"

# Radio devices to enable on startup: bluetooth wifi wwan
#DEVICES_TO_ENABLE_ON_STARTUP="wifi"

# Radio devices to disable on shutdown: bluetooth wifi wwan
# (workaround for devices that are blocking shutdown)
#DEVICES_TO_DISABLE_ON_SHUTDOWN="bluetooth wifi wwan"

# Radio devices to enable on shutdown: bluetooth wifi wwan
# (to prevent other operating systems from missing radios)
#DEVICES_TO_ENABLE_ON_SHUTDOWN="wwan"

# Radio devices to enable when wireless radio switch is turned on:
# bluetooth wifi wwan (Ubuntu + ThinkPad only)
#DEVICES_TO_ENABLE_ON_RADIOSW="wifi wwan"

# Battery charge thresholds (ThinkPad only, tp-smapi or acpi-call kernel module required)
# Charging starts when the remaining capacity falls below the START_CHARGE_TRESH
# value and stops when exceeding the STOP_CHARGE_TRESH value.
# Main battery (values in %)
#START_CHARGE_THRESH_BAT0=75
#STOP_CHARGE_THRESH_BAT0=80
# Ultrabay or slice battery (values in %)
#START_CHARGE_THRESH_BAT1=75
#STOP_CHARGE_THRESH_BAT1=80

# Set to 1 to disable use of tpacpi-bat on Sandy Bridge or newer Thinkpads
# and force usage of tp-smapi instead
#DISABLE_TPACPIBAT=1

# ------------------------------------------------------------------------------
# tlp-rdw - Parameters for the radio device wizard
# Possible devices: bluetooth/wifi/wwan

# Hint: parameters are disabled by default, remove the leading # to enable them

# Radio devices to disable on connect
#DEVICES_TO_DISABLE_ON_LAN_CONNECT="wifi wwan"
#DEVICES_TO_DISABLE_ON_WIFI_CONNECT="wwan"
#DEVICES_TO_DISABLE_ON_WWAN_CONNECT="wifi"

# Radio devices to enable on disconnect
#DEVICES_TO_ENABLE_ON_LAN_DISCONNECT="wifi wwan"
#DEVICES_TO_ENABLE_ON_WIFI_DISCONNECT=""
#DEVICES_TO_ENABLE_ON_WWAN_DISCONNECT=""

# Radio devices to enable/disable when docked
#DEVICES_TO_ENABLE_ON_DOCK=""
#DEVICES_TO_DISABLE_ON_DOCK=""

# Radio devices to enable/disable when undocked
#DEVICES_TO_ENABLE_ON_UNDOCK="wifi"
#DEVICES_TO_DISABLE_ON_UNDOCK=""

tushar@dv6-linux:~$ sudo tl
tload        tlp          tlp-pcilist  tlp-stat     tlp-usblist  
tushar@dv6-linux:~$ sudo tlp start
[sudo] password for tushar: 
TLP started in ac mode.
tushar@dv6-linux:~$ cd /etc/default/
tushar@dv6-linux:/etc/default$ cat tlp 
# ------------------------------------------------------------------------------
# tlp - Parameters for power save

# Hint: some features are disabled by default, remove the leading # to enable them

# Set to 0 to disable/1 to enable TLP
TLP_ENABLE=1

# Seconds laptop mode has to to wait after the disk goes idle before doing a sync.
# Non-zero value enables, zero disables laptop mode.
DISK_IDLE_SECS_ON_AC=0
DISK_IDLE_SECS_ON_BAT=2

# Dirty page values (timeouts in secs).
MAX_LOST_WORK_SECS_ON_AC=15
MAX_LOST_WORK_SECS_ON_BAT=60

# Select a cpu frequency scaling governor: ondemand/powersave/performance/conservative
# Important:
# - You *must* disable your distribution's governor settings or conflicts will occur
# - ondemand is sufficient for *almost all* workloads, you should know what you're doing!
CPU_SCALING_GOVERNOR_ON_AC=powersave
CPU_SCALING_GOVERNOR_ON_BAT=powersave

# Set the min/max frequency available for the scaling governor.
# Possible values strongly depend on your cpu. For available frequencies see
# tlp-stat output, Section "+++ Processor".
# Hint: Parameters are disabled by default, remove the leading # to enable them,
#       otherwise kernel default values are used.
CPU_SCALING_MIN_FREQ_ON_AC=933000
CPU_SCALING_MAX_FREQ_ON_AC=1999000
CPU_SCALING_MIN_FREQ_ON_BAT=933000
CPU_SCALING_MAX_FREQ_ON_BAT=1999000

# Set the cpu "turbo boost" feature: 0=disable / 1=allow
# Requires an Intel Core i processor and kernel 3.7 or later.
# Important:
# - This may conflict with your distribution's governor settings
# - A value of 1 does *not* activate boosting, it just allows it
CPU_BOOST_ON_AC=0
CPU_BOOST_ON_BAT=0

# Minimize number of used cpu cores/hyper-threads under light load conditions
SCHED_POWERSAVE_ON_AC=1
SCHED_POWERSAVE_ON_BAT=1

# Kernel NMI Watchdog
# 0=disable (default, saves power) / 1=enable (for kernel debugging only)
NMI_WATCHDOG=0

# Change CPU voltages aka "undervolting" - Kernel with PHC patch required
# Freq:voltage pairs are written to /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
# CAUTION: only use this, if you thoroughly understand what you are doing!
#PHC_CONTROLS="F:V F:V F:V F:V"

# Hard disk devices, separate multiple devices with spaces (default: sda).
# Devices can be specified by disk id too (lookup with: tlp diskid).
DISK_DEVICES="sda sdb"

# Hard disk advanced power management level: 1(max saving)..254(off)
# Levels 1..127 may spin down the disk.
# Separate values for multiple devices with spaces.
DISK_APM_LEVEL_ON_AC="128 128"
DISK_APM_LEVEL_ON_BAT="128 128"

# Hard disk spin down timeout:
# 0:        spin down disabled
# 1..240:   timeouts from 5s to 20min (in units of 5s)
# 241..251: timeouts from 30min to 5.5 hours (in units of 30min)
# (see 'man hdparm' for details)
DISK_SPINDOWN_TIMEOUT_ON_AC="60 60"
DISK_SPINDOWN_TIMEOUT_ON_BAT="60 60"

# Select io scheduler for the disk devices: noop/deadline/cfq (Default: cfq)
# Separate values for multiple devices with spaces.
#DISK_IOSCHED="cfq cfq"

# SATA aggressive link power management (ALPM):
# min_power/medium_power/max_performance
SATA_LINKPWR_ON_AC=min_power
SATA_LINKPWR_ON_BAT=min_power

# PCI Express Active State Power Management (PCIe ASPM):
# default/performance/powersave
# Hint: needs kernel boot option pcie_aspm=force on some machines
PCIE_ASPM_ON_AC=powersave
PCIE_ASPM_ON_BAT=powersave

# Radeon graphics clock speed (profile method): low/mid/high/auto/default
# auto = mid on BAT, high on AC; default = use hardware defaults
# (Kernel >= 2.6.35 only, not with fglrx driver!)
RADEON_POWER_PROFILE_ON_AC=high
RADEON_POWER_PROFILE_ON_BAT=low

# New radeon dynamic power management method (dpm): battery/performance
# (Kernel >= 3.11 only, requires boot option radeon.dpm=1)
RADEON_DPM_STATE_ON_AC=performance
RADEON_DPM_STATE_ON_BAT=battery

# New radeon dpm performance level: auto/low/high (auto is recommended)
RADEON_DPM_PERF_LEVEL_ON_AC=auto
RADEON_DPM_PERF_LEVEL_ON_BAT=auto

# WiFi power saving mode: 1=disable/5=enable
# (Linux 2.6.32 and later, some adapters only!)
WIFI_PWR_ON_AC=1
WIFI_PWR_ON_BAT=5

# Disable wake on lan: Y/N
WOL_DISABLE=Y

# Enable audio power saving for Intel HDA, AC97 devices (timeout in secs).
# A value of 0 disables / >=1 enables power save.
SOUND_POWER_SAVE=1
# Disable controller too (HDA only): Y/N
SOUND_POWER_SAVE_CONTROLLER=Y

# Set to 1 to power off optical drive in UltraBay (ThinkPads only)
# when running on battery. A value of 0 disables this Feature (Default).
# Drive can be powered on again by releasing (and reinserting) the
# eject lever or by pressing the disc eject button on newer models.
# Note: an UltraBay hard disk is never powered off.
BAY_POWEROFF_ON_BAT=0
# Optical drive device to power off (default sr0)
BAY_DEVICE="sr0"

# Runtime Power Management for pci(e) bus devices
# (Kernel >= 2.6.35 only): on=disable/auto=enable
RUNTIME_PM_ON_AC=on
RUNTIME_PM_ON_BAT=auto

# Runtime PM for *all* pci(e) bus devices, expect backlisted ones:
# 0=disable / 1=enable
# Warning: experimental option, could cause system instabilities
RUNTIME_PM_ALL=0

# Exclude pci(e) device adresses the following list from Runtime PM
# (separate with spaces). Use lspci to get the adresses (1st column).
#RUNTIME_PM_BLACKLIST="bb:dd.f 11:22.3 44:55.6"

# Set to 0 to disable/1 to enable usb autosuspend feature
USB_AUTOSUSPEND=1

# Devices from the following list are excluded from usb autosuspend
# (separate with spaces). Use lsusb to get the ids.
# Note: input devices (usbhid) are excluded automatically
#USB_BLACKLIST="1111:2222 3333:4444"

# WWAN devices are excluded from usb autosuspend:
# 0=do not exclude / 1=exclude
# Note: works for ids 05c6:* 0bdb:* 1199:* only
USB_BLACKLIST_WWAN=1

# Set to 1 to disable autosuspend before shutdown/0 to do nothing
# (workaround for usb devices that cause shutdown problems)
#USB_AUTOSUSPEND_DISABLE_ON_SHUTDOWN=1

# Restore radio device state (bluetooth, wifi, wwan) from previous shutdown
# on system startup: 0=disable/1=enable
# Hint: the parameters DEVICES_TO_DISABLE/ENABLE_ON_STARTUP/SHUTDOWN below
#       are ignored when this is enabled!
RESTORE_DEVICE_STATE_ON_STARTUP=0

# Radio devices to disable on startup: bluetooth wifi wwan
#DEVICES_TO_DISABLE_ON_STARTUP="bluetooth wifi wwan"

# Radio devices to enable on startup: bluetooth wifi wwan
#DEVICES_TO_ENABLE_ON_STARTUP="wifi"

# Radio devices to disable on shutdown: bluetooth wifi wwan
# (workaround for devices that are blocking shutdown)
#DEVICES_TO_DISABLE_ON_SHUTDOWN="bluetooth wifi wwan"

# Radio devices to enable on shutdown: bluetooth wifi wwan
# (to prevent other operating systems from missing radios)
#DEVICES_TO_ENABLE_ON_SHUTDOWN="wwan"

# Radio devices to enable when wireless radio switch is turned on:
# bluetooth wifi wwan (Ubuntu + ThinkPad only)
#DEVICES_TO_ENABLE_ON_RADIOSW="wifi wwan"

# Battery charge thresholds (ThinkPad only, tp-smapi or acpi-call kernel module required)
# Charging starts when the remaining capacity falls below the START_CHARGE_TRESH
# value and stops when exceeding the STOP_CHARGE_TRESH value.
# Main battery (values in %)
#START_CHARGE_THRESH_BAT0=75
#STOP_CHARGE_THRESH_BAT0=80
# Ultrabay or slice battery (values in %)
#START_CHARGE_THRESH_BAT1=75
#STOP_CHARGE_THRESH_BAT1=80

# Set to 1 to disable use of tpacpi-bat on Sandy Bridge or newer Thinkpads
# and force usage of tp-smapi instead
#DISABLE_TPACPIBAT=1

# ------------------------------------------------------------------------------
# tlp-rdw - Parameters for the radio device wizard
# Possible devices: bluetooth/wifi/wwan

# Hint: parameters are disabled by default, remove the leading # to enable them

# Radio devices to disable on connect
#DEVICES_TO_DISABLE_ON_LAN_CONNECT="wifi wwan"
#DEVICES_TO_DISABLE_ON_WIFI_CONNECT="wwan"
#DEVICES_TO_DISABLE_ON_WWAN_CONNECT="wifi"

# Radio devices to enable on disconnect
#DEVICES_TO_ENABLE_ON_LAN_DISCONNECT="wifi wwan"
#DEVICES_TO_ENABLE_ON_WIFI_DISCONNECT=""
#DEVICES_TO_ENABLE_ON_WWAN_DISCONNECT=""

# Radio devices to enable/disable when docked
#DEVICES_TO_ENABLE_ON_DOCK=""
#DEVICES_TO_DISABLE_ON_DOCK=""

# Radio devices to enable/disable when undocked
#DEVICES_TO_ENABLE_ON_UNDOCK="wifi"
#DEVICES_TO_DISABLE_ON_UNDOCK=""

---

