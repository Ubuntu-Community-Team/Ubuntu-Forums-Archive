---
title: "Can't shut down (power off) netbook. System always reboots instead"
date: 2016-09-04
forum: General Help
---

### Post by Katzwinkel on 2016-09-04
Hi, I recently updated my netbook OS von xubuntu 14.04 to 16.04 LTS via  a clean reinstall. My netbook is a Medion (=Lenovo) Akoya E1228 with an Intel Atom processor (Yeah I know, they suck, but aside from my problem in the title, everything works just fine) and 2 GB of RAM. 

I used to run 32bit xubuntu, but now switched to the 64 bit version because the processor explicitely supports it (and several tools are not supported for 32bit versions anymore). 

Everything works just fine, but now I can't shutdown the netbook anymore. Everytime I select "shut down" from the Log-Out menu or when I short press the power button (Associated with "shut down" in the power settings) the system just reboots. Basically the only option to turn of my netbook is to long press the power button (force power off) or rip out the battery.

When searching for this problem in diverse forums, I found it is rather common, but none of the mentioned solutions worked for me.

-Most solutions suggest disabling "Wake on LAN" in the BIOS, but that setting is already disabled in my case
-Some solutions suggest editing some GRUB configuration files, but apart from being problematic because these solutions did not explain WHY this should help, the respective configuration files are not found on my system:
    -Some suggest editing /etc/grub/modules, but that does not exist on my system
   -others exist editing /etc/grub.conf, but that does not exist on my system either

Does anybody have a solution to the problem (and, if possible, an explanation too)?

---

### Post by Katzwinkel on 2016-09-05
However, If anybodyhas found a solution that works, without wanting or being able to explain why, That would be welcome too :(

---

### Post by Jimysbil on 2016-09-05
A solution you could apply is you try to reboot and when you see the Grub menu press 'c' and type 'halt'.

If you have access on a root terminal you may try those commands:
```
halt -p
shutdown -P
shutdown -h now
poweroff
```

---

### Post by Katzwinkel on 2016-09-10
Thanks, but the terminal command did not work (Computer just rebooted again instead of turning off).
There must be another way to power off the netbook, other than waiting for the right moment to abort the reboot?
This must be an issue with the new Ubuntu version, as this did not happen with the older version?

UPDATE: reactivated hibernation mode to try If I can use this as an alternative to power off. Doesn't work either. Sending the netbook into hibernation mode triggers a reboot!

---

### Post by pqwoerituytrueiwoq on 2016-09-10
does it have any bios setting that could have it boot on a schedule or even after power loss?

---

### Post by Katzwinkel on 2016-09-10
@pqwoerituytrueiwoq
no, only "wake on LAN" and that is deactivated

---

