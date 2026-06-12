---
title: "Nvidia Driver - Black screen - Ubuntu 18.04"
date: 2019-03-11
forum: General Help
---

### Post by vinhvu1995 on 2019-03-11
Hi all,

I'm wanting to install CUDA on my computer and I'm currently having problems installing Nvidia drivers on a freshly installed Ubuntu 18.04. Specifically a problem with the display managers I think. The problem doesn't occur if I uninstall the Nvidia drivers (which is the opposite of what I want)
My computer specs are 
I7-6700
Nvidia Tesla K40c (Dedicated Graphics card)
HD Graphics 530 (Integrated Graphics card)

I've googled around and tried to implement the proposed solutions but it refuses to work and it always hangs after booting. If I use gdm3, it gets stuck at 'started gnome display manager', and uncommenting WaylandEnable=false in my /etc/gdm3/custom.conf doesn't work. If I switch to Lightdm, it just hangs without doing anything. 

I also tried the solutions listed in here
[https://askubuntu.com/questions/968365/ubuntu-17-10-nvidia-drivers-black-screen-loop](https://askubuntu.com/questions/968365/ubuntu-17-10-nvidia-drivers-black-screen-loop)
[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1705369](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1705369)
[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1798790](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1798790)

Specifically 
[LIST]
[*]Reinstalling nvidia drivers (Using the repository)
[*]Trying Nvidia driver 418,410,390,384
[*]Updating header files
[*]Adding nomodeset and nvidia-drm.modeset=1 in grub
[*]Trying Lightdm as a display manager
[/LIST]

Is there another way I can get my nvidia drivers to work? am I forgetting to do something important?

Cheers,
Vinh

---

### Post by CatKiller on 2019-03-11
A couple of things that might help:

Since it's a desktop rather than a laptop you'll probably want to disable your Intel graphics in the BIOS.

The last driver version that supports that card is 410. There's no point trying anything newer.

You need to purge all the nvidia stuff when installing a different version.

X's log file is at /var/log/Xorg.0.log. That might help with identifying where the problem lies.

---

### Post by vinhvu1995 on 2019-03-11
I think the last advice helped!

The log was saying that my GPU wasn't powered properly so I'll try sort that out. Cheers! Once I've sorted that out I'll comment back if it works/doesn't work.

---

### Post by fely35 on 2019-06-25
Ubuntu 19.04, nvidia-418: The solution for me was to set the primary display in the PC BIOS to Auto, instead of Nvidia. The bios mentioned that if NVIDIA is selected, the Intel GPU is also active. If you don't have that bios option: Nvidia Optimus: [https://wiki.archlinux.org/index.php/NVIDIA_Optimus#Display_Managers](https://wiki.archlinux.org/index.php/NVIDIA_Optimus#Display_Managers)

---

### Post by vinhvu1995 on 2019-06-25
Heya, thanks for reminding me about this. Yeah turned out that I didn't have enough power in my PSU to power my GPU, when I tried it with a less power hungry GPU it worked fine. The issue was the 'symptoms' for the solutions I googled and a underpowered GPU was the same whereas my google search didn't come up with the underpowered GPU. Thanks for helping out though.

---

