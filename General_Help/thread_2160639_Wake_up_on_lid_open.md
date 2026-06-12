---
title: "Wake up on lid open"
date: 2013-07-07
forum: General Help
---

### Post by DeathByDenim on 2013-07-07
I'm trying to figure out how to make my laptop wake up by opening the lid. When I close the lid, the laptop goes to sleep, which is fine, but when I open the lid again, it will remain asleep and I have to press the power button or any other key on the keyboard. I found plenty of references on how to prevent a laptop from waking up, but only one on how to set it up [here]("http://dan.bodar.com/2013/01/13/samsung-series-9-np900x3c-a05uk-ubuntulinux-wake-up-when-i-open-the-lid/"). Basically, it says to find out what the lid event is called using the command:
```
ls /proc/acpi/button/lid/
```
, which is my case says it's just called "LID". Typing
```
cat /proc/acpi/button/lid/LID/state
```
does indeed say: "state:      open". So far so good. Then I'm supposed to type
```
echo LID > /proc/acpi/wakeup
```
as root, which works in the sense that no error is given. However, typing
```
cat /proc/acpi/wakeup
```
produces
```
Device  S-state   Status   Sysfs node
P0P1      S4    *disabled
GLAN      S4    *disabled
EHC1      S3    *enabled   pci:0000:00:1d.0
EHC2      S3    *enabled   pci:0000:00:1a.0
XHC       S3    *enabled   pci:0000:00:14.0
HDEF      S0    *disabled  pci:0000:00:1b.0
RP01      S4    *disabled  pci:0000:00:1c.0
PXSX      S4    *disabled  pci:0000:07:00.0
RP02      S4    *disabled  pci:0000:00:1c.1
PXSX      S4    *disabled  pci:0000:0d:00.0
RP03      S4    *disabled
PXSX      S4    *disabled
RP04      S4    *disabled
PXSX      S4    *disabled
RP05      S4    *disabled
PXSX      S4    *disabled
RP06      S4    *disabled  pci:0000:00:1c.5
PXSX      S4    *disabled  pci:0000:0e:00.0
RP07      S4    *disabled
PXSX      S4    *disabled
RP08      S4    *disabled
PXSX      S4    *disabled
PEG0      S4    *disabled  pci:0000:00:01.0
PEGP      S4    *disabled  pci:0000:01:00.0
PEG1      S4    *disabled
PEG2      S4    *disabled
PEG3      S4    *disabled
```
I closed the lid to make the laptop sleep again, but after opening the lid, the laptop will remain asleep until I press a key on the keyboard. I also looked at the energy savings menu in the system settings, but there are only options for making the laptop sleep, not wake up. Is this simply something that is not supported on my hardware?
I'm using Kubuntu 13.04 on an Acer Aspire V3 771G-9633.

---

