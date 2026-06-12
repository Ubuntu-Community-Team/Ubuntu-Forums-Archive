---
title: "Disable X Server"
date: 2007-05-05
forum: General Help
---

### Post by matty13 on 2007-05-05
I need to install my nvidia graphics drivers, how do i disable x server completley in order to do this? can anyone please help me out.

Thanks,
Matt

---

### Post by Theimon on 2007-05-05
When in X press Ctrl+Alt+F1, you'll get a commandprompt. Enter the following: ```
sudo /etc/init.d/gdm stop
``` (or kdm when you run Kubuntu)
When you did that, the X server is dead. To start X again enter: ```
sudo /etc/init.d/gdm stop
```
But since you're installing nvidia drivers, it's easier to just reboot the system, that way you can be sure all the right modules get loaded for nvidia to work. Enter this ```
sudo shutdown -r now
``` at the prompt.

---

### Post by matty13 on 2007-05-05
How do i get into X im new to all this you see you'll have to explain fully for me.
At moment i believe im in

Gnome on the desktop yeah?

So how would i get into X :S

---

### Post by Theimon on 2007-05-05
When you startup your computer, it will load all necessary modules and processes. As soon as you get the login screen, you're in fact in X. When you're at the login screen you can do the above instructions as well. Or you can login first and wait for Gnome to be loaded. Then hit Ctrl+Alt+F1 etc.
You still have to login at the command prompt though.

---

### Post by matty13 on 2007-05-05
Ok got really far really really far on my Nvidia drivers but it asks for now the

**Libc Header files**

Any guide on how to install them so it can compile something to do with matching the kernel, any ideas.

Also says "Libc Development Package" suppose same as Libc Header FIles

I get

```
ERROR: You do not appear to have libc header files installed on your system.
Please install your distribution's libc development package.

Then i click OK

ERROR: Installation of the network driver has failed. Please see the file
'/var/log/nvidia-nforce-installer.log' for details. You may find
suggestions on fixing installation problems in the README available
on the Linux driver download page at www.nvidia.com.
```

---

### Post by Theimon on 2007-05-05
You're compiling them from the binary? They're in the repos.
But hey if you want to compile them from binary, look in Synaptic for libc6 dev. Make sure you removed all of nvidia glx stuff and disable the resticted nv modules. 
Plus make sure that you killed X before you install them.

---

