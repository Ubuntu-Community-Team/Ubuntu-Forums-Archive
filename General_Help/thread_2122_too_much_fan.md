---
title: "too much fan"
date: 2004-10-26
forum: General Help
---

### Post by e.j. on 2004-10-26
anyone know how to make my laptop fan come on less frequently? my tempertature is pretty steady between 62-70C, but the fan is constantly coming on, even though it rarely came on under SUSE. im running a toshiba M30.

thanks,
e.j.

---

### Post by jdong on 2004-10-26
Please issue the following debugging commands and post back the output:
```

lsmod
find /proc/acpi

```

---

### Post by e.j. on 2004-10-26
lsmod

Module                  Size  Used by
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
ds                     17796  2
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  12
af_packet              20872  2
yenta_socket           19328  0
pcmcia_core            63156  2 ds,yenta_socket
ipw2100                90596  0
firmware_class          9728  1 ipw2100
ieee80211              21124  1 ipw2100
ieee80211_crypt         5704  1 ieee80211
eepro100               28300  0
e100                   30208  0
mii                     4864  2 eepro100,e100
ohci1394               32004  0
snd_intel8x0m          18632  3
snd_intel8x0           33068  4
snd_ac97_codec         59268  2 snd_intel8x0m,snd_intel8x0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  6 snd_pcm_oss
snd_pcm                85540  3 snd_intel8x0m,snd_intel8x0,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  3 snd_intel8x0m,snd_intel8x0,snd_pcm
gameport                4736  1 snd_intel8x0
snd_mpu401_uart         7296  1 snd_intel8x0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  14 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  6 snd
ehci_hcd               27780  0
uhci_hcd               29328  0
usbcore               104292  4 ehci_hcd,uhci_hcd
pci_hotplug            30640  0
intel_agp              20512  1
agpgart                31784  2 intel_agp
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
nvidia               4821428  12
parport_pc             32064  0
lp                     10436  0
parport                37320  2 parport_pc,lp
sbp2                   22408  0
ieee1394              100536  2 ohci1394,sbp2
tsdev                   7168  0
joydev                  9536  0
evdev                   9088  1
ide_cd                 38276  0
mousedev               10124  1
psmouse                17800  0
sr_mod                 15780  0
scsi_mod              115148  2 sbp2,sr_mod
cdrom                  35872  2 ide_cd,sr_mod
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
piix                   12576  1
ide_disk               16768  3
ide_core              125272  4 ide_cd,ide_generic,piix,ide_disk
unix                   25904  1025
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

find /proc/acpi
/proc/acpi
/proc/acpi/button
/proc/acpi/button/lid
/proc/acpi/button/lid/LID
/proc/acpi/button/lid/LID/state
/proc/acpi/button/lid/LID/info
/proc/acpi/button/power
/proc/acpi/button/power/PWRF
/proc/acpi/button/power/PWRF/info
/proc/acpi/ac_adapter
/proc/acpi/ac_adapter/ADP1
/proc/acpi/ac_adapter/ADP1/state
/proc/acpi/battery
/proc/acpi/battery/BAT1
/proc/acpi/battery/BAT1/alarm
/proc/acpi/battery/BAT1/state
/proc/acpi/battery/BAT1/info
/proc/acpi/fan
/proc/acpi/fan/FAN
/proc/acpi/fan/FAN/state
/proc/acpi/thermal_zone
/proc/acpi/thermal_zone/THRM
/proc/acpi/thermal_zone/THRM/polling_frequency
/proc/acpi/thermal_zone/THRM/cooling_mode
/proc/acpi/thermal_zone/THRM/trip_points
/proc/acpi/thermal_zone/THRM/temperature
/proc/acpi/thermal_zone/THRM/state
/proc/acpi/processor
/proc/acpi/processor/CPU0
/proc/acpi/processor/CPU0/limit
/proc/acpi/processor/CPU0/throttling
/proc/acpi/processor/CPU0/power
/proc/acpi/processor/CPU0/info
/proc/acpi/wakeup
/proc/acpi/alarm
/proc/acpi/sleep
/proc/acpi/event
/proc/acpi/fadt
/proc/acpi/dsdt
/proc/acpi/info
/proc/acpi/power_resource
/proc/acpi/power_resource/PFAN
/proc/acpi/power_resource/PFAN/state
/proc/acpi/embedded_controller


thanks,
e.j.

---

### Post by Arun on 2004-10-30
I have the same problem too.

I am running IBM Thinkpad T41.

The fan is running continuously even at very low temperatures.
cat /proc/acpi/thermal_zone/THM0/temperature gives me 43 C
But my fan is running.

Any help appreciated..


Arun

---

### Post by jdong on 2004-10-30
heh, if this happens only with Ubuntu, then it's a kernel bug. Please file a bug report for it!

---

### Post by e.j. on 2004-11-02
ok, then.

i posted a bug report to bugzilla. 

you can find the report and the replies (none so far) [here](https://bugzilla.ubuntu.com/show_bug.cgi?id=3147)

---

### Post by e.j. on 2004-11-20
well, after being clueless about this for a long time, i think i've finally sorted it. my fan now seems to be behaving properly after the following steps.

speedstep was not enabled for my centrino laptop by ubuntu at install, so i added the line:

speedstep-centrino 

to /etc/modules

to get it started without rebooting, just go
sudo modprobe speedstep-centrino

also, my battery power sucked on ubuntu, usually i would only get 2 hours. another thing i noticed while trying to figure this fan thing out was that

cat /proc/cpufreq

revealed that i wasn't running cpufreq, meaning my cpu was never throttling down or running in powersave mode when AC power wasn't connected.

all i had to do was install cpufreqd in synaptic.

if you wanted to personalize your settings, you can edit /etc/cpufreqd.conf according to the rules laid out in:

man cpufreqd.conf

someone should make a HOWTO about this for people with centrino laptops or for laptops in general if this issue is widespread.

---

