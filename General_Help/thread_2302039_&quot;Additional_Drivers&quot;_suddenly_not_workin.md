---
title: "&quot;Additional Drivers&quot; suddenly not working"
date: 2015-11-07
forum: General Help
---

### Post by freshtef on 2015-11-07
Hello everyone.

I have just freshly installed Ubuntu 12.04 LTS.
The first thing I did after the initial install is to download and install drivers for my NVidia gpu. I did that using "Additional Drivers" tool. I have also downloaded everything "Update Manager" tool had to offer.
I restarted the PC, and went to check if my GPU drivers are active, and Additional Drivers suddenly says
```


No proprietary drivers are in use on this system.


```

Second reboot didnt help.
However, when I run

```
[COLOR=#111111][FONT=Consolas]lspci | grep VGA[/FONT][/COLOR]
```

i get

```

01:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 760] (rev a1)

```

What is going on here? :(

---

### Post by howefield on 2015-11-07
What is the output of this command.. specifically the configuration line ?

```
lshw -c video
```

---

### Post by freshtef on 2015-11-07
When I run it, I get this:  

```

  *-display               
       description: VGA compatible controller
       product: GK104 [GeForce GTX 760]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:46 memory:f2000000-f2ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f3000000-f307ffff

```

---

### Post by howefield on 2015-11-07
Looks like the nvidia driver is the one being used then.

You could also check that the open source nouveau isn't being loaded with..

```
lsmod | grep nouveau
```

You should get no output from that command whereas

```
lsmod | grep nvidia
```

should give you something like...

```
hugh@wily:~$ lsmod | grep nouveau
hugh@wily:~$ lsmod | grep nvidia
nvidia               8601600  57
drm                   356352  3 nvidia
hugh@wily:~$ 
```

Probably a bug in additional drivers, which if I recall correctly, was first being talked about some time ago predating 12.04.

---

### Post by efflandt on 2015-11-07
To see which nvidia driver you have installed you can do (-l is small -L):```
dpkg-query -l nvidia* | grep ii
```And to see if it is working install **mesa-utils** and see what **glxinfo** shows```
sudo apt-get update
sudo apt-get install mesa-utils
glxinfo
```

---

### Post by buzzingrobot on 2015-11-07
The Nvidia settings app is also installed by Additional Drivers and it will complain when launched if an Nvidia driver is not in use.

---

### Post by grahammechanical on 2015-11-07
When first launched Additional Drivers always says: "No proprietary drivers are in use." But in its main panel it says: "Searching for available drivers." Additional Drivers does an online search and then compares what is available in the Ubuntu repositories with what is activated on the system and that information is then presented in the main panel with an activated radio button against the driver in use.

What driver is Additional Drivers indicating is in use? An Nividia driver or X.Org X Server - Nouveau?

EDIT: IThere machine has to be connected to the Internet for Additional Drivers to do its stuff.

Regards.

---

