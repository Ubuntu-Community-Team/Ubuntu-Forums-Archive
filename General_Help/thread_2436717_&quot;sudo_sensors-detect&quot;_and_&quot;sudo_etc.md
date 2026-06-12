---
title: "&quot;sudo sensors-detect&quot; and &quot;sudo /etc/init.d/kmod start&quot; problem (Xubuntu 19.10)"
date: 2020-02-11
forum: General Help
---

### Post by caljp on 2020-02-11
First of all excuse me if you see any type or error in my english. Is not my native language.

So, here is the problem.
Mi cpu fan was running super fast, so after some googling i applied the next commands:
"sudo sensors-detect" which give me the next final output:
[I]"To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
it87
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)y
Successful!
To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
it87
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)y
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/kmod start'
to load them.

Unloading cpuid... OK


Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/kmod start'
to load them.

Unloading cpuid... OK"

[/I]Following the instructions that the output gave me, then i run the next command:
"*sudo /etc/init.d/kmod start*"
And the output was:
"[I][....] Starting kmod (via systemctl): kmod.serviceJob for systemd-modules-load.service failed because the control process exited with error code.
See "systemctl status systemd-modules-load.service" and "journalctl -xe" for details.
 failed[/I]"

I would really like to solve this issue. 

Thanks!

---

### Post by CatKiller on 2020-02-11
By putting the name of the module in /etc/modules it will be loaded at system start automatically. The other (outdated) command is to load the module without restarting, but you can just restart the computer.

---

