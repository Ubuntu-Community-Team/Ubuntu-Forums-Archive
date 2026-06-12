---
title: "[SOLVED] Device manager?"
date: 2008-07-09
forum: General Help
---

### Post by Paul T. on 2008-07-09
Does Ubuntu have a function similar to Windows Device Manager where I can check if all my hardware is working ok?

---

### Post by danwood76 on 2008-07-09
Not as such.
If you open the terminal and do:
```

sudo lshw

```
You will see a list of all your hardware, any that dont have hardware drivers associated get listed as unclaimed.
If you append -short to the end, so sudo lshw -short, it will give a shorter list.

Most hardware in linux is auto detected and will have drivers already, you will normally know if anything isnt working.
Also hardware errors are thrown out in the kernel logs, look through them in the system logs if you're interested.

---

### Post by Vivaldi Gloria on 2008-07-09
> **Paul T. said:**
> Does Ubuntu have a function similar to Windows Device Manager where I can check if all my hardware is working ok?


There isn't one installed out of the box. Have you checked the Hardware drivers in the the top panel system > admin. menu?

There are some apps in the synaptic that you can install (sysinfo etc.). Search for them.

If you are OK with terminal then there are a lot of very strong commands. Start by looking at my post here:

[http://ubuntuforums.org/showthread.php?t=853180](http://ubuntuforums.org/showthread.php?t=853180)

My post there gives only a little selection of commands. Here is some more:

```

aplay -l (sound info)
uname -a (kernel info)
lspci (pci info)
lsusb
ls /dev/disk/* -lah (disk info)
fdisk -l (disk info)
free -m (memory info)
```

and the list goes on and on. The more you use ubuntu and read these forums the more commands you learn. :-)

See the man pages of the commands for more info, e.g.

```
man free
```

Note that some of these commands works better (or only) with a sudo infront of them. 

If you want to know about a particular type of hardware then ask about the commands for that hardware.

---

### Post by drs305 on 2008-07-09
You can also append the command to create a nice, readable html file - hardware.html on your Desktop in this example :
```
sudo lshw -html > ~/Desktop/hardware.html
```

---

### Post by Paul T. on 2008-07-09
Wow, loads of info from these commands. Thanks all, I'm new to Linux and only just beginning to see how powerful the terminal is, amazing :)

---

