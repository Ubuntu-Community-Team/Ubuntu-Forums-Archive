---
title: "Ubuntu 20.04 black screen"
date: 2021-07-30
forum: General Help
---

### Post by gustavo-amor on 2021-07-30
I have a computer with Ubuntu 20.04 with an Nvidia GT710 card and every so often it starts up and the screen goes black with the cursor blinking.


I modified a GRUB line by putting "nomodeset" instead of "quiet splash". It worked for a while but it crashed again.


Every so often I have to retrieve a Timeshift snapshot


Can anyone help me?

---

### Post by Bashing-om on 2021-07-30
gustavo-amor; Hello

I run that same Nvidia card with no issues. The open source nouveau driver is sufficient for my needs.
> 
sysop@2004x-c:~$ lspci -k | grep -iEA5 'vga|3d'
06:00.0 VGA compatible controller: NVIDIA Corporation GK208B [GeForce GT 710] (rev a1)
	Subsystem: eVga.com. Corp. GK208B [GeForce GT 710]
	Kernel driver in use: nouveau
	Kernel modules: nvidiafb, nouveau


In your case running with the "nomodeset" boot option is not an optimal solution.

What would you prefer for the driver ?
 - nouveau works out of the box IF you do not require 3D
 - Nvidia is well supported but secure boot must be disabled in bios to allow the install

Show us presently what we have to work from - booting without added parameters
```

sudo lshw -C display
dpkg -l | grep -i nvidia
cat /var/log/gpu-manager.log

```

and we see which way we go.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by gustavo-amor on 2021-08-01
Nouveau is not good for me since it does not accept the resolution of my 2560x1080 monitor.


Also it wouldn't let me install only Nouveau, it gave an error when installing it.


Searching on the internet I found a tutorial to reconfigure xorg-conf (or so I think since I tried too many things) ...


In the end it is working, I think something goes wrong when the kernel is updated. But I don't know how to fix it so it doesn't happen again.


I'm even considering changing the motherboard and processor so I don't have to use an nvidia graphics ...

---

### Post by Bashing-om on 2021-08-01
gustavo-amor; Good deal :D

as to:
> 
something goes wrong when the kernel is updated. But I don't know how to fix it so it doesn't happen again.

depends on how you installed the driver.
DKMS is supposed to take care of the updates but ....
 and Nvidia says:
> 
Note that many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this rather than NVIDIA's official package.


[INDENT]there is a path that seems right - but;
[INDENT][INDENT]leads to a broken system
[/INDENT][/INDENT][/INDENT]

---

