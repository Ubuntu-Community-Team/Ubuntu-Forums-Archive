---
title: "Can't install NVIDIA graphics drivers(and yes,I've read the HOWTO)"
date: 2005-09-17
forum: General Help
---

### Post by chimera on 2005-09-17
this is how I start the NVIDIA graphics driver installation:

sudo su
cd /home/chimera
sh NVIDIA-linux(tab)

and I get this:

No precompiled kernel interface was found to match your kernel;would you like the installer to attempt to download a kernel interface from the NVIDIA ftp site?

(I select yes;if you click no,the installation aborts)

No matching precompiled kernel interface was found;installer will need to compile a kernel interface for your system

(I select OK,which is the onyl option I'm given)

ERROR:Unable to find the kernel source tree for the currently running kernel.Please make sure you have installed the kernel source files for your kernel.If you know the current kernel source files are installed,you may specify the kernel source path with the "--kernel-source-path" commandline option

(Once again,I select OK,which is the only option I'm given)

ERROR:Installation failed


And that's just about it.I have installed gcc 3.3 using apt-get,thinking that might be the problem,but it still wont install normally.HELP please,thanks in advance.

[RIGHT]chimera[/RIGHT]

---

### Post by arnieboy on 2005-09-17
> **chimera]this is how I start the NVIDIA graphics driver installation:

sudo su
cd /home/chimera
sh NVIDIA-linux(tab)

and I get this:

No precompiled kernel interface was found to match your kernel said:**
> chimera[/RIGHT]
Please post the contents of ```

uname -r
```

---

### Post by chimera on 2005-09-17
2.6.10-5-386,whatever the hell that tells you :)

[RIGHT]chimera[/RIGHT]

---

### Post by arnieboy on 2005-09-17
[QUOTE=chimera]2.6.10-5-386,whatever the hell that tells you :)

[RIGHT]chimera[/RIGHT][/QUOTE]
please do the following from terminal and after that run the nvidia script again:
```
sudo apt-get install linux-headers-2.6.10-5 linux-headers-2.6.10-5-386
```
run the script after shutting down X server.

---

### Post by chimera on 2005-09-17
**IT WORKS!!!**  \\:D/ 

Thanks a lot

[RIGHT]chimera[/RIGHT]

---

### Post by chimera on 2005-09-17
**IT WORKS!!!**  :D 

Thanks a lot

[RIGHT]chimera[/RIGHT]

---

### Post by arnieboy on 2005-09-17
[QUOTE=chimera]**IT WORKS!!!**  \\:D/ 

Thanks a lot

[RIGHT]chimera[/RIGHT][/QUOTE]
glad to have been of help. :)

---

