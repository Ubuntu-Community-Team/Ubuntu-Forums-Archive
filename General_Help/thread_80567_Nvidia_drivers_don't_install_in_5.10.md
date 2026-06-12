---
title: "Nvidia drivers don't install in 5.10"
date: 2005-10-22
forum: General Help
---

### Post by legit on 2005-10-22
hey all,
so i followed a tut. on how to install nvidia drivers in warty and it worked fine, however in 5.10 it doesn't work.  The problem is that when i run the nvidia driver setup it says that i am running a different gcc that my kernel was compiled with (im running 4.0 and compiled the kernel with 3.4) it says i can just change the [CC] environment variable to fix teh problem, but im not sure how.  can anyone help me or offer other advice? thanks
- legit

---

### Post by somuchfortheafter on 2005-10-22
okay first off you need to know what kernel you are running. open a terminal and use
```
uname -r
```
to find out what kernel. next open synaptic and search for all the available packages that match that kernel, etc headers and such. install these then install nvidia-settings and nvidia-glx.
finally backup and edit your xorg.conf by
```
sudo cp /etc/X11/xorg.conf /etc/xorg.conf.bc
```
```
sudo gedit /etc/X11/xorg.conf
```
find the section that says most likely nv for your video driver and replace it with nvidia. to test that the drivers are indeed working use ctrl-alt-backspace. hopefully this works out for ya.

---

### Post by legit on 2005-10-22
[QUOTE=somuchfortheafter]okay first off you need to know what kernel you are running. open a terminal and use
```
uname -r
```
to find out what kernel. next open synaptic and search for all the available packages that match that kernel, etc headers and such. install these then install nvidia-settings and nvidia-glx.
[/QUOTE]
i did this and i still got that error, also what is nvidia-settings and nvidia-glx, are those just the driver i have to install

---

### Post by tofuconfetti on 2005-10-23
I just solved this very problem.  There were a couple of issues.  First of all there were no kernel headers for the drivers to load, so it wouldn't even load or work if you installed it.  So step one was to install them.  Use synaptics install the "linux-headers" for your kernel.  You'll need to know your exact kernel.  Using "uname -r" I found mine were 2.6.12-r9.  So I loaded the "linux-headers for kernel 2.6.12-r9".  

Now the module (driver) should load.  I reinstalled (or install for the first time) nvidia-glx, nvidia-configuration, and nvidia-kernel-drivers using the synaptics package manager.

I still had one more problem, the module wasn't automatically loading at boot.  You can see if it's available before you add it to the boot list by opening a terminal and typing "sudo modprobe nvidia".  If it's there and able to work, you'll get a response showing the module.  If you want to test it further type "lsmod | grep nvidia".  You should get the same list.

If you reboot and it's not there (which it probably won't be since mine did not get automagically added to the list), then edit the /etc/modules file and add "nvidia" (no quotes) to the end of the list and it'll load at boot time.  

Your problem is that your module isn't getting loaded.  You should be working after you make sure all the steps above have been done.

---

