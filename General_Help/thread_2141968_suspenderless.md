---
title: "suspenderless"
date: 2013-05-04
forum: General Help
---

### Post by Pedroski55 on 2013-05-04
My Ubuntu 12.04 will not suspend. Very occasionally it actually does suspend when I click suspend, but mostly it just shuts down for about 1 second, then comes right back at me.

Is there any known cure for this?

---

### Post by Toz on 2013-05-04
Can you please provide some more information? Specifically:

[LIST=1]
[*]The make/model of your computer.
[*]The results of the following terminal command:
```
cat /proc/cmdline
```
[*]The contents of /var/log/pm-suspend.log:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.
[*]The results of the following terminal command:
```
cat /var/log/syslog | grep PM:
```
[*]
[/LIST]
More troubleshooting information can be found by clicking the "Kernel Suspend" link in my signature.

---

### Post by Pedroski55 on 2013-05-04
Thanks for that. 

1)
This is a Toshiba C600D laptop.

2) 
pedro@peterpu:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-28-generic root=UUID=092ff536-f1b9-486d-bbe7-f036dbd58bd0 ro quiet splash
pedro@peterpu:~$ 

3)
pedro@peterpu:~$ pastebinit /var/log/pm-suspend.log
[http://paste.ubuntu.com/5633753/](http://paste.ubuntu.com/5633753/)
pedro@peterpu:~$ 


4)
pedro@peterpu:~$ cat /var/log/syslog | grep PM:
pedro@peterpu:~$

---

### Post by Toz on 2013-05-04
> **Pedroski55 said:**
> 
4)
pedro@peterpu:~$ cat /var/log/syslog | grep PM:
pedro@peterpu:~$

This surprises me. Can you share the complete log file:
```
pastebinit /var/log/syslog
```

5. dmesg might also be helpful:
```
pastebinit /var/log/dmesg
```

6. Which video card do you have and which drivers:
```
sudo lspci -vnn | grep -A12 VGA
```

7. And finally, lets try a debug run:
```

sudo bash
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
pm-suspend
```
...when you've recovered from the suspend:
```
pastebinit /var/log/pm-suspend.log
```

---

### Post by Pedroski55 on 2013-05-04
pedro@peterpu:~$ sudo lspci -vnn | grep -A12 VGA
[sudo] password for pedro: 
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310] [1002:9802] (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device [1179:fdf6]
    Flags: bus master, fast devsel, latency 0, IRQ 40
    Memory at 80000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=256]
    Memory at 90300000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: radeon
    Kernel modules: radeon
pedro@peterpu:~$ 

Did all that. Thanks for your help. My machine actually suspended from your command in 7) pm-suspend!

How did you make me root?? I never get that!

---

### Post by Toz on 2013-05-04
> How did you make me root?? I never get that! 
I used the "sudo" command. See: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo").

> Did all that. Thanks for your help. My machine actually suspended from your command in 7) pm-suspend!
**So can you confirm that suspend works from the command line, but not when you click the suspend option? **

Lets try this:
1. Delete the existing suspend log file:
```
sudo rm /var/log/pm-suspend.log
```

2. Try to suspend via the command line:
```
sudo pm-suspend
```

3. Try to suspend with the menu option.

4. Post back /var/log/pm-suspend.log:
```
pastebinit /var/log/pm-suspend.log
```
...and
```
cat /var/log/syslog | grep PM:
```

---

### Post by Pedroski55 on 2013-05-04
Thanks again!

It just suspended twice no problem. From the command line and from the menu!

---

### Post by Pedroski55 on 2013-05-04
The output of the last command is very long, I won't paste it all unless you need it. Here is the end of it:

May  5 08:14:52 peterpu kernel: [ 6615.203642] PM: resume of drv:uvcvideo dev:3-4:1.0 complete after 1215.483 msecs
May  5 08:14:52 peterpu kernel: [ 6615.203735] PM: resume of drv: dev:ep_83 complete after 1215.578 msecs
May  5 08:14:52 peterpu kernel: [ 6615.454494] PM: resume of devices complete after 1487.692 msecs
May  5 08:14:52 peterpu kernel: [ 6615.454670] PM: resume devices took 1.488 seconds
May  5 08:14:52 peterpu kernel: [ 6615.454776] PM: Finishing wakeup.
pedro@peterpu:~$ 



I have to go now, Next time I get a non suspend, how about I pasteinitbin the result to you??

---

### Post by Toz on 2013-05-04
No worries. Post back if the problem re-occurs.

---

