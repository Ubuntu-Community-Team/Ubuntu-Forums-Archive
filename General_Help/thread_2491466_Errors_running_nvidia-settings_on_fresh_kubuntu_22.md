---
title: "Errors running nvidia-settings on fresh kubuntu 22.04"
date: 2023-10-10
forum: General Help
---

### Post by nilovsergey on 2023-10-10
I have installed fresh  kubuntu 22.04 on my laptop   MSI GP70-2PE (GP702PE-426XUA)   and in Driver
manager I have installed  418 (proprietary) and what I see after OS restarted: [https://prnt.sc/_XdxizS0yXGS](https://prnt.sc/_XdxizS0yXGS)


But running nvidia-settings
I see some errors in console :

```

    (nvidia-settings:2079): GLib-GObject-CRITICAL **: 06:45:14.541: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
    
    ** (nvidia-settings:2079): CRITICAL **: 06:45:14.543: ctk_powermode_new: assertion '(ctrl_target != NULL) && (ctrl_target->h != NULL)' failed
    
    ERROR: nvidia-settings could not find the registry key file or the X server is not accessible. This file
           should have been installed along with this driver at
           /usr/share/nvidia/nvidia-application-profiles-key-documentation. The application profiles will
           continue to work, but values cannot be prepopulated or validated, and will not be listed in the help
           text. Please see the README for possible values and descriptions.
    
    
    ** (nvidia-settings:2079): WARNING **: 06:45:14.591: PRIME: Failed to execute child process “/usr/bin/prime-supported” (No such file or directory)
    ** Message: 06:45:14.591: PRIME: is it supported? no

```

and opened nvidia-settings does not look properly :  [https://prnt.sc/O1tCaE3NnYzJ](https://prnt.sc/O1tCaE3NnYzJ)


What is misconfigured and  how can I fix it ?

```

    # sudo lshw -numeric -C display
      *-display UNCLAIMED       
           description: 3D controller
           product: GM108M [GeForce 840M] [10DE:1341]
           vendor: NVIDIA Corporation [10DE]
           physical id: 0
           bus info: pci@0000:01:00.0
           version: a2
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress bus_master cap_list
           configuration: latency=0
           resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
      *-display
           description: VGA compatible controller
           product: 4th Gen Core Processor Integrated Graphics Controller [8086:416]
           vendor: Intel Corporation [8086]
           physical id: 2
           bus info: pci@0000:00:02.0
           logical name: /dev/fb0
           version: 06
           width: 64 bits
           clock: 33MHz
           capabilities: msi pm vga_controller bus_master cap_list rom fb
           configuration: depth=32 driver=i915 latency=0 resolution=1920,1080
           resources: irq:34 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64) memory:c0000-dffff

```all partitions of my OS has a lot of free space : 


    ```
# df -HT  
    Filesystem     Type     Size  Used Avail Use% Mounted on
    tmpfs          tmpfs    824M  1,8M  822M   1% /run
    /dev/sdb2      ext4      53G  8,7G   41G  18% /
    tmpfs          tmpfs    4,2G     0  4,2G   0% /dev/shm
    tmpfs          tmpfs    5,3M  4,1k  5,3M   1% /run/lock
    /dev/sdb5      ext4      28G  302M   26G   2% /boot
    /dev/sdb7      ext4      30G  3,3G   25G  12% /var
    /dev/sdb8      fuseblk  399G  149G  250G  38% /mnt/_work_sdb8
    /dev/sda1      fuseblk   65G   58G  7,2G  89% /mnt/Win_sda1
    /dev/sda6      fuseblk  237G   95G  143G  40% /mnt/Work_sda6
    /dev/sda8      fuseblk  628G  606G   23G  97% /mnt/Media_sda8
    tmpfs          tmpfs    824M   74k  824M   1% /run/user/1000
    
    $ uname -a
    Linux serge-at-home 6.2.0-34-generic #34~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Sep  7 13:12:03 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

```

Priorly I used   kubuntu 20.04 on my laptop and did not have such problems...

---

### Post by Autodave on 2023-10-10
Not sure what driver you installed, but it should have been the newest 535.  HOWEVER, there have been issues with that driver and I would strongly recommend the 525 driver.

---

### Post by nilovsergey on 2023-10-10
Could you please detalize which issues there were with [COLOR=#000000]535 driver ? Which console commands can I use to check ?[/COLOR]

---

### Post by oldfred on 2023-10-10
Do you have UEFI Secure boot on?
You have to provide your own MOK key to install proprietary drivers, if you have Secure Boot on.
Often easier just to turn Secure boot off.
```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo mokutil --sb-state [/COLOR]
[sudo] password for fred:  
SecureBoot disabled 
Platform is in Setup Mode
[/FONT]
```

If you change nVidia driver, you must purge first or you get conflicts and nothing works.
This should show installed nVidia driver:
#What is installed
dkms status

To install recommended:
sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall

You may need this:
sudo update-initramfs -k all -c

---

### Post by #&amp;thj^% on 2023-10-10
+1 with oldfred's suggestions.
And there is nothing wrong with Driver 535 outside of the installer..(hint user)

---

### Post by nilovsergey on 2023-10-10
I had to install mokutil and next :


```
# sudo mokutil --sb-state
EFI variables are not supported on this system

```

Have I move next to
```
sudo apt-get remove --purge nvidia-*
...

```

commands or need to tune some configuation?

---

