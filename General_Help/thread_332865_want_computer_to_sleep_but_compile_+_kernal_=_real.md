---
title: "want computer to sleep but compile + kernal = really bad feeling."
date: 2007-01-06
forum: General Help
---

### Post by Portable_Jim on 2007-01-06
I want to send my computer to sleep - standby, but...
```
apmsleep: Your kernel does not support APM.
apmsleep: Recompile kernel with APM and /dev/rtc support
```I don't like the sound of that. Compiling programs is alright but to compile the very foundations of your operating system seems to be a recipe for disaster.

---

### Post by Portable_Jim on 2007-01-07
(bump) Does anyone know of a guide that is foolproof for recompiling your kernel.

---

### Post by JohnSka7 on 2007-08-07
Also Bump. I want to set up my ubu to go to sleep at 11pm every night and wake up at 7:30 every morning, and I can see that apmsleep will let me do this, but I don't really know how to recompile the kernel to allow apm support.

Any help?

---

### Post by nick_h on 2007-08-07
Have a look at the [Master Kernel Thread](http://ubuntuforums.org/showthread.php?t=311158).  It is a good starting point but not necessarily foolproof.  Read the instructions carefully.

---

### Post by JohnSka7 on 2007-08-07
Any idea how GDM suspends/hibernates the computer? I can do it that way, but not from the command line...just looking for an alternative before I try to recompile...

---

### Post by nick_h on 2007-08-07
As I understand it the Gnome power manager calls:

/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
/usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux

Which in turn call:

/etc/acpi/sleep.sh
/etc/acpi/hibernate.sh

Try these last 2 from the command line. (with sudo)

---

### Post by bufordsf on 2008-02-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/194314](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/194314) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This seems like a fairly old problem; has anybody had success, and if so with what method? I installed my first Linux last week and I'm a little timid to compile kernel (I think I'll miss some option somewhere that I don't know how to find). I had hoped updating to Gusty up from Dapper would solve the problem -- but no such luck.

This old Fujistu C2240 Lifebook's symptoms resemble others I've seen on the web:
[LIST]
[*]The GDM, a push on the power button, or running "acpitool -s" launches ACPI suspend state succesfully (screen goes down, power still on). I've tried both states S1 and S3. Another push on the power button to wake, and the fan runs, no display: computer hangs.
Similarly hibernation (S4, by running "acpitool -S") is reachable, but on waking the computer immediately boots (seems to have to memory of having been on).
[*]Of course I tried the boot options recommended by documentation (ref. 1), with the same old "No APM support in kernel" and "Recompile kernel with APM and /dev/rtc support" (US locale) coming back from "apm" and "apmsleep".
[/LIST]

I hope that at most I will have to recompile. If that doesn't work, there's an off-tree patch called Tux-on-ice (ref. 2) which is supposed to do something good. I'll be back later, hopefully

[https://help.ubuntu.com/community/SuspendHowto](https://help.ubuntu.com/community/SuspendHowto)
[https://help.ubuntu.com/community/Suspend2Kernel](https://help.ubuntu.com/community/Suspend2Kernel)

---

