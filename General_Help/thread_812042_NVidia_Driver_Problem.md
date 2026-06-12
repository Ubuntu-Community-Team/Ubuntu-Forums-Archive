---
title: "NVidia Driver Problem"
date: 2008-05-29
forum: General Help
---

### Post by Captain666 on 2008-05-29
after searching the forums for a good while i haven`t been able to come across anything about a problem that im having while trying to install my NVidia GeForce 8500 GT on Ubuntu 8.04. I know that the driver works perfectly on Vista. I figured out all of the steps to install except i ran into a problem:
[B]
-> No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answered Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;this means that the installer will need to compile a kernel interface for your kernel.
ERROR: You do not appear to have libc header files installed on your system.
Please install your distribution's libc development package.[/B]

im new to Linux and am not too sure how to get the libc development package, if anyone could help i would be soooo happy. Thanks!

---

### Post by Nepherte on 2008-05-29
Try installing build-essential before installing the nvidia-driver
```
sudo apt-get install build-essential
```

The way you're installing the driver is fine, but if that doesn't work there exists an easier way called envy.
```
sudo apt-get install envyng-gtk
```
and run the program.

---

### Post by Captain666 on 2008-05-29
well they seemed like they were going to work but then the ubuntu archives timed out 

Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-17.31
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out

theres more to what it said but the rest is basically saying that there were errors and whatnot.. this actually happened to me when i tried to 

sudu apt-get update

im not sure if that started the timing out problem, i know this isnt really the right thread but is there any solutions to the timing out problem so that i can get my driver running?

also says something about:

 Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by Nepherte on 2008-05-29
Just retry or switch mirror if that doesn't work. I had that too a couple of times, but the download resumes where he left and will process everything as it should.

---

### Post by Captain666 on 2008-05-31
thanks so much.. i changed the server and everything worked perfect. I also tried the "build essential" code but it didnt work so i went with envy.. and im honestly disappointed that i didnt hear about envy it sooner. It saved a load of time.

---

