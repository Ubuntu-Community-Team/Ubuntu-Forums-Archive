---
title: "Ubuntu crashes very often"
date: 2008-06-24
forum: General Help
---

### Post by WeeWoh on 2008-06-24
I am running Ubuntu Studio (sorry if its supposed to be in a different area but this is where the site said to post) on a 1.2GHz AMD Athlon with 384MB of RAM. Usually, after about 1/2 an hour of usage when I insert a USB device of some sort it crashes and I have to turn it off and back on again.

It has happened with Linux Mint as well, except sooner, but Debian seemed to be fine on it (its a testing machine).

It also has a ati radeon 9500 (with 128MB of RAM) in it, which I upgraded from a Nvida Geforce 2 (with 32MB of RAM). I dont think its a cooling problem because it has 2 fans to get rid of all heat, a GPU fan and a CPU fan, plus gaps for the heat to escape from the GPU (OK, I did bodge it together).

---

### Post by jpeddicord on 2008-06-24
Sounds to me like it's run out of memory. Do you get any error messages when it crashes, or does the screen simply lock? Does pressing Ctrl+Alt+Backspace do anything when the system is frozen?

---

### Post by WeeWoh on 2008-06-25
> **jacobmp92 said:**
> Sounds to me like it's run out of memory. Do you get any error messages when it crashes, or does the screen simply lock? Does pressing Ctrl+Alt+Backspace do anything when the system is frozen?
Nope just locks. Have tried pressing 'Num Lock' to check whether it is responding, no luck. It has done it on boot up once and the boot up sound just kept repeating a small section of it like a broken CD. Dont know if that helps.
Neither Fluxbuntu nor Xubuntu crashed on it but this was before the graphics card upgrade. (again if that helps)

---

### Post by jpeddicord on 2008-06-25
> **WeeWoh said:**
> Nope just locks. Have tried pressing 'Num Lock' to check whether it is responding, no luck. It has done it on boot up once and the boot up sound just kept repeating a small section of it like a broken CD. Dont know if that helps.
Neither Fluxbuntu nor Xubuntu crashed on it but this was before the graphics card upgrade. (again if that helps)

In that case, it definitely sounds like it's running out of memory. You may want to open System > Administration > System Monitor and watch your memory usage. If it hits 384 (or above, if you have swap space) when it locks up, that's most likely your problem. If there is still plenty of free memory, then it could be a kernel-based bug.

If it is an issue of running out of memory, then you may want to try out Xubuntu. Xubuntu is a more lightweight version of Ubuntu (Studio) that runs XFCE, a more speedy desktop environment. You can still install the same multimedia applications in Xubuntu.

---

### Post by Habbit on 2008-06-25
Following what jacobmp92 said, do you have an enabled swap partition? You can check by issuing the "free" command on the Terminal: if the three figures in the "Swap" line are all zeros, you either don't have a swap partition or it is disabled. In this case, run "sudo swapon -a" to enable all swap partitions known by the system (though this is theoretically run at boot time) and check the "free" output again.

If you still don't have any swapspace, you're into some trouble, as the applications you're trying to use are very memory-intensive and running out of memory will cause hard crashes: in particular, the Linux kernel tries to kill the most memory-expensive application, which is usually the X server (the graphic environment), but it sometimes cannot be killed because it is connected to kernel video drivers, hence your lockup.

You may have a swap partition, but the system may not know about it: run "sudo fdisk -l" and look for a partition of type "82 Linux swap / Solaris". Run "swapon /dev/sdXY", where XY come from the first field on the fdisk line for the swap partition. If an error occurs, you can try to "clean" the swapspace with "sudo mkswap /dev/sdXY" (be very careful with this command: you will lose all data on the selected partition) and try again. If you get it working, add the swap partition to fstab with a line like this: ```
UUID=5a6e47d7-e5dd-470d-827b-9f64d440ce38 none            swap    sw              0       0
```Where the UUID part is the output of running "sudo vol_id /dev/sdXY" on your swap partition (you can also put just /dev/sdXY instead of the UUID= part, but this method is more resilient to drives being moved around).

If you have _no_ swapspace at this point, you can create either a swap partition or a swap file. The former is the standard way and very slighly faster, while the latter saves you from the dangerous step of messing with partitions. For the size, you'll probably require at least 512MB and maybe 1GB to be on the safe side.[LIST][*]Creating a swap file: find a directory with some free space (I've chosen /var in my example). In the terminal, create an empty file of the required size like this: ```
sudo dd if=/dev/zero of=/var/swap bs=1M count=512
```Where the number after "count=" is the size of the swap file in MB.[*]Creating a swap partition: boot from the Live CD (so that you don't have to worry about what is mounted) and run "System->Administration->Partition editor". Create a partition of type "linux-swap" on free space on your HD (if you don't have any free space, you can try to resize other partitions and move them around, though this is a bit dangerous and will take long). Reboot into your normal Ubuntu installation.[/LIST]No matter whether you've created a swap file or partition, prepare it for hosting swap data with "sudo mkswap DEVFILE", where DEVFILE is either the device name of your swap partition (i.e. /dev/sdXY) or the file name of your swap file (i.e. /var/swap). Then, activate it with "sudo swapon DEVFILE". If everything goes fine (check the output of the "free" command and you should have some swapspace available), add the new swapspace to /etc/fstab as described before, remembering that the UUID= syntax will NOT work with swap files (you just have to put the swap file name in the first field).

Phew! That was it. I hope I didn't leave anything out and that it will be useful :KS

---

### Post by WeeWoh on 2008-06-25
OK Thanks, but ive definately got a swap partition. It is 1.2 GB, is that enought? I have tried Xcfe before but it doesnt quite work as well as GNOME (OK personal preference)

P.S. If Ubuntu Studio is too much, will bog standard Ubuntu not crash?

---

### Post by snowpine on 2008-06-25
Hi WeeWoh, are you using the standard or the real time (rt) kernel? If you are using the rt kernel, can you try loading the standard kernel from your grub menu, see if you are still having the same problems?

I have found that the real time kernel behaves strangely on my computer. Just a suggestion.

---

### Post by WeeWoh on 2008-07-06
Alright, the same happens with CentOS and bog standard Ubuntu, but ive tested Debian with the new configuration and that seemed fine. And Snowpine there doesnt seem to be an entry on the GRUB menu for a normal kernel but thanks anyway.

---

### Post by WeeWoh on 2008-07-24
It happens with Xubuntu as well, so I think its a bug.

Yeah its definately a bug, but it is fixable by putting in on GRUB append men=nopentium

---

