---
title: "Ubunt doesn't start anymore... HELP"
date: 2018-02-04
forum: General Help
---

### Post by prismak on 2018-02-04
After some operations, today Ubuntu 16.04LTS didn't start and continued flickering at the boot during start-up.

I don't know what to check because I'm not really an expert. So please tell me.

After some search on the Net, I found that could be a problem of graphic card drivers. Indeed, "lshw -c display" shows that I have only one display UNCLAIMED... could be this the problem?

Thanks in advance for any help

---

### Post by linuchsan on 2018-02-04
Is it integrated graphics?

---

### Post by cruzer001 on 2018-02-04
Hello prismak

Please post your system specs.

```
inxi -bG
```

---

### Post by prismak on 2018-02-05
It seems that I don't have inxi on recovery mode... I print here the result of ```
inxi -bG
``` on another partition in which i have installed Ubuntu 16.04.2 LTS (it was Ubuntu 16.04.3 LTS on the faulted one)

```
System:    Host: joe-Aspire-ES1-572 Kernel: 4.8.0-36-generic x86_64 bits: 64
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04.2 LTS
Machine:   Device: laptop System: Acer product: Aspire ES1-572 v: V1.06 serial: N/A
           Mobo: Acer model: T-Rex_SK v: V1.06 serial: N/A
           UEFI [Legacy]: Insyde v: V1.06 date: 11/02/2016
Battery    BAT1: charge: 45.7 Wh 100.0% condition: 45.7/48.9 Wh (93%)
CPU:       Dual core Intel Core i3-7100U (-MT-MCP-) speed/max: 899/2400 MHz
Graphics:  Card: Intel Device 5916
           Display Server: x11 (X.Org 1.18.4 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1366x768@59.97hz
           OpenGL: renderer: Mesa DRI Intel Kabylake GT2
           version: 4.3 Mesa 12.0.6
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           Card-2: Intel Device 24fb driver: iwlwifi
Drives:    HDD Total Size: 1000.2GB (2.8% used)
Info:      Processes: 236 Uptime: 3 min Memory: 873.2/3819.2MB
           Client: Shell (bash) inxi: 2.3.56 

```

Otherwise how can I install inxi on recovery mode? It seems network doesn't start...

This instead is the result of ```
lshw -c display
``` on the faulted partition:

```
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:b0000000-b0ffffff memory:a0000000-afffffff ioport:4000(size=64) memory:c0000-dffff


```

---

### Post by cruzer001 on 2018-02-05
I think what your telling me is the HardWare Stack is not working for you.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Revert to the previous kernel at boot (grub) in advance options and see if this will correct it.

[https://help.ubuntu.com/community/Grub2/Submenus](https://help.ubuntu.com/community/Grub2/Submenus)

As shown in the first link.  The 4.4 kernel is supported for five years and the HWE kernels are replaced every 6 months.  This could be why 16.04.2 is working for you and 16.04.3 is not.

---

### Post by prismak on 2018-02-06
I reverted to a previous version of the Kernel, as much as allowed in the advance options but the problem remains.
I didn't say that 16.04.2 is working and 16.04.3 no. 16.04.2 is installed on a new partition (because this is the version I have on CD) but 16.04.3 on the other partition was working fine until I launched something with apt-get  that made the system unstable and after the restart un-boot-able.

Anyway for now at least i succeeded in running the network in recovery mode...

---

### Post by cruzer001 on 2018-02-06
> **prismak said:**
> the other partition was working fine until I launched something with apt-get  that made the system unstable and after the restart un-boot-able.

And what command was that?

In recovery mode

In a terminal try using the "up" arrow to go through your command history and post this command you used.

You can also try:

```
apt-get -f install
```

---

### Post by prismak on 2018-02-06
If I remember correctly I was launching "sudo apt-get install gdb-multiarch", in which it asked as usual: I remove this, I add that, is OK? Yes, I don't care, and after that eclipse seemed messed up, and after restart I entered in the problem.

I know that this is not of much help. Anyway, currently I'm trying to launch "apt-get -f install" but I'm stuck as you can see in the attached image. 

I have network and DNS, but after "dpkg --configure -a" I'm stuck forever on that "Setting up apt" (the following errors don't seem related to the operation, but I'm not sure).

---

### Post by cruzer001 on 2018-02-06
Hello

Something is wrong here.  Apt is trying to set up 1.6~alpha7 and that only appears in Bionic 18.04 thats still in development.

Its not in the developmental options offered for 16.04.  

Makes me think your in the middle of a version upgrade from 16.04 to 18.04.

Could this be?

[https://packages.ubuntu.com/bionic/apt](https://packages.ubuntu.com/bionic/apt)

---

### Post by prismak on 2018-02-07
>  Makes me think your in the middle of a version upgrade from 16.04 to 18.04.

Could this be?

I don't know... Among other things, I tried "apt-get upgrade" on recovery mode... But I don't think before the issue.

Anyway, how I can exit from this stuck situation and run "apt-get -f install"? Do I have to downgrade apt to a stable version?

---

### Post by cruzer001 on 2018-02-07
Hello

> Do I have to downgrade apt to a stable version? 

You can't.  Your package management system (apt) is broken, you cannot download, update or upgrade without it :(

My solution to this is a reinstall of Ubuntu.

You can use Nautilus in your working install to mount the broken one and retrieve any files, then reinstall from here:

[http://old-releases.ubuntu.com/releases/16.04.1/](http://old-releases.ubuntu.com/releases/16.04.1/)

16.04.1 will upgrade to 16.04.3 after you install, but this install will keep you on the 4.4 kernel for the life of the install (its fully supported).  The hardware stack (HWE) will not be installed and there will be no kernel changes every 6 months.  I think this will help keep your system up and running.

If you need further help with a reinstall, please start a new thread and close this one.  I will not be available until later today and a fresh thread will entice others to answer.

---

### Post by prismak on 2018-02-07
> **cruzer001 said:**
> Hello

 

You can't.  Your package management system (apt) is broken, you cannot download, update or upgrade without it :(




Isn't possible to downgrade apt in some way downloading the version from here? 

[https://packages.ubuntu.com/xenial-updates/amd64/apt/download](https://packages.ubuntu.com/xenial-updates/amd64/apt/download)

---

### Post by cruzer001 on 2018-02-07
Even if you could manually install apt; what would happen next?

As I said, I think your stuck in a version upgrade to 18.04.  And if so, you are asking if you can downgrade while your upgrading.  Not possible as far as I know.

Unless someone else has a better solution, I think reinstall is the best answer.  Let this thread ride for a while, maybe someone else will chime in.

---

