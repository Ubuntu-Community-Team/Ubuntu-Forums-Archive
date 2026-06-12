---
title: "Removing old linux-headrs NOT in apt"
date: 2017-08-16
forum: General Help
---

### Post by Graeme_Pietersz on 2017-08-16
Running xubuntu 16.04

I have a lot of old kernel related files, but cannot see the corresponding packages:

```
ls /usr/src/
libdvd-pkg/                              linux-headers-3.13.0-30-generic/  linux-headers-3.13.0-36-generic/  linux-headers-3.13.0-43-generic/
linux-headers-3.12.0-031200rc7/          linux-headers-3.13.0-32/          linux-headers-3.13.0-37/          linux-headers-4.4.0-91/
linux-headers-3.12.0-031200rc7-generic/  linux-headers-3.13.0-32-generic/  linux-headers-3.13.0-37-generic/  linux-headers-4.4.0-91-generic/
linux-headers-3.13.0-24/                 linux-headers-3.13.0-33/          linux-headers-3.13.0-39/          linux-headers-4.4.0-92/
linux-headers-3.13.0-24-generic/         linux-headers-3.13.0-33-generic/  linux-headers-3.13.0-39-generic/  linux-headers-4.4.0-92-generic/
linux-headers-3.13.0-27/                 linux-headers-3.13.0-34/          linux-headers-3.13.0-40/          virtualbox-4.3.10/
linux-headers-3.13.0-27-generic/         linux-headers-3.13.0-34-generic/  linux-headers-3.13.0-40-generic/  virtualbox-guest-4.3.10/
linux-headers-3.13.0-29/                 linux-headers-3.13.0-35/          linux-headers-3.13.0-41/
linux-headers-3.13.0-29-generic/         linux-headers-3.13.0-35-generic/  linux-headers-3.13.0-41-generic/
linux-headers-3.13.0-30/                 linux-headers-3.13.0-36/          linux-headers-3.13.0-43/
```

but

```
/:dpkg --list | grep linux-header
ii  linux-headers-4.4.0-91                      4.4.0-91.114                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-91-generic              4.4.0-91.114                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-92                      4.4.0-92.115                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-92-generic              4.4.0-92.115                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                       4.4.0.92.97                                  amd64        Generic Linux kernel headers
```

The 3.13 stuff is in /boot as well.

```
/:ls /boot                                                                                                                          graeme@anvard[15:15]
abi-3.12.0-031200rc7-generic     config-3.13.0-33-generic             initrd.img-3.13.0-39-generic         System.map-3.13.0-43-generic
abi-3.13.0-24-generic            config-3.13.0-34-generic             initrd.img-3.13.0-40-generic         System.map-3.8.0-32-generic
abi-3.13.0-27-generic            config-3.13.0-35-generic             initrd.img-3.13.0-41-generic         System.map-4.4.0-91-generic
abi-3.13.0-29-generic            config-3.13.0-36-generic             initrd.img-3.13.0-43-generic         System.map-4.4.0-92-generic
abi-3.13.0-30-generic            config-3.13.0-37-generic             initrd.img-3.8.0-32-generic          vmlinuz-3.12.0-031200rc7-generic
abi-3.13.0-32-generic            config-3.13.0-39-generic             initrd.img-4.4.0-91-generic          vmlinuz-3.13.0-24-generic
abi-3.13.0-33-generic            config-3.13.0-40-generic             initrd.img-4.4.0-92-generic          vmlinuz-3.13.0-27-generic
abi-3.13.0-34-generic            config-3.13.0-41-generic             memtest86+.bin                       vmlinuz-3.13.0-29-generic
abi-3.13.0-35-generic            config-3.13.0-43-generic             memtest86+.elf                       vmlinuz-3.13.0-30-generic
abi-3.13.0-36-generic            config-3.8.0-32-generic              memtest86+_multiboot.bin             vmlinuz-3.13.0-32-generic
abi-3.13.0-37-generic            config-4.4.0-91-generic              System.map-3.12.0-031200rc7-generic  vmlinuz-3.13.0-33-generic
abi-3.13.0-39-generic            config-4.4.0-92-generic              System.map-3.13.0-24-generic         vmlinuz-3.13.0-34-generic
abi-3.13.0-40-generic            grub/                                System.map-3.13.0-27-generic         vmlinuz-3.13.0-35-generic
abi-3.13.0-41-generic            initrd.img-3.12.0-031200rc7-generic  System.map-3.13.0-29-generic         vmlinuz-3.13.0-36-generic
abi-3.13.0-43-generic            initrd.img-3.13.0-24-generic         System.map-3.13.0-30-generic         vmlinuz-3.13.0-37-generic
abi-3.8.0-32-generic             initrd.img-3.13.0-27-generic         System.map-3.13.0-32-generic         vmlinuz-3.13.0-39-generic
abi-4.4.0-91-generic             initrd.img-3.13.0-29-generic         System.map-3.13.0-33-generic         vmlinuz-3.13.0-40-generic
abi-4.4.0-92-generic             initrd.img-3.13.0-30-generic         System.map-3.13.0-34-generic         vmlinuz-3.13.0-41-generic
config-3.12.0-031200rc7-generic  initrd.img-3.13.0-32-generic         System.map-3.13.0-35-generic         vmlinuz-3.13.0-43-generic
config-3.13.0-24-generic         initrd.img-3.13.0-33-generic         System.map-3.13.0-36-generic         vmlinuz-3.8.0-32-generic
config-3.13.0-27-generic         initrd.img-3.13.0-34-generic         System.map-3.13.0-37-generic         vmlinuz-4.4.0-91-generic
config-3.13.0-29-generic         initrd.img-3.13.0-35-generic         System.map-3.13.0-39-generic         vmlinuz-4.4.0-92-generic
config-3.13.0-30-generic         initrd.img-3.13.0-36-generic         System.map-3.13.0-40-generic
config-3.13.0-32-generic         initrd.img-3.13.0-37-generic         System.map-3.13.0-41-generic
```

I have not manually installed a kernel or anything like that.

So, why are these files there, and how do I get rid of them

---

### Post by VMC on 2017-08-16
See the results of this 1-liner:
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-3]| xargs sudo apt-get -y purge --dry-run
```

If you were to remove the "--dry-run", it would remove the listed files. I use this after a new kernel. Most people here like keeping at least two kernels around, I don't.

---

### Post by vocx on 2017-08-16
> **Graeme_Pietersz said:**
> Running xubuntu 16.04

I have a lot of old kernel related files, but cannot see the corresponding packages:

I have not manually installed a kernel or anything like that.

So, why are these files there, and how do I get rid of them
This probably means you have been using your current 16.04 system since the days it was 14.04. That is, over the years you installed the corresponding updates and downloaded the kernel files for each, then the system upgraded to 16.04, and the old kernels were never removed.

You don't really need the kernel headers if you are not compiling drivers against it. Some things like the wireless drivers, or the video drivers do need to have the kernel headers so they rebuild themselves after each update, which is probably why you have many headers from older kernels. You also have some virtualbox source code, so maybe the Virtual Box system also used the kernel headers to build the special "guest addition" drivers for the system.

Having many kernel headers in "/usr/src" is not a problem itself, because they do not interfere with the normal functioning of the system. They just sit there, occupying space. Same with the old Linux kernels in "/boot". As long as you have enough hard drive space, the space taken up by all the kernels is not a problem. However, for many people that installed their systems with a small "/boot" partition, if they don't clean the old kernels, they may experience an "out of space" error when they receive an upgrade to a new kernel, so you should definitely want to avoid this problem.

See this thread for some information on removing old kernels
[https://ubuntuforums.org/showthread.php?t=2368158&p=13673982#post13673982](https://ubuntuforums.org/showthread.php?t=2368158&p=13673982#post13673982)

You should try removing (purging) cleanly the old packages with "dpkg". First check how many old kernels you have, and try to remove them.
```

dpkg -l linux-image*

```
You should check for the presence of "image" files, which is the actual kernel. If you remove these, chances are the headers will be removed as well, as they are a dependent on the image packages.

You may also try purging directly with the version number
```

sudo dpkg -P linux-headers-3.13.0-29-generic

```

If that does not work. Then, for the headers, these are completely static files that don't do anything in the system. They are only used when you compile stuff against the kernel. So, if you don't need them any more, you may as well remove the entire kernel header tree for a specific version.
```

sudo rm -rf /usr/src/linux-headers-3.12.0-031200rc7/
sudo rm -rf /usr/src/linux-headers-3.12.0-031200rc7-generic
sudo rm -rf/usr/src/linux-headers-3.13.0-24/
sudo rm -rf/usr/src/linux-headers-3.13.0-24-generic/
... etc.

```

To remove the kernel files in "/boot" you could also manually remove them with "rm" commands, but this is not such a nice way of doing it. Check first if you can purge them with "dpkg". And never remove a kernel you are currently using. You are probably using the 4.4.0-92 kernel, so do not try to remove this kernel from "/boot". Check again the link of the thread above so you get a better idea of the process.

---

### Post by gordintoronto on 2017-08-17
I find that synaptic package manager is the best tool for me to manage all aspects of kernel versions. Within Synaptic, I perform a search such as 3.12.0

Then highlight the oldest installed packages and choose "mark for complete removal" then "apply".

After a cleanup, I run: sudo update-grub

---

