---
title: "how can I get automount back?"
date: 2008-02-03
forum: General Help
---

### Post by wawarren on 2008-02-03
Whenever I try to access my CDROM drive it forces me to mount it as root from the terminal, and ejecting the same. 

Is there any way to make automount work again for my CDROM?  

It's never done this before. 

Thanks

---

### Post by drs305 on 2008-02-03
Take a look at System, Preferences, Removable Drives and Media and see if the automount options you desire have been unchecked. There are several tabs that may apply.

---

### Post by wawarren on 2008-02-03
Thanks, there's no options unchecked, or anything else suggesting my CDROM wouldn't mount due to permission errors. 

I am having the same issue as the folks in this thread, which is unresolved.  

[http://ubuntuforums.org/showthread.php?t=536715](http://ubuntuforums.org/showthread.php?t=536715)

My fstab line for my cdrom looks fine.

```
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

and here are my permissions.
```
brw-rw---- 1 root cdrom 3, 0 2008-02-03 15:34 /dev/hda

```

The message I get is "unable to mount.  must be superuser to use mount"

---

### Post by wawarren on 2008-02-04
Figure I'll try one last time.  

Does anyone know if my fstab and permissions for my cdrom drive look okay?  Or, if thats not the culprit, where else should I check?  

Ubuntu is still forcing me to mount cdrom as root, and it's never done this before :confused:

---

### Post by drs305 on 2008-02-05
Sorry you aren't getting any responses. 

I don't have my device in fstab. You can check your permissions by opening a nautilus window (with root privileges so you can change permissions if necessary - gksu nautilus). Go to /media/cdrom0 , right click, Properties, and select permissions. Mine are set to create/delete as user and my group can access files. I favor command line but seeing how the permissions are set graphically may provide a little more confidence when you are having problems.

---

### Post by wawarren on 2008-02-05
Thanks for your help.  I'll try that when I get home.

---

### Post by geirha on 2008-02-08
Based on the two posts you pasted in this other thread:
[http://ubuntuforums.org/showthread.php?p=4277691#post4277691](http://ubuntuforums.org/showthread.php?p=4277691#post4277691)
[http://ubuntuforums.org/showthread.php?p=4291066#post4291066](http://ubuntuforums.org/showthread.php?p=4291066#post4291066)

Could you paste the output of "dmesg|tail" after inserting a CD or DVD and having it fail to mount automatically. There might be some clues there.

Segfaults are not good. Do you know what slpp is? "dpkg -S slpp" might show which package it is part of.

---

### Post by wawarren on 2008-02-08
Thanks a lot. I will post the output of my dmesg | tail again after lunch in about 3 1/2 hrs.  

All I could find on SLPP.
> Simple Loop Prevention Protocol (SLPP)
With Release 4.1 Nortel introduces SLPP, an enhanced loop prevention
functionality for any type of L2 or L3 network. SLPP can be used in conjunction
with Spanning Tree or SMLT as well as any L3 protocol. SLPP protects networks
of unwanted network loops by actively detecting whether test packets are looping
back to the originating switch. If a loop is detected a port is switched off. The
auto-enable feature can be used to re-enable the port after a pre-set time.
SLPP does not replace Spanning Tree or SMLT for designing redundant
networks, it however provides additional loop prevention capabilities if undesired
network conditions occur.
For more information on SLPP, see Configuring VLANs, Spanning Tree, and Link
Aggregation (314725-E).


source:  [http://www.archer.pl/doc/p80rn410.pdf](http://www.archer.pl/doc/p80rn410.pdf)

---

### Post by wawarren on 2008-02-08
dmesg | tail after the error.

```
[   56.855210] No dock devices found.
[   56.891030] input: Power Button (FF) as /class/input/input6
[   56.891053] ACPI: Power Button (FF) [PWRF]
[   56.891139] input: Power Button (CM) as /class/input/input7
[   56.891156] ACPI: Power Button (CM) [PWRB]
[   58.073167] Capability LSM initialized
[   61.982565] NET: Registered protocol family 10
[   61.982695] lo: Disabled Privacy Extensions
[   72.620569] eth0: no IPv6 routers present
[17203.759262] slpp[12288]: segfault at 0000000000000000 rip 0000000000401b77 rsp 00007ffff013f020 error 4

```

Note, I can use my cdrom if I mount it with sudo from the terminal.

---

### Post by geirha on 2008-02-08
Ok, no errors there at least, except for that slpp seg fault, which shouldn't be related.

Eject the CD/DVD if any are inserted, then kill the hal daemon with ```
sudo killall hald
``` Check that all hal-processes are dead with ```
ps -ef | grep hal
``` There should be no output except for maybe the "grep hal"-command itself. Then start it in non-daemon mode. ```
sudo hald --daemon=no
``` Wait for it to settle, then insert a CD. There should be a lot of output from hald now. What does it say?

To get hald back to "normal", hit CTRL+C in the terminal you started it in, then run ```
sudo hald
```

---

### Post by wawarren on 2008-02-08
Ok, here is all the output from sudo hald --daemon=no

Note, that once I inserted a CD it only spit out 2 more lines, which are the last 2. 

```
~$ sudo hald --daemon=no
Runner started - allowed paths are '/usr/lib/hal:/usr/lib/hal/scripts:/usr/bin'
Run started hal-system-power-pmi (10000) (0) 
!  full path is '/usr/lib/hal/hal-system-power-pmi', program_dir is '/usr/lib/hal'
/usr/lib/hal/hal-system-power-pmi exited
Run started hald-probe-smbios (10000) (0) 
!  full path is '/usr/lib/hal/hald-probe-smbios', program_dir is '/usr/lib/hal'
/usr/lib/hal/hald-probe-smbios exited
Run started hal-storage-cleanup-all-mountpoints (10000) (0) 
!  full path is '/usr/lib/hal/hal-storage-cleanup-all-mountpoints', program_dir is '/usr/lib/hal'
in hal-storage-cleanup-all-mountpoints
hal_mtab = ''
/usr/lib/hal/hal-storage-cleanup-all-mountpoints exited
Run started hald-addon-keyboard (0) (0) 
!  full path is '/usr/lib/hal/hald-addon-keyboard', program_dir is '/usr/lib/hal'
Run started hald-addon-keyboard (0) (0) 
!  full path is '/usr/lib/hal/hald-addon-keyboard', program_dir is '/usr/lib/hal'
Run started hald-addon-keyboard (0) (0) 
!  full path is '/usr/lib/hal/hald-addon-keyboard', program_dir is '/usr/lib/hal'
Run started hald-addon-keyboard (0) (0) 
!  full path is '/usr/lib/hal/hald-addon-keyboard', program_dir is '/usr/lib/hal'
Run started hald-addon-keyboard (0) (0) 
!  full path is '/usr/lib/hal/hald-addon-keyboard', program_dir is '/usr/lib/hal'
Run started hald-probe-serial (10000) (0) 
!  full path is '/usr/lib/hal/hald-probe-serial', program_dir is '/usr/lib/hal'
Run started hald-addon-cpufreq (0) (0) 
!  full path is '/usr/lib/hal/hald-addon-cpufreq', program_dir is '/usr/lib/hal'
/usr/lib/hal/hald-probe-serial exited
Run started hald-addon-acpi (0) (0) 
!  full path is '/usr/lib/hal/hald-addon-acpi', program_dir is '/usr/lib/hal'
17:39:00.963 [W] addon-cpufreq.c:1363: CPUFreq not supported. Exiting...
/usr/lib/hal/hald-addon-cpufreq exited
Run started hald-probe-serial (10000) (0) 
!  full path is '/usr/lib/hal/hald-probe-serial', program_dir is '/usr/lib/hal'
/usr/lib/hal/hald-probe-serial exited
Run started hald-probe-serial (10000) (0) 
!  full path is '/usr/lib/hal/hald-probe-serial', program_dir is '/usr/lib/hal'
/usr/lib/hal/hald-probe-serial exited
Run started hald-probe-serial (10000) (0) 
!  full path is '/usr/lib/hal/hald-probe-serial', program_dir is '/usr/lib/hal'
/usr/lib/hal/hald-probe-serial exited
Run started hald-probe-hiddev (10000) (0) 
!  full path is '/usr/lib/hal/hald-probe-hiddev', program_dir is '/usr/lib/hal'
/usr/lib/hal/hald-probe-hiddev exited
Run started hald-probe-hiddev (10000) (0) 
!  full path is '/usr/lib/hal/hald-probe-hiddev', program_dir is '/usr/lib/hal'
/usr/lib/hal/hald-probe-hiddev exited
Run started hald-probe-storage (10000) (0) 
!  full path is '/usr/lib/hal/hald-probe-storage', program_dir is '/usr/lib/hal'
/usr/lib/hal/hald-probe-storage exited
Run started hald-addon-storage (0) (0) 
!  full path is '/usr/lib/hal/hald-addon-storage', program_dir is '/usr/lib/hal'
Run started hald-probe-storage (10000) (0) 
!  full path is '/usr/lib/hal/hald-probe-storage', program_dir is '/usr/lib/hal'
/usr/lib/hal/hald-probe-storage exited
Run started hald-probe-volume (10000) (0) 
!  full path is '/usr/lib/hal/hald-probe-volume', program_dir is '/usr/lib/hal'
/usr/lib/hal/hald-probe-volume exited
Run started hald-probe-volume (10000) (0) 
!  full path is '/usr/lib/hal/hald-probe-volume', program_dir is '/usr/lib/hal'
/usr/lib/hal/hald-probe-volume exited
Run started hald-probe-volume (10000) (0) 
!  full path is '/usr/lib/hal/hald-probe-volume', program_dir is '/usr/lib/hal'
/usr/lib/hal/hald-probe-volume exited
Run started hald-probe-storage (10000) (0) 
!  full path is '/usr/lib/hal/hald-probe-storage', program_dir is '/usr/lib/hal'
/usr/lib/hal/hald-probe-storage exited
Run started hald-probe-volume (10000) (0) 
!  full path is '/usr/lib/hal/hald-probe-volume', program_dir is '/usr/lib/hal'
/usr/lib/hal/hald-probe-volume exited

```

I still think this has got to be a simple permissions issue. It was always fine before I used -o force to mount my external hardrive.  

Thanks

---

### Post by geirha on 2008-02-13
Hi, sorry for the late reply on this. I can' think of what's wrong. The fact that you mounted an ntfs with the force-option, I don't see how that could be connected to the automount of cds, though, I don't really know that much of how it really works. I was hoping hald would give some error message that would help get to the bottom of it.

I found this bug-report [https://bugs.launchpad.net/ubuntu/+bug/130367](https://bugs.launchpad.net/ubuntu/+bug/130367). Could you try commenting out the cdrom-drive from /etc/fstab?

---

