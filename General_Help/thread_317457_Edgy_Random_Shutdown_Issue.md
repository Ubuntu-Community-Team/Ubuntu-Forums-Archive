---
title: "Edgy Random Shutdown Issue"
date: 2006-12-12
forum: General Help
---

### Post by flankk on 2006-12-12
Edgy is shutting down sporadically.  The cause is ACPI reporting an overheating CPU temperature of -264 C.  Clearly this temperature is wrong.  So, I set "acpi=off" in the Grub menu.lst.  When I boot with ACPI disabled, the GDM login screen freezes the mouse and keyboard completely.

This PC boots into Windows fine with no issues and all power management works  flawlessly.  This is **not** a hardware issue.  Windows likely checks for power management support and loads APM dynamically since ACPI is not supported.

Any help would be greatly appreciated.  ](*,)

---

### Post by flankk on 2006-12-12
*bump*  :-({|=

---

### Post by flankk on 2006-12-18
*bump*  :(

---

### Post by flankk on 2006-12-19
Almost a week of no replies.  I still have the same issue.  :(

---

### Post by flankk on 2006-12-19
Hello...  anyone out there?

---

### Post by kevinatkins on 2006-12-19
Hi,

I've had a similar issue with Edgy on my laptop.. ended up going back to Dapper.. But before going that far, if ACPI is not supported on your laptop and you need to use APM instead, try the following:

1. First disable ACPI by modifying the kernel boot options in Grub - edit /boot/grub/menu.lst and append 'ACPI=off NOACPI' to your kernel boot options;

2. Make sure the APM module is loaded at boot - edit /etc/modules and add 'apm' to the end of the list of modules.

Now reboot, and see if it works. If it doesn't, you may need to boot into recovery mode and revesre the above changes.

Failing that, try Daper instead - my laptop overheated with Edgy because CPU throttling didn;t work correctly, and it seemed to be an ACPI-related problem.

---

### Post by flankk on 2006-12-19
This is not a laptop, it is a desktop computer.
> **kevinatkins said:**
> 1. First disable ACPI by modifying the kernel boot options in Grub - edit /boot/grub/menu.lst and append 'ACPI=off NOACPI' to your kernel boot options;


I have already tried this, if you read my post:
> **Flankk]I set "acpi=off" in the Grub menu.lst.[/QUOTE]

The issue is that GDM freezes up when ACPI is disabled.

[QUOTE=kevinatkins said:**
> 2. Make sure the APM module is loaded at boot - edit /etc/modules and add 'apm' to the end of the list of modules.

Is APM compiled as a kernel module though?  I cannot find it in the repos.  Surely I must have the module installed before I can add a call to instantiate it.
I tried this anyway and GDM still locks up on boot.

---

### Post by Azakus on 2006-12-19
If it's already in the kernel, then you won't find a module for it in synaptic (since it is obviously already included).

---

### Post by kevinatkins on 2006-12-20
apm is included as a module in the stock kernel, but you will need to load it - by default it isn't used or loaded (ACPI used by default instead, and you can't use both at the same time!) so you'll need to edit your /etc/modules to make sure the module is loaded at boot time.

---

### Post by clementine on 2007-01-08
Aha! This is just about the exact problem I'm having. I'm new to linux commands (sorry) and would REALLY appreciate a step by step on how to disable the shutdown and- probably more importantly- how to get the fan to turn on , which it never does after bootup - but it runs in grub and under winXP so I know it works. 
THANKS in advance for any help, you smart smart people.

---

### Post by glabouni on 2007-01-08
I would recommend using dapper drake instead of edgy eft.

> [COLOR="Red"]Also note that Edgy 6.10 is considered a development platform for testing new ideas,and technology. Use of this version,and coming versions there after are at your own risk.[/COLOR]
**First Time Linux/Ubuntu users are advised to use dapper,and not edgy as their frist step into Linux. **

(...)

**Note: New users who choose to use edgy as their Operating system are urged to used caution,and advised to know and understand how to fix your own issues. You have been warned.**
[http://ubuntuforums.org/showthread.php?t=286209](http://ubuntuforums.org/showthread.php?t=286209)

---

