---
title: "Can I stop the keyboard from waking my computer from suspend?"
date: 2017-11-23
forum: General Help
---

### Post by blackbird34 on 2017-11-23
Hi, 

I carry my laptop around in a backpack a lot, and it's a Lenovo Z50-70 with a plastic body, I think the screen flexes (there's lots of stuff pressing on t in a tightly packed bag), presses down on the keyboard and wakes my computer up when it's inside the bag. This makes it turn on and heat up very fast to 60-70°C or more, with the fans running like crazy. 

How can I disable the keyboard from resuming the computer, and only resume with the power button? 

When I run ```
$ cat /proc/acpi/wakeup 
``` I get the following result: 

```
nad@Incendies:~$ cat /proc/acpi/wakeup  
Device  S-state   Status   Sysfs node
P0P1      S4    *disabled
UAR1      S3    *disabled
EHC1      S3    *enabled   pci:0000:00:1d.0
XHC       S3    *enabled   pci:0000:00:14.0
HDEF      S4    *disabled  pci:0000:00:1b.0
TPD4      S4    *disabled
TPD7      S0    *disabled
TPD8      S0    *disabled
RP01      S4    *disabled
PXSX      S4    *disabled
RP02      S4    *disabled
PXSX      S4    *disabled
RP03      S4    *disabled  pci:0000:00:1c.0
PXSX      S4    *disabled  pci:0000:01:00.0
RP04      S4    *disabled  pci:0000:00:1c.3
PXSX      S4    *disabled  pci:0000:02:00.0
RP05      S4    *disabled
RP06      S4    *disabled
PXSX      S4    *disabled
RP07      S4    *disabled
PXSX      S4    *disabled
RP08      S4    *disabled
PXSX      S4    *disabled
PEG0      S4    *disabled
PEGP      S4    *disabled
PEG1      S4    *disabled
PEG2      S4    *disabled
LID0      S3    *enabled   platform:PNP0C0D:00
PWRB      S4    *enabled   platform:PNP0C0C:00

```

I read several AskUbuntu posts about this and googled for a while. People suggested toggling the different components that were able to wake the computer up. LID0 and PWRB seem to be explicit enough (wake when the lid opens / when the power button is pressed) so I didn't bother toggling them. I tried disabling EHC1, suspending, resuming with the keyboard and it worked anyway. I tried disabling XHC, suspending, resuming with the keyboard and it worked too. I think I read that these were the internal USB interfaces. 

Was I using bad information here? How can I stop my keyboard from waking the computer?

---

### Post by irv on 2017-11-29
One thing you can do is set the Automatic Suspend to 15 minutes. So when the computer comes out of suspending it will be for a shorter time. I know it not the answer, but it will help from heating up. My laptop boot so fast with a SSD I just got in the habit of shutting it down when I am done with it.

---

### Post by blackbird34 on 2017-11-30
Thanks for your answer! Yeah I suppose I should just set a really short automatic suspend time when it's on battery power. I usually plug it in the wall. 

It also has an SSD but I prefer having my work instantly appear instead of counting on KDE Neon to find all my windows (sometimes it forgets stuff, but at least it tries, its better than vanilla Unity in that respect). If I have five or ten libreoffice documents open (class teaching plus research) it could take a while to track them all down.

---

