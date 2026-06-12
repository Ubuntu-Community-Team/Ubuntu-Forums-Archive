---
title: "Computer reboots unexpectedly"
date: 2013-08-14
forum: General Help
---

### Post by masoud2 on 2013-08-14
I recently purchased a new Dell XPS 8700 (Core™ i7-4770 processor, 16GB Dual Channel  DDR3 SDRAM), added a 2TB Seagate hard disk and installed Ubuntu 13.04 (64 bit) on this new drive. I have even disconnected the original hard disk (includes Windows 8) as currently the PC is only used for Ubuntu. So there is no dual OS. The system is explicitly used to run OpenFOAM v2.1.1, a CFD toolbox. I run OpenFOAM in serial, i.e., one CPU is allocated to each task, and computations may take several days, means some of the CPUs are running %100 for few days (there are total of 8 CPUs). At least one CPU is left unloaded at all times.    
The issue that I am running to is that over the past week the PC has rebooted 3-4 times unexpectedly. All the running programs are killed as a result. At first I thought it is installing necessary updates, I checked for all the updated and there was nothing left. I shutdown the system and started again. I even disconnected internet connection, as I did not want any reboot (due to downloading/installing updates) at the middle of OpenFOAM computations. Despite all, the PC rebooted again unexpectedly! The PC is in a room with several other computers (older PCs), and nothing similar is happening to other machines. The computer is connected to a surge protector (not the best one, nor  cheapest one), so that may be a reason. But all other computers in the  room are also connected to similar surge protectors, and no rebooting is  observed in those machines. 
I do not find any reason on why rebooting is happening. Does anyone have an idea on what is possibly causing this or how can I stop it? Is there any way (a log file, installing a toolbox etc) that I could learn what forces the system to reboot, or monitor system temperature (this is just a guess)? I appreciate any help very much. Thank you.

---

### Post by Slug71 on 2013-08-14
If you CPUs are running at 100%, I'd say there is a possibility you're running out of RAM or your CPU is getting too hot.

How much RAM does your system have?
You can install Sensors to check your temps.

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by Yellow Pasque on 2013-08-14
Memtest is a good idea too.

---

### Post by masoud2 on 2013-08-14
I do not think RAM is an issue, the computations I am performing use CPU intensively but not RAM. I have 16 GB of memory and 100 GB of SWAP space. I monitor CPU and memory usage frequently and memory use is less than 10 GB. 
Thank you for your hint on installing Sensors. I will pursue this and monitor CPU temperature. That may give me something.

---

### Post by masoud2 on 2013-08-14
Also, are there any particular conditions under which Ubuntu would reboot automatically, without any confirmation from the user? The computer is disconnected from internet, so updates would not be an option!

---

### Post by ian-weisser on 2013-08-14
> **masoud2 said:**
> Also, are there any particular conditions under which Ubuntu would reboot automatically, without any confirmation from the user?

No, unless you programmed it to do so.
Nor would it reboot after updates, unless you programmed it to do so. It merely notifies you to reboot.
This assumes you really mean a hardware reboot. Are you sure that's what is happening? Have you actually seen it reloading the OS? Does /var/log/syslog indicate a system restart?

Most software crashes will simply kill the application without affecting the OS.
Some software crashes will kill the X server process, which will automatically restart and return you to the login screen. That's not a reboot. The OS has not been reloaded, power has not been cycled.
Some software crashes freeze or panic the kernel. The system will be unusable, but turned on.
I don't know of any software crashes that power off or restart the hardware.


Check the BIOS: Rebooting after power failure is a common option. Try switching surge protectors, power cords, and power outlets to rule out power hardware.

Check /var/log/syslog for any unusual log activity (errors, crashes, etc) immediately before the reboot.

---

### Post by masoud2 on 2013-08-15
> **ian-weisser said:**
>  Check /var/log/syslog for any unusual log activity (errors, crashes, etc) immediately before the reboot.

Hi ian-weisser, Thank you for your response. But how can I check syslog immediately **[COLOR=#0000ff]before [/COLOR]**the reboot, when reboot is happening unexpectedly, and in fact that is the whole issue! The PC has been running now for about 40 hours and there is no unusual activity recorded in syslog, so far. What I would need, I guess, is a log file that I can check **[COLOR=#0000ff]AFTER [/COLOR][COLOR=#000000][/COLOR]**a reboot, to tell me what was the reason of rebooting. 
Also, yes I do mean a hardware reboot, i.e., computer goes off and on again. Once I was working next to the computer and this occurred and I saw the OS reloading process.

---

### Post by slw210 on 2013-08-15
Almost sounds like a bad processor or motherboard. My mother's computer was doing the same a couple months ago and the processor was going out (fairly new computer also).

Could be overheating, loose components or bad components.

---

### Post by ian-weisser on 2013-08-15
> **masoud2 said:**
> But how can I check syslog immediately **[COLOR=#0000ff]before [/COLOR]**the reboot, when reboot is happening unexpectedly, and in fact that is the whole issue! The PC has been running now for about 40 hours and there is no unusual activity recorded in syslog, so far. What I would need, I guess, is a log file that I can check **[COLOR=#0000ff]AFTER [/COLOR]**a reboot, to tell me what was the reason of rebooting.
Precisely. /var/log/syslog is not erased by reboot. If there is a software issue that logs, it probably logs there.
It's worth a look after a reboot...though your description reads more and more like a hardware issue to me.

---

### Post by masoud2 on 2013-08-16
Few minutes ago, the computer rebooted unexpectedly again. This is happening after approximately 68 hours of operation. 7 out of 8 CPUs have been active %100 during this time. I have been monitoring system temperature and have not noticed anything wrong, Cores' temperature have been between 30 c and 40 c, though I do not know the temperature at the moment of rebooting. 
I checked var/log/syslog. The log file started recording intensively at Aug 15 17:07, about the exact time that rebooting occured. So did kern.log and pm-powersave.log. Unfortunately, I could not extract any useful information from these files to help me understand the reason(s) of rebooting, so I made a copy of these files and there are attached. I would be very thankful if one could take a look at these files and possibly provide me with some information about the rebooting.[ATTACH]245395[/ATTACH][ATTACH]245396[/ATTACH][ATTACH]245397[/ATTACH]

---

### Post by Yellow Pasque on 2013-08-16
I don't see anything unusual between boots (other than lack of shutdown messages because it's instantly shutting off).

Note: Please use plain text in the future

---

### Post by ian-weisser on 2013-08-16
Agreed.
syslog seems to contain normal activity before the failure.
kern.log shows the filesystem was not properly shut down. Lots of orphaned inodes.
This means the system did not properly "shut down" or "reboot". It was depowered unexpectedly.

You definitely have a hardware fault, not an Ubuntu or software failure.
Some component in that machine (or it's power supply) is intermittently failing, and killing that system.
Since failure kills the system instantly, there is no way to log a record of the failure.

Get out your screwdriver and spare parts bin, and start substituting components....

---

### Post by VMC on 2013-08-16
Looking at this:
```
Aug 12 20:11:39 CFD-PC-1 kernel: [    6.473481] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)Aug 12 20:11:39 CFD-PC-1 kernel: [    6.473486] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Aug 12 20:11:39 CFD-PC-1 kernel: [    6.473489] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPRL 1 (20121018/utaddress-251)
Aug 12 20:11:39 CFD-PC-1 kernel: [    6.473490] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPR_ 2 (20121018/utaddress-251)
Aug 12 20:11:39 CFD-PC-1 kernel: [    6.473492] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Aug 12 20:11:39 CFD-PC-1 kernel: [    6.473492] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPRL 1 (20121018/utaddress-251)
Aug 12 20:11:39 CFD-PC-1 kernel: [    6.473493] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPR_ 2 (20121018/utaddress-251) Aug 12 20:11:39 CFD-PC-1 kernel: [    6.473495] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
```

I found a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1078289"). You might look at it and see if you can add anything.

---

### Post by Yellow Pasque on 2013-08-16
> **ian-weisser said:**
> Get out your screwdriver and spare parts bin, and start substituting components....

*cough Memtest

---

