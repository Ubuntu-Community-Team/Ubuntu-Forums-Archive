---
title: "kernel update 2.6.20-16-generic and no Xorg"
date: 2007-05-30
forum: General Help
---

### Post by Bloch on 2007-05-30
The kernel update top kernel 2.6.20-16-generic (using Feisty) came in yesterday. I installed and rebooted.

On booting the usual splash screen shows at first, then some command line stuff and then an error message

```
/etc/x11/xorg.conf
FATAL: Could not open
'/lib/modules/2.6.20-16-generic/volatile/nvidia.ko': no such file or directory
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module

Restart gdm when it is configured correctly.
```


When I press Return the system stalls - I do not reach the commandline interface.

I booted into the old kernel (from where I'm working now) and the directory 
/lib/modules/2.6.20-16-generic/volatile
exists. It is empty however.

I have a Nvidia graphics card and it worked perfectly before.

Given I can't even seem to get a commandline in the new kernel, what can I do?

---

### Post by Blender on 2007-05-30
You should be able:
[LIST]
[*] to boot using the recovery entries
[*] to use Control+Alt+F1 to switch to vt1.
[/LIST]

How did you install the nvidia drivers- by using the nvidia-supplied package or the ubuntu package(s)?

---

### Post by Bloch on 2007-05-31
The NVIDIA drivers were originally installed using Envy..

I uninstalled the drivers with envy and rebooted into the new kernel. No joy. Then I booted into the old kernel. Now xorg is broken there too! 

The Nvidia driver was uninstalled by Envy, yet in the error messages it seems the system is still looking for the nvidia kernel module.

The faukt occurs after
running local boot scripts (/etc/rc.local)
This is the error message:

```
NVIDIA: could not open the device file /dev/nvidiact1 (no such device or address)
(EE) NVIDIA (0) Failed to initialize the NVIDIA kernel module!
Please ensure there is a supported NVIDIA GPU in the system
```

Some time ago I messed around with BUM and currently the ```
bootclean
```  scripts are disabled - I don't know what the default is. Still, my system was working fine.

How do I at least thoroughly uninstall the Nvidia so I can fall back on the default X windows?

---

### Post by snakedr on 2007-05-31
If you can get to a terminal you can run envy from the command line as:

envy -t

This will bring up a text menu from which you can reinstall the nvidia driver. Make sure to run it as root.

---

### Post by Princegiri on 2007-11-29
> **snakedr said:**
> If you can get to a terminal you can run envy from the command line as:

envy -t

This will bring up a text menu from which you can reinstall the nvidia driver. Make sure to run it as root.

I had this problem too and this worked for me....... 
but now the sound is gone...... should i just reinstall the alsa once more?

---

### Post by Princegiri on 2007-11-29
ok strike that....... after reinstalling the sound drivers its back online........ 
but i dont know if this is the most ethical way of doing this.....

i just had a fresh install of ubuntu FF...... 
so all i had installed manually were the graphics drivers via envy and the sound drivers from ALSA.......
so all i had to do was reinstall both......

---

