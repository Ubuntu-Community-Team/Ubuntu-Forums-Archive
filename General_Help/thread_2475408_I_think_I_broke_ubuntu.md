---
title: "I think I broke ubuntu"
date: 2022-05-25
forum: General Help
---

### Post by guine on 2022-05-25
I've been trying to get my gpu to stop randomly not working so after the latest time it stopped I decided to try switching nvidia drivers and restart my computer to see if that might do anything but on shutdown it got stuck on a black screen with this message
```
[   0.366457] pci 0000:00:07.0: DPC: RP PI0 log size 0 is invalid
 - Gave up waiting for root file system deice. Common problems:
   - Check rootdelay: (did the system wait long enought?)
 - Missing modules (cat /proc/modules: ls /dev)
ALERT! VVID=98D64C8B-58F0-4731-85CB-3AF3FDED657 does not exist. Dropping to a shell!

BusyBox v1.30.1 (Ubuntu 1:1.30.1-7ubuntu3) built-in shell (ash)
Enter 'help for a list of built-in commands.
(initramfs)
```

I also get this message if I try to boot into the regular install or recovery mode after a hard shutdown as well. Is there any hope of saving this install or am I just going to have to go with a fresh install, I was at least able to boot a live usb and recover my files. Thanks

---

### Post by Autodave on 2022-05-25
Please give us some info: what machine are you running?  What GPU is in it?  What driver did you install and where did you get the driver from?  What version of 'buntu are you running?

---

### Post by guine on 2022-05-25
I'm running ubuntu 22.04 on a asus viviobook with a geforce rtx 3050 mobile gpu. I'm pretty certain I installed the nvidia driver from the ubuntu repositories, I had been using nvidia driver metapackage from nvidia-driver-510 when I having my earlier issues and switched to an older version to see if that might do anything since I was out of other ideas before I got to my current point of not being able to boot.

---

### Post by Bashing-om on 2022-05-25
guine - --

Further to what Autodave request -
as there is also:
> 
 ALERT! VVID=98D64C8B-58F0-4731-85CB-3AF3FDED657 does not exist.

we need to verity the *UUID*.
From the liveUSB mount the install root partition and show:
```

sudo blkid -c /dev/null -o list
cat /mnt/<some-directory>/etc/fstab

```
Here the "<some-directory>" is some mount point that you make up >> mkdir.

[INDENT]see where we go from here
[/INDENT]

---

### Post by guine on 2022-05-25
I'm not entirely sure I did what you were asking for but after doing 
```
sudo blkid -c /dev/null -o list
```
I got 
```
device         fs-type label    mount point     UUID
/dev/loop0   squshfs           /rofs
/dev/nvme0n1p1
                    vfat                (not mounted)   90BA-0042
/dev/nvme0n1p2
                    ext4               (not mounted)   98d64c8b-58f0-4731-85cb-3af3f8ded657
/dev/sda1     iso9660 Linux Mint 20.3 Cinnamon 64-bit /cdrom 2022-01-04-15-01-47-00
/dev/sda2     vfat               (not mounted)    54C5-9C6C
/dev/sda3     ext4    writable /var/log           922bbd01-dfel-434e-9739-c5cld2af124e
```

For the <some directory> I did mkir test and that folder is showing up in file browser and then when I did 
```
cat /mnt/<some-directory>/etc/fstab
```
I got "No such file or directory"

I'm not sure if the root directory needed to be mounted some other way but all my files are showing up in the file browser.

---

### Post by Bashing-om on 2022-05-25
guine;

Well we now know that we are looking at /dev/nvme0n1p2
Next is to look at what the /etc/fstab file is configured for.
in your "test' case run from the liveUSB:
```

sudo mkdir /mnt/test
sudo mount /dev/nvme0n1p2 /mnt/test
cat /mnt/test/etc/fstab

```

Once we have the UUIDs correct then we can take a gander at the graphic's situation.

[INDENT]like dead men
[INDENT][INDENT]just one issue in the box
[/INDENT][/INDENT][/INDENT]

oopps - forgot to advise to UNmount when done prior to rebooting:
```

sudo umount /mnt/test

```

---

### Post by guine on 2022-05-25
After those I got
```
/etc/fstab: static file system information.

Use 'blkid' to print the universally unique identifier for a device; this may be used with UUID= as a more robust way to name devices that works even if disks are added and removed. See fstab(5).

<file system> <mount point>  <type>   <options>         <dump>  <pass>
/ was on /dev/nbme0n1p2 during installation
UUID=98d64c8b-58f0-4731-85cb-3af3f8ded657 /               ext4      errors=remount-ro 0      1
/boot/efi was on /dev/nvme0n1p1 during installation
UUID=90BA-0042  /boot/efi        vfat        umask=0077     0             1
/swapfile                                                         none                 swap        sw                  0        0
```

---

### Post by Bashing-om on 2022-05-25
guine; Hummm ...

UUIDs are correct. No idea presently why the kernel is saying can not not find that UUID.

Moving on to  graphics >>

What results when booting the install - at grub's boot menu: advanced options; recovery ?
Might try both the current kernel version and one release under too.

Here I expect the system to boot as "recovery" employs the nomodeset boot option.

If you do boot up show us:
```

lspci -k | grep -iEA5 'vga|3d'
dpkg -l | grep -i nvidia

```
see what driver(s) are installed - we got a driver conflict ?

[INDENT]moving merrily along
[/INDENT]

---

### Post by guine on 2022-05-26
The computer uses UEFI so I'm not sure I'm getting to where you're hoping to try the commands. When attempting to boot the regular install of ubuntu or recovery mode and I get stuck on the terminal message from before nothing happens when I enter those commands. The only other way I've found to get to a terminal is through this method with the live usb - [https://www.asus.com/support/FAQ/1013017/](https://www.asus.com/support/FAQ/1013017/) where I got this for the first command
```
grep: iEAS: No such file or directory
grep: vga|3d: No such file or directory
```
and this for the second
```
ii nvidia-prime-applet                                                          1.3.1
           all           An applet for NVIDIA Prime
```
I have been using a mint live usb rather than ubuntu since the mint one has been booting a lot faster but can put ubuntu back on the usb from my old computer if that might help.

---

### Post by Bashing-om on 2022-05-26
guine Ack :D

We want to boot the installed operating system.
UEFI: It is the escape key that grub looks for to activate it's boot menu,
As soon as the firmware splash screen clears spam the escape key - as there is only a 3 second window of opportunity.
Now - if you here can not get the grub boot menu - well we know out next step is to investigate the boot code.
Be aware that I have limited experience with this boot code - Might be a lot of trial and error to get the system to boot in this event.

Welcome to the learning curve :D

[INDENT]all we can do is try - try - try again :P
[/INDENT]

---

### Post by guine on 2022-05-26
I was able to get into grub that way but got syntax errors when trying those commands. At the top of the screen it gave me a message saying "minimal bash like editing is supported" and when I hit tab to get options I think it only lists lspci but not dpkg(my choice of hi res monitor is really not seeming like a smart move with these lines of tiny terminal text so its possible I missed it) so that may explain why one of them wasn't working.

---

### Post by Bashing-om on 2022-05-26
guine; Ouch

That does not sound like you got to the advanced options selection - to select a recovery kernel to boot up.

with a "recovery" kernel selected - I do expect that you will boot. Then too I expect it to be but a matter of cleaning up old graphic's driver installs and installing the correct driver.

[INDENT]small steps - [/INDENT]

---

### Post by guine on 2022-05-26
I got to the grub terminal(not sure thats the right name) by pressing escape as soon as the asus name popped up, I did try with all of the different recovery modes and did find one that took me to a purple screen screen(its the same as the screenshop about halfway down the page here [https://linuxhint.com/boot-ubuntu-into-recovery-mode/](https://linuxhint.com/boot-ubuntu-into-recovery-mode/)) with options for "resume - resume normal boot", "clean - try to make free space", "dpkg - repair broken packages", "fsck - check all file systems", "grub - update grub boot loader", "network - enable networking", "root - drop to root sheel prompt", system-summary" that I can navigate through with my arrow keys. I'm holding off on trying anything for a little as I'm reading about this screen first.

---

### Post by Bashing-om on 2022-05-26
guine; Great :D

Making progress and pleased to know that you are doing the homework :D

2 of the recovery menu options will do for what we need.
What option have you selected and what is this result ?

[INDENT]give me a terminal and bash; I will move linux
[/INDENT]

---

### Post by guine on 2022-05-26
I ran the dpkg which removed 60 some files and on the first reboot it went past the terminal section to just a black screen with a cursor that I could move so I did a hard shutdown and was leaning towards trying the fsck option but on the second try it booted to the login and I've logged in so at least some of the issues have resolved. In software and updates under additional drivers its still set to the nvidia-driver-470 that I switched it to before restarting when everything crashing(it originally was on the 510 version when I was periodically losing the gpu, at the moment the gpu is working and I didn't get any errors when booting darktable). As soon as I logged in software updater popped up with some ubuntu base updates so I'm running those now.

---

### Post by Bashing-om on 2022-05-26
guine; Outstanding

Still I want to see what is:
when you get the updates done -
post back:
```

lspci -k | grep -iEA5 'vga|3d'
dpkg -l | grep -i nvidia

```

see what we got

[INDENT]progress - 
[INDENT][INDENT]one step at a time
[/INDENT][/INDENT][/INDENT]

---

### Post by guine on 2022-05-26
To lspci -k | grep -iEA5 'vga|3d' I got
```
0000:00:02.0 VGA compatible controller: Intel Corporation TigerLake-LP GT2 [Iris Xe Graphics] (rev 01)
	DeviceName: VGA
	Subsystem: ASUSTeK Computer Inc. TigerLake-LP GT2 [Iris Xe Graphics]
	Kernel driver in use: i915
	Kernel modules: i915
0000:00:04.0 Signal processing controller: Intel Corporation TigerLake-LP Dynamic Tuning Processor Participant (rev 01)
	Subsystem: ASUSTeK Computer Inc. TigerLake-LP Dynamic Tuning Processor Participant
--
0000:01:00.0 3D controller: NVIDIA Corporation GA107M [GeForce RTX 3050 Mobile] (rev a1)
	DeviceName: Second VGA
	Subsystem: ASUSTeK Computer Inc. GA107M [GeForce RTX 3050 Mobile]
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
0000:2e:00.0 Network controller: MEDIATEK Corp. MT7921 802.11ax PCI Express Wireless Network Adapter
	DeviceName: WLAN
```
And for dpkg -l | grep -i nvidia I got
```
ii  libnvidia-cfg1-470:amd64                   470.129.06-0ubuntu0.22.04.1                amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-470                       470.129.06-0ubuntu0.22.04.1                all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-470:amd64                470.129.06-0ubuntu0.22.04.1                amd64        NVIDIA libcompute package
ii  libnvidia-compute-470:i386                 470.129.06-0ubuntu0.22.04.1                i386         NVIDIA libcompute package
rc  libnvidia-compute-510:amd64                510.60.02-0ubuntu1                         amd64        NVIDIA libcompute package
ii  libnvidia-decode-470:amd64                 470.129.06-0ubuntu0.22.04.1                amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-470:i386                  470.129.06-0ubuntu0.22.04.1                i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-egl-wayland1:amd64               1:1.1.9-1.1                                amd64        Wayland EGL External Platform library -- shared library
ii  libnvidia-encode-470:amd64                 470.129.06-0ubuntu0.22.04.1                amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-470:i386                  470.129.06-0ubuntu0.22.04.1                i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-470:amd64                  470.129.06-0ubuntu0.22.04.1                amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-470:amd64                   470.129.06-0ubuntu0.22.04.1                amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-470:i386                    470.129.06-0ubuntu0.22.04.1                i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-470:amd64                     470.129.06-0ubuntu0.22.04.1                amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-470:i386                      470.129.06-0ubuntu0.22.04.1                i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-470:amd64                   470.129.06-0ubuntu0.22.04.1                amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-470:i386                    470.129.06-0ubuntu0.22.04.1                i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  linux-modules-nvidia-470-5.15.0-33-generic 5.15.0-33.34                               amd64        Linux kernel nvidia modules for version 5.15.0-33
ii  linux-modules-nvidia-470-generic-hwe-22.04 5.15.0-33.34                               amd64        Extra drivers for nvidia-470 for the generic-hwe-22.04 flavour
rc  linux-modules-nvidia-510-5.15.0-25-generic 5.15.0-25.25                               amd64        Linux kernel nvidia modules for version 5.15.0-25
rc  linux-modules-nvidia-510-5.15.0-27-generic 5.15.0-27.28                               amd64        Linux kernel nvidia modules for version 5.15.0-27
ii  linux-objects-nvidia-470-5.15.0-33-generic 5.15.0-33.34                               amd64        Linux kernel nvidia modules for version 5.15.0-33 (objects)
rc  linux-objects-nvidia-510-5.15.0-25-generic 5.15.0-25.25                               amd64        Linux kernel nvidia modules for version 5.15.0-25 (objects)
ii  linux-objects-nvidia-510-5.15.0-27-generic 5.15.0-27.28                               amd64        Linux kernel nvidia modules for version 5.15.0-27 (objects)
ii  linux-objects-nvidia-510-5.15.0-33-generic 5.15.0-33.34                               amd64        Linux kernel nvidia modules for version 5.15.0-33 (objects)
ii  linux-signatures-nvidia-5.15.0-27-generic  5.15.0-27.28                               amd64        Linux kernel signatures for nvidia modules for version 5.15.0-27-generic
ii  linux-signatures-nvidia-5.15.0-33-generic  5.15.0-33.34                               amd64        Linux kernel signatures for nvidia modules for version 5.15.0-33-generic
ii  nvidia-compute-utils-470                   470.129.06-0ubuntu0.22.04.1                amd64        NVIDIA compute utilities
rc  nvidia-compute-utils-510                   510.60.02-0ubuntu1                         amd64        NVIDIA compute utilities
ii  nvidia-driver-470                          470.129.06-0ubuntu0.22.04.1                amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-470                   470.129.06-0ubuntu0.22.04.1                amd64        Shared files used with the kernel module
rc  nvidia-kernel-common-510                   510.60.02-0ubuntu1                         amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-470                   470.129.06-0ubuntu0.22.04.1                amd64        NVIDIA kernel source package
ii  nvidia-opencl-dev:amd64                    11.5.1-1ubuntu1                            amd64        NVIDIA OpenCL development files
ii  nvidia-prime                               0.8.17.1                                   all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            510.47.03-0ubuntu1                         amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-470                           470.129.06-0ubuntu0.22.04.1                amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                    0.18.2                                     all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-470              470.129.06-0ubuntu0.22.04.1                amd64        NVIDIA binary Xorg driver
```

---

### Post by Bashing-om on 2022-05-26
guine -\ hey hey

Nvidia does in fact recommend the 510 version driver for your RTX 3050 :
[https://www.nvidia.com/Download/driverResults.aspx/188994/en-us](https://www.nvidia.com/Download/driverResults.aspx/188994/en-us)

Lets do it like this to re-install
```

sudo apt purge nvidia-*
sudo ubuntu-drivers autoinstall

```
where I do expect with autoinstall that the kernel will choose to install that 510 version.

Reboot to see the effect and once again at the desktop let's do a bit of cleanup -
those packages marked 'rc' >> removed but config files remain;
clean them out with
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```


[INDENT][INDENT]good things can happen
[/INDENT][/INDENT]

---

### Post by guine on 2022-05-27
All of that went through with no errors. In software and updates under additional drivers its now back to the 510 version and both darktable and davinci resolve seem to be finding and using the gpu again. Is there any way to check if I'm likely to loose the gpu again or will we just be wanting to wait and see if I have to do a restart for the gpu again? Before I was typically having to restart every 1-3 days for the gpu so waiting likely won't take too long to get an idea if its working properly.

---

### Post by guine on 2022-05-27
I ended losing my gpu again, I ran these 2 commands again just to see if anything looked differed 
```
lspci -k | grep -iEA5 'vga|3d'
dpkg -l | grep -i nvidia
```
The first one got the same results, the second had some changes but looked related to it using 510 instead of 470 but heres the full report in case that has something I'm missing
```
ii  libnvidia-cfg1-510:amd64                   510.73.05-0ubuntu0.22.04.1                 amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-510                       510.73.05-0ubuntu0.22.04.1                 all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-510:amd64                510.73.05-0ubuntu0.22.04.1                 amd64        NVIDIA libcompute package
ii  libnvidia-compute-510:i386                 510.73.05-0ubuntu0.22.04.1                 i386         NVIDIA libcompute package
ii  libnvidia-decode-510:amd64                 510.73.05-0ubuntu0.22.04.1                 amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-510:i386                  510.73.05-0ubuntu0.22.04.1                 i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-egl-wayland1:amd64               1:1.1.9-1.1                                amd64        Wayland EGL External Platform library -- shared library
ii  libnvidia-encode-510:amd64                 510.73.05-0ubuntu0.22.04.1                 amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-510:i386                  510.73.05-0ubuntu0.22.04.1                 i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-510:amd64                  510.73.05-0ubuntu0.22.04.1                 amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-510:amd64                   510.73.05-0ubuntu0.22.04.1                 amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-510:i386                    510.73.05-0ubuntu0.22.04.1                 i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-510:amd64                     510.73.05-0ubuntu0.22.04.1                 amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-510:i386                      510.73.05-0ubuntu0.22.04.1                 i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  linux-modules-nvidia-510-5.15.0-33-generic 5.15.0-33.34                               amd64        Linux kernel nvidia modules for version 5.15.0-33
ii  linux-modules-nvidia-510-generic-hwe-22.04 5.15.0-33.34                               amd64        Extra drivers for nvidia-510 for the generic-hwe-22.04 flavour
ii  linux-objects-nvidia-470-5.15.0-33-generic 5.15.0-33.34                               amd64        Linux kernel nvidia modules for version 5.15.0-33 (objects)
ii  linux-objects-nvidia-510-5.15.0-27-generic 5.15.0-27.28                               amd64        Linux kernel nvidia modules for version 5.15.0-27 (objects)
ii  linux-objects-nvidia-510-5.15.0-33-generic 5.15.0-33.34                               amd64        Linux kernel nvidia modules for version 5.15.0-33 (objects)
ii  linux-signatures-nvidia-5.15.0-27-generic  5.15.0-27.28                               amd64        Linux kernel signatures for nvidia modules for version 5.15.0-27-generic
ii  linux-signatures-nvidia-5.15.0-33-generic  5.15.0-33.34                               amd64        Linux kernel signatures for nvidia modules for version 5.15.0-33-generic
ii  nvidia-compute-utils-510                   510.73.05-0ubuntu0.22.04.1                 amd64        NVIDIA compute utilities
ii  nvidia-driver-510                          510.73.05-0ubuntu0.22.04.1                 amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-510                   510.73.05-0ubuntu0.22.04.1                 amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-510                   510.73.05-0ubuntu0.22.04.1                 amd64        NVIDIA kernel source package
ii  nvidia-prime                               0.8.17.1                                   all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            510.47.03-0ubuntu1                         amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-510                           510.73.05-0ubuntu0.22.04.1                 amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                    0.18.2                                     all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-510              510.73.05-0ubuntu0.22.04.1                 amd64        NVIDIA binary Xorg driver
```
Are there any tests I should be running when its not working before I restart my computer?

---

### Post by Bashing-om on 2022-05-27
guine; Good news that 

the 510 version driver installed:D

> 
Is there any way to check if I'm likely to loose the gpu again

DKMS (Dynamic Kernel Module Support) takes care of that; should be installed along with the driver. 

```

dkms status

```

with DKMS these things should no longer happen.

//
> 
I ended losing my gpu again,

Ouch! My first encounter with a situation like this.

Anything in the ~/.xsession-errors file for hints as to what is going on ?

[INDENT][INDENT]ain't over til ubuntu sings
[/INDENT][/INDENT]

---

### Post by guine on 2022-05-27
I didn't have dkms installed so I went ahead and installed that. I'm not sure I found the right thing for searching xsession errors, I didn't find anything with xsession-errors in its name but did find several xsession text logs. There were some xsession errors like this in there, not sure if this provides anything useful as I wasn't overly sure what I was looking at :
# attempt to create an error file; abort if we cannot
if (umask 077 && touch "$ERRFILE") 2> /dev/null && [ -w "$ERRFILE" ] &&
  [ ! -L "$ERRFILE" ]; then
  chmod 600 "$ERRFILE"
elif ERRFILE=$(tempfile 2> /dev/null); then
  if ! ln -sf "$ERRFILE" "${TMPDIR:=/tmp}/xsession-$USER"; then
    message "warning: unable to symlink \"$TMPDIR/xsession-$USER\" to" \
             "\"$ERRFILE\"; look for session log/errors in" \
             "\"$TMPDIR/xsession-$USER\"."

---

### Post by Bashing-om on 2022-05-27
guine; Humm ,,,

Odd that DKMS was not installed ....

as to the error file --- in your /home.
"-rw-------  1 sysop sysop  53035 May 27 16:37 .xsession-errors"
```

ls -al ~/.xsession-errors

```
where the ~/ is short hand for your /home.

[INDENT]gots to be a reason
[/INDENT]

---

### Post by Bashing-om on 2022-05-27
guine; Hey another thought !

Nvidia does not play nice with the Wayland environment !

What release are we working with and what desktop ?
show
```

lsb_release -a
echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
ps -efly | grep Xorg
systemctl status gdm

```

[INDENT]again - gots to be a reason
[/INDENT]

---

### Post by guine on 2022-05-27
I'm using 22.04 in gnome, pretty certain with x11 running from past checks although I don't remember ever changing if from wayland which I thought was the default for 22.04, but I've been avoiding wayland since it came out since color profiling monitors doesn't work with wayland yet.

lsb_release -a
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04 LTS
Release:	22.04
Codename:	jammy
```

echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
```
 " " $XDG_CURRENT_DESKTOP
ubuntu   ubuntu:GNOME
```

ps -efly | grep Xorg
```
S christi+    1818    1816  1  80   0 153560 6687332 ep_pol 08:25 tty2  00:12:56 /usr/lib/xorg/Xorg vt2 -displayfd 3 -auth /run/user/1000/gdm/Xauthority -nolisten tcp -background none -noreset -keeptty -novtswitch -verbose 3
S christi+   29561   29543  0  80   0  2348  4466 pipe_r 20:24 pts/0    00:00:00 grep --color=auto Xorg
```

systemctl status gdm(I cut out a lot of the blank and ~ lines from the result just to make it flow better for reading and it stays in this last one rather than letting me enter more terminal commands afterwards):
```
&#9679; gdm.service - GNOME Display Manager
     Loaded: loaded (/lib/systemd/system/gdm.service; static)
     Active: active (running) since Fri 2022-05-27 08:24:53 EDT; 12h ago
    Process: 843 ExecStartPre=/usr/share/gdm/generate-config (code=exited, stat>
   Main PID: 850 (gdm3)
      Tasks: 3 (limit: 18738)
     Memory: 6.6M
        CPU: 152ms
     CGroup: /system.slice/gdm.service
             &#9492;&#9472;850 /usr/sbin/gdm3

May 27 08:24:53 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC systemd[1]: Start>
May 27 08:24:53 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC systemd[1]: Start>
May 27 08:24:53 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm-launch-enviro>
May 27 08:24:59 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm-fingerprint][>
May 27 08:25:03 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm-password][168>
May 27 08:25:03 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm-password][168>
May 27 08:25:03 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm-password][168>
May 27 08:25:03 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm-password][168>
May 27 08:25:08 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm3[850]: Gdm: C>
May 27 15:15:46 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm3[850]: GLib: >
lines 1-21/21 (END)...skipping...





&#9679; gdm.service - GNOME Display Manager
     Loaded: loaded (/lib/systemd/system/gdm.service; static)
     Active: active (running) since Fri 2022-05-27 08:24:53 EDT; 12h ago
    Process: 843 ExecStartPre=/usr/share/gdm/generate-config (code=exited, status=0/SUCCESS)
   Main PID: 850 (gdm3)
      Tasks: 3 (limit: 18738)
     Memory: 6.6M
        CPU: 152ms
     CGroup: /system.slice/gdm.service
             &#9492;&#9472;850 /usr/sbin/gdm3

May 27 08:24:53 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC systemd[1]: Starting GNOME Display Manager...
May 27 08:24:53 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC systemd[1]: Started GNOME Display Manager.
May 27 08:24:53 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm-launch-environment][908]: pam_unix(gdm-launch-environment:session): session opened for user gdm(uid=127) by (uid=0)
May 27 08:24:59 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm-fingerprint][1684]: gkr-pam: no password is available for user
May 27 08:25:03 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm-password][1683]: gkr-pam: unable to locate daemon control file
May 27 08:25:03 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm-password][1683]: gkr-pam: stashed password to try later in open session
May 27 08:25:03 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm-password][1683]: pam_unix(gdm-password:session): session opened for user christian(uid=1000) by (uid=0)
May 27 08:25:03 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm-password][1683]: gkr-pam: gnome-keyring-daemon started properly and unlocked keyring
May 27 08:25:08 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm3[850]: Gdm: Child process -1054 was already dead.
May 27 15:15:46 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm3[850]: GLib: Source ID 94 was not found when attempting to remove it
~
~
~
~
~
~
lines 1-21/21 (END)
&#9679; gdm.service - GNOME Display Manager
     Loaded: loaded (/lib/systemd/system/gdm.service; static)
     Active: active (running) since Fri 2022-05-27 08:24:53 EDT; 12h ago
    Process: 843 ExecStartPre=/usr/share/gdm/generate-config (code=exited, status=0/SUCCESS)
   Main PID: 850 (gdm3)
      Tasks: 3 (limit: 18738)
     Memory: 6.6M
        CPU: 152ms
     CGroup: /system.slice/gdm.service
             &#9492;&#9472;850 /usr/sbin/gdm3

May 27 08:24:53 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC systemd[1]: Starting GNOME Display Manager...
May 27 08:24:53 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC systemd[1]: Started GNOME Display Manager.
May 27 08:24:53 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm-launch-environment][908]: pam_unix(gdm-launch-environment:session): session opened for user gdm(uid=127) by (uid=0)
May 27 08:24:59 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm-fingerprint][1684]: gkr-pam: no password is available for user
May 27 08:25:03 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm-password][1683]: gkr-pam: unable to locate daemon control file
May 27 08:25:03 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm-password][1683]: gkr-pam: stashed password to try later in open session
May 27 08:25:03 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm-password][1683]: pam_unix(gdm-password:session): session opened for user christian(uid=1000) by (uid=0)
May 27 08:25:03 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm-password][1683]: gkr-pam: gnome-keyring-daemon started properly and unlocked keyring
May 27 08:25:08 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm3[850]: Gdm: Child process -1054 was already dead.
May 27 15:15:46 christian-Vivobook-ASUSLaptop-X7600PC-N7600PC gdm3[850]: GLib: Source ID 94 was not found when attempting to remove it
~
~
~
~
~
~
~
lines 1-21/21 (END)
```

---

### Post by Bashing-om on 2022-05-27
guine; Yeah -

Those all say should workie great and last long time.

Next then is Xorg happy ?
```

cat .local/share/xorg/Xorg.0.log

```

[INDENT]looking left and right - gots to be a reason
[/INDENT]

---

### Post by guine on 2022-05-27
I notice a couple of directories not found, not sure how important that is or if theres something else I wasn't noticing(splitting the response between posts due to an error when trying to post it all at once)
```
[    44.152] _XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
[    44.152] _XSERVTransMakeAllCOTSServerListeners: server already running
[    44.153] (--) Log file renamed from "/home/christian/.local/share/xorg/Xorg.pid-1907.log" to "/home/christian/.local/share/xorg/Xorg.1.log"
[    44.153] 
X.Org X Server 1.21.1.3
X Protocol Version 11, Revision 0
[    44.153] Current Operating System: Linux christian-Vivobook-ASUSLaptop-X7600PC-N7600PC 5.15.0-33-generic #34-Ubuntu SMP Wed May 18 13:34:26 UTC 2022 x86_64
[    44.153] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.15.0-33-generic root=UUID=98d64c8b-58f0-4731-85cb-3af3f8ded657 ro quiet splash vt.handoff=7
[    44.153] xorg-server 2:21.1.3-2ubuntu2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    44.153] Current version of pixman: 0.40.0
[    44.153] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    44.153] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    44.153] (==) Log file: "/home/christian/.local/share/xorg/Xorg.1.log", Time: Fri May 27 21:04:40 2022
[    44.153] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    44.153] (==) ServerLayout "layout"
[    44.153] (==) No screen section available. Using defaults.
[    44.153] (**) |-->Screen "Default Screen Section" (0)
[    44.153] (**) |   |-->Monitor "<default monitor>"
[    44.153] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    44.153] (==) Automatically adding devices
[    44.153] (==) Automatically enabling devices
[    44.153] (==) Automatically adding GPU devices
[    44.153] (==) Automatically binding GPU devices
[    44.153] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    44.153] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    44.153] 	Entry deleted from font path.
[    44.153] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    44.153] 	Entry deleted from font path.
[    44.153] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    44.153] 	Entry deleted from font path.
[    44.153] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    44.153] 	Entry deleted from font path.
[    44.153] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    44.153] 	Entry deleted from font path.
[    44.153] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    44.154] (==) ModulePath set to "/usr/lib/xorg/modules"
[    44.154] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    44.154] (II) Loader magic: 0x55fc7ca84020
[    44.154] (II) Module ABI versions:
[    44.154] 	X.Org ANSI C Emulation: 0.4
[    44.154] 	X.Org Video Driver: 25.2
[    44.154] 	X.Org XInput driver : 24.4
[    44.154] 	X.Org Server Extension : 10.0
[    44.154] (++) using VT number 2

[    44.154] (II) systemd-logind: took control of session /org/freedesktop/login1/session/_32
[    44.155] (II) xfree86: Adding drm device (/dev/dri/card0)
[    44.155] (II) Platform probe for /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    44.155] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 15 paused 0
[    44.155] (II) xfree86: Adding drm device (/dev/dri/card1)
[    44.155] (II) Platform probe for /sys/devices/pci0000:00/0000:00:06.0/0000:01:00.0/drm/card1
[    44.156] (II) systemd-logind: got fd for /dev/dri/card1 226:1 fd 16 paused 0
[    44.156] (**) OutputClass "nvidia" ModulePath extended to "/usr/lib/x86_64-linux-gnu/nvidia/xorg,/usr/lib/xorg/modules"
[    44.157] (--) PCI:*(0@0:2:0) 8086:9a49:1043:1a42 rev 1, Mem @ 0x6130000000/16777216, 0x4000000000/268435456, I/O @ 0x00004000/64, BIOS @ 0x????????/131072
[    44.157] (--) PCI: (1@0:0:0) 10de:25a2:1043:1a42 rev 161, Mem @ 0x85000000/16777216, 0x6000000000/4294967296, 0x6100000000/33554432, I/O @ 0x00003000/128, BIOS @ 0x????????/524288
[    44.157] (II) LoadModule: "glx"
[    44.157] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    44.157] (II) Module glx: vendor="X.Org Foundation"
[    44.157] 	compiled for 1.21.1.3, module version = 1.0.0
[    44.157] 	ABI class: X.Org Server Extension, version 10.0
[    44.157] (II) Applying OutputClass "nvidia" to /dev/dri/card1
[    44.157] 	loading driver: nvidia
[    44.260] (==) Matched nvidia as autoconfigured driver 0
[    44.260] (==) Matched nouveau as autoconfigured driver 1
[    44.260] (==) Matched modesetting as autoconfigured driver 2
[    44.260] (==) Matched fbdev as autoconfigured driver 3
[    44.260] (==) Matched vesa as autoconfigured driver 4
[    44.260] (==) Assigned the driver to the xf86ConfigLayout
[    44.260] (II) LoadModule: "nvidia"
[    44.260] (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/nvidia_drv.so
[    44.260] (II) Module nvidia: vendor="NVIDIA Corporation"
[    44.260] 	compiled for 1.6.99.901, module version = 1.0.0
[    44.260] 	Module class: X.Org Video Driver
[    44.260] (II) LoadModule: "nouveau"
[    44.260] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    44.260] (II) Module nouveau: vendor="X.Org Foundation"
[    44.260] 	compiled for 1.21.1.3, module version = 1.0.17
[    44.260] 	Module class: X.Org Video Driver
[    44.260] 	ABI class: X.Org Video Driver, version 25.2
[    44.260] (II) LoadModule: "modesetting"
[    44.260] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    44.260] (II) Module modesetting: vendor="X.Org Foundation"
[    44.260] 	compiled for 1.21.1.3, module version = 1.21.1
[    44.260] 	Module class: X.Org Video Driver
[    44.260] 	ABI class: X.Org Video Driver, version 25.2
[    44.260] (II) LoadModule: "fbdev"
[    44.260] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    44.260] (II) Module fbdev: vendor="X.Org Foundation"
[    44.260] 	compiled for 1.21.1.3, module version = 0.5.0
[    44.260] 	Module class: X.Org Video Driver
[    44.260] 	ABI class: X.Org Video Driver, version 25.2
[    44.260] (II) LoadModule: "vesa"
[    44.260] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    44.260] (II) Module vesa: vendor="X.Org Foundation"
[    44.260] 	compiled for 1.21.1.3, module version = 2.5.0
[    44.260] 	Module class: X.Org Video Driver
[    44.260] 	ABI class: X.Org Video Driver, version 25.2
[    44.260] (II) NVIDIA dlloader X Driver  510.73.05  Sat May  7 05:29:47 UTC 2022
[    44.260] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    44.260] (II) NOUVEAU driver Date:   Sat Jan 23 12:24:42 2021 -0500
[    44.260] (II) NOUVEAU driver for NVIDIA chipset families :
[    44.260] 	RIVA TNT            (NV04)
[    44.260] 	RIVA TNT2           (NV05)
[    44.260] 	GeForce 256         (NV10)
[    44.260] 	GeForce 2           (NV11, NV15)
[    44.260] 	GeForce 4MX         (NV17, NV18)
[    44.260] 	GeForce 3           (NV20)
[    44.260] 	GeForce 4Ti         (NV25, NV28)
[    44.260] 	GeForce FX          (NV3x)
[    44.260] 	GeForce 6           (NV4x)
[    44.260] 	GeForce 7           (G7x)
[    44.260] 	GeForce 8           (G8x)
[    44.260] 	GeForce 9           (G9x)
[    44.261] 	GeForce GTX 2xx/3xx (GT2xx)
[    44.261] 	GeForce GTX 4xx/5xx (GFxxx)
[    44.261] 	GeForce GTX 6xx/7xx (GKxxx)
[    44.261] 	GeForce GTX 9xx     (GMxxx)
[    44.261] 	GeForce GTX 10xx    (GPxxx)
[    44.261] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    44.261] (II) FBDEV: driver for framebuffer: fbdev
[    44.261] (II) VESA: driver for VESA chipsets: vesa
[    44.261] xf86EnableIO: failed to enable I/O ports 0000-03ff (Operation not permitted)
[    44.261] (II) modeset(0): using drv /dev/dri/card0
[    44.261] (WW) Falling back to old probe method for fbdev
[    44.261] (II) Loading sub module "fbdevhw"
[    44.261] (II) LoadModule: "fbdevhw"
[    44.261] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    44.261] (II) Module fbdevhw: vendor="X.Org Foundation"
[    44.261] 	compiled for 1.21.1.3, module version = 0.0.2
[    44.261] 	ABI class: X.Org Video Driver, version 25.2
[    44.261] (II) systemd-logind: releasing fd for 226:1
[    44.261] (II) Loading sub module "fb"
[    44.261] (II) LoadModule: "fb"
[    44.261] (II) Module "fb" already built-in
[    44.261] (II) Loading sub module "wfb"
[    44.261] (II) LoadModule: "wfb"
[    44.261] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    44.261] (II) Module wfb: vendor="X.Org Foundation"
[    44.261] 	compiled for 1.21.1.3, module version = 1.0.0
[    44.261] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    44.261] (II) Loading sub module "ramdac"
[    44.261] (II) LoadModule: "ramdac"
[    44.261] (II) Module "ramdac" already built-in
[    44.262] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[    44.262] (II) modeset(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    44.262] (==) modeset(0): Depth 24, (==) framebuffer bpp 32
[    44.262] (==) modeset(0): RGB weight 888
[    44.262] (==) modeset(0): Default visual is TrueColor
[    44.262] (II) Loading sub module "glamoregl"
[    44.262] (II) LoadModule: "glamoregl"
[    44.262] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    44.265] (II) Module glamoregl: vendor="X.Org Foundation"
[    44.265] 	compiled for 1.21.1.3, module version = 1.0.1
[    44.265] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    44.286] (II) modeset(0): glamor X acceleration enabled on Mesa Intel(R) Xe Graphics (TGL GT2)
[    44.286] (II) modeset(0): glamor initialized
[    44.286] (==) modeset(0): VariableRefresh: disabled
[    44.286] (==) modeset(0): AsyncFlipSecondaries: disabled
[    44.288] (II) modeset(0): Output eDP-1 has no monitor section
[    44.288] (II) modeset(0): Output HDMI-1 has no monitor section
[    44.297] (II) modeset(0): Output DP-1 has no monitor section
[    44.297] (II) modeset(0): Output DP-2 has no monitor section
[    44.299] (II) modeset(0): EDID for output eDP-1
[    44.299] (II) modeset(0): Manufacturer: SDC  Model: 415d  Serial#: 0
[    44.299] (II) modeset(0): Year: 2021  Week: 11
[    44.299] (II) modeset(0): EDID Version: 1.4
[    44.299] (II) modeset(0): Digital Display Input
[    44.299] (II) modeset(0): 10 bits per channel
[    44.299] (II) modeset(0): Digital interface is DisplayPort
[    44.299] (II) modeset(0): Max Image Size [cm]: horiz.: 34  vert.: 22
[    44.299] (II) modeset(0): Gamma: 2.20
[    44.299] (II) modeset(0): No DPMS capabilities specified
[    44.299] (II) modeset(0): Supported color encodings: RGB 4:4:4 
[    44.299] (II) modeset(0): First detailed timing is preferred mode
[    44.299] (II) modeset(0): Preferred mode is native pixel format and refresh rate
[    44.299] (II) modeset(0): redX: 0.680 redY: 0.320   greenX: 0.237 greenY: 0.723
[    44.299] (II) modeset(0): blueX: 0.140 blueY: 0.050   whiteX: 0.312 whiteY: 0.329
[    44.299] (II) modeset(0): Manufacturer's mask: 0
[    44.299] (II) modeset(0): Supported detailed timing:
[    44.299] (II) modeset(0): clock: 572.0 MHz   Image Size:  344 x 215 mm
[    44.299] (II) modeset(0): h_active: 3840  h_sync: 3872  h_sync_end 3880 h_blank_end 3920 h_border: 0
[    44.299] (II) modeset(0): v_active: 2400  v_sync: 2408  v_sync_end 2416 v_blanking: 2432 v_border: 0
[    44.299] (II) modeset(0): Supported detailed timing:
[    44.299] (II) modeset(0): clock: 572.0 MHz   Image Size:  344 x 215 mm
[    44.299] (II) modeset(0): h_active: 3840  h_sync: 3872  h_sync_end 3880 h_blank_end 3920 h_border: 0
[    44.299] (II) modeset(0): v_active: 2400  v_sync: 2408  v_sync_end 2416 v_blanking: 2432 v_border: 0
[    44.299] (II) modeset(0): Unknown vendor-specific block f
[    44.299] (II) modeset(0):  ATNA60YV02-0
[    44.299] (II) modeset(0): Number of EDID sections to follow: 1
[    44.299] (II) modeset(0): EDID (in hex):
[    44.299] (II) modeset(0): 	00ffffffffffff004c835d4100000000
[    44.299] (II) modeset(0): 	0b1f0104b5221678020cf1ae523cb923
[    44.299] (II) modeset(0): 	0c505400000001010101010101010101
[    44.299] (II) modeset(0): 	01010101010171df0050f06020902008
[    44.299] (II) modeset(0): 	880058d71000001b71df0050f0602090
[    44.299] (II) modeset(0): 	2008880058d71000001b0000000f00ff
[    44.299] (II) modeset(0): 	0a3cff0a3c28800300000000000000fe
[    44.299] (II) modeset(0): 	0041544e413630595630322d3020017f
[    44.299] (II) modeset(0): 	02030f00e3058000e606050174600700
[    44.299] (II) modeset(0): 	00000000000000000000000000000000
[    44.299] (II) modeset(0): 	00000000000000000000000000000000
[    44.299] (II) modeset(0): 	00000000000000000000000000000000
[    44.299] (II) modeset(0): 	00000000000000000000000000000000
[    44.299] (II) modeset(0): 	00000000000000000000000000000000
[    44.299] (II) modeset(0): 	00000000000000000000000000000000
[    44.299] (II) modeset(0): 	000000000000000000000000000000b7
[    44.299] (II) modeset(0): Printing probed modes for output eDP-1
[    44.299] (II) modeset(0): Modeline "3840x2400"x60.0  572.01  3840 3872 3880 3920  2400 2408 2416 2432 +hsync -vsync (145.9 kHz eP)
[    44.299] (II) modeset(0): Modeline "3840x2160"x120.0  1446.25  3840 4188 4616 5392  2160 2161 2164 2235 doublescan -hsync +vsync (268.2 kHz d)
[    44.299] (II) modeset(0): Modeline "3840x2160"x120.0  1044.88  3840 3864 3880 3920  2160 2161 2164 2221 doublescan +hsync -vsync (266.5 kHz d)
[    44.299] (II) modeset(0): Modeline "3840x2160"x60.0  712.75  3840 4160 4576 5312  2160 2163 2168 2237 -hsync +vsync (134.2 kHz d)
[    44.299] (II) modeset(0): Modeline "3840x2160"x60.0  533.00  3840 3888 3920 4000  2160 2163 2168 2222 +hsync -vsync (133.2 kHz d)
[    44.299] (II) modeset(0): Modeline "3200x1800"x60.0  492.00  3200 3456 3800 4400  1800 1803 1808 1865 -hsync +vsync (111.8 kHz d)
[    44.300] (II) modeset(0): Modeline "3200x1800"x59.9  373.00  3200 3248 3280 3360  1800 1803 1808 1852 +hsync -vsync (111.0 kHz d)
[    44.300] (II) modeset(0): Modeline "2880x1620"x60.0  396.25  2880 3096 3408 3936  1620 1623 1628 1679 -hsync +vsync (100.7 kHz d)
[    44.300] (II) modeset(0): Modeline "2880x1620"x60.0  303.75  2880 2928 2960 3040  1620 1623 1628 1666 +hsync -vsync (99.9 kHz d)
[    44.300] (II) modeset(0): Modeline "2560x1600"x60.0  348.50  2560 2760 3032 3504  1600 1603 1609 1658 -hsync +vsync (99.5 kHz d)
[    44.300] (II) modeset(0): Modeline "2560x1600"x60.0  268.50  2560 2608 2640 2720  1600 1603 1609 1646 +hsync -vsync (98.7 kHz d)
[    44.300] (II) modeset(0): Modeline "2560x1440"x120.0  638.25  2560 2780 3064 3568  1440 1441 1444 1491 doublescan -hsync +vsync (178.9 kHz d)
[    44.300] (II) modeset(0): Modeline "2560x1440"x120.0  469.12  2560 2584 2600 2640  1440 1441 1444 1481 doublescan +hsync -vsync (177.7 kHz d)
[    44.300] (II) modeset(0): Modeline "2560x1440"x60.0  312.25  2560 2752 3024 3488  1440 1443 1448 1493 -hsync +vsync (89.5 kHz d)
[    44.300] (II) modeset(0): Modeline "2560x1440"x60.0  241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync (88.8 kHz d)
[    44.300] (II) modeset(0): Modeline "2048x1536"x60.0  266.95  2048 2200 2424 2800  1536 1537 1540 1589 -hsync +vsync (95.3 kHz d)
[    44.300] (II) modeset(0): Modeline "1920x1440"x60.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz d)
[    44.300] (II) modeset(0): Modeline "1856x1392"x60.0  218.30  1856 1952 2176 2528  1392 1393 1396 1439 -hsync +vsync (86.4 kHz d)
[    44.300] (II) modeset(0): Modeline "1792x1344"x60.0  204.80  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.7 kHz d)
[    44.300] (II) modeset(0): Modeline "2048x1152"x120.0  406.50  2048 2220 2444 2840  1152 1153 1156 1193 doublescan -hsync +vsync (143.1 kHz d)
[    44.300] (II) modeset(0): Modeline "2048x1152"x120.0  302.50  2048 2072 2088 2128  1152 1153 1156 1185 doublescan +hsync -vsync (142.2 kHz d)
[    44.300] (II) modeset(0): Modeline "2048x1152"x59.9  197.00  2048 2184 2400 2752  1152 1155 1160 1195 -hsync +vsync (71.6 kHz d)
[    44.300] (II) modeset(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz d)
[    44.300] (II) modeset(0): Modeline "1920x1200"x59.9  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync (74.6 kHz d)
[    44.300] (II) modeset(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz d)
[    44.300] (II) modeset(0): Modeline "1920x1080"x120.0  356.38  1920 2080 2288 2656  1080 1081 1084 1118 doublescan -hsync +vsync (134.2 kHz d)
[    44.300] (II) modeset(0): Modeline "1920x1080"x119.9  266.50  1920 1944 1960 2000  1080 1081 1084 1111 doublescan +hsync -vsync (133.2 kHz d)
[    44.300] (II) modeset(0): Modeline "1920x1080"x60.0  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync (67.2 kHz d)
[    44.300] (II) modeset(0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz d)
[    44.300] (II) modeset(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz d)
[    44.300] (II) modeset(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz d)
[    44.300] (II) modeset(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz d)
[    44.300] (II) modeset(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz d)
[    44.300] (II) modeset(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz d)
[    44.300] (II) modeset(0): Modeline "1600x900"x120.0  246.00  1600 1728 1900 2200  900 901 904 932 doublescan -hsync +vsync (111.8 kHz d)
[    44.300] (II) modeset(0): Modeline "1600x900"x119.9  186.50  1600 1624 1640 1680  900 901 904 926 doublescan +hsync -vsync (111.0 kHz d)
[    44.300] (II) modeset(0): Modeline "1600x900"x59.9  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync (56.0 kHz d)
[    44.300] (II) modeset(0): Modeline "1600x900"x59.8   97.50  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.4 kHz d)
[    44.300] (II) modeset(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz d)
[    44.300] (II) modeset(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
[    44.300] (II) modeset(0): Modeline "1400x900"x60.0  103.50  1400 1480 1624 1848  900 903 913 934 -hsync +vsync (56.0 kHz d)
[    44.300] (II) modeset(0): Modeline "1400x900"x59.9   86.50  1400 1448 1480 1560  900 903 913 926 +hsync -vsync (55.4 kHz d)
[    44.300] (II) modeset(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz d)
[    44.300] (II) modeset(0): Modeline "1440x810"x120.0  198.12  1440 1548 1704 1968  810 811 814 839 doublescan -hsync +vsync (100.7 kHz d)
[    44.300] (II) modeset(0): Modeline "1440x810"x119.9  151.88  1440 1464 1480 1520  810 811 814 833 doublescan +hsync -vsync (99.9 kHz d)
[    44.300] (II) modeset(0): Modeline "1368x768"x59.9   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync (47.8 kHz d)
[    44.300] (II) modeset(0): Modeline "1368x768"x59.9   72.25  1368 1416 1448 1528  768 771 781 790 +hsync -vsync (47.3 kHz d)
[    44.300] (II) modeset(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    44.300] (II) modeset(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    44.300] (II) modeset(0): Modeline "1280x800"x120.0  174.25  1280 1380 1516 1752  800 801 804 829 doublescan -hsync +vsync (99.5 kHz d)
[    44.300] (II) modeset(0): Modeline "1280x800"x119.9  134.25  1280 1304 1320 1360  800 801 804 823 doublescan +hsync -vsync (98.7 kHz d)
[    44.300] (II) modeset(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz d)
[    44.300] (II) modeset(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz d)
[    44.300] (II) modeset(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[    44.300] (II) modeset(0): Modeline "1280x720"x120.0  156.12  1280 1376 1512 1744  720 721 724 746 doublescan -hsync +vsync (89.5 kHz d)
[    44.300] (II) modeset(0): Modeline "1280x720"x120.0  120.75  1280 1304 1320 1360  720 721 724 740 doublescan +hsync -vsync (88.8 kHz d)
[    44.300] (II) modeset(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz d)
[    44.300] (II) modeset(0): Modeline "1280x720"x59.7   63.75  1280 1328 1360 1440  720 723 728 741 +hsync -vsync (44.3 kHz d)
[    44.300] (II) modeset(0): Modeline "1024x768"x120.1  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[    44.300] (II) modeset(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    44.300] (II) modeset(0): Modeline "960x720"x120.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[    44.300] (II) modeset(0): Modeline "928x696"x120.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[    44.300] (II) modeset(0): Modeline "896x672"x120.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[    44.300] (II) modeset(0): Modeline "1024x576"x119.9   98.50  1024 1092 1200 1376  576 577 580 597 doublescan -hsync +vsync (71.6 kHz d)
[    44.300] (II) modeset(0): Modeline "1024x576"x119.9   78.38  1024 1048 1064 1104  576 577 580 592 doublescan +hsync -vsync (71.0 kHz d)
[    44.300] (II) modeset(0): Modeline "1024x576"x59.9   46.50  1024 1064 1160 1296  576 579 584 599 -hsync +vsync (35.9 kHz d)
[    44.300] (II) modeset(0): Modeline "1024x576"x59.8   42.00  1024 1072 1104 1184  576 579 584 593 +hsync -vsync (35.5 kHz d)
[    44.300] (II) modeset(0): Modeline "960x600"x119.9   96.62  960 1028 1128 1296  600 601 604 622 doublescan -hsync +vsync (74.6 kHz d)
[    44.300] (II) modeset(0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[    44.300] (II) modeset(0): Modeline "960x540"x119.9   86.50  960 1024 1124 1288  540 541 544 560 doublescan -hsync +vsync (67.2 kHz d)
[    44.300] (II) modeset(0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[    44.300] (II) modeset(0): Modeline "960x540"x59.6   40.75  960 992 1088 1216  540 543 548 562 -hsync +vsync (33.5 kHz d)
[    44.300] (II) modeset(0): Modeline "960x540"x59.8   37.25  960 1008 1040 1120  540 543 548 556 +hsync -vsync (33.3 kHz d)
[    44.300] (II) modeset(0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[    44.300] (II) modeset(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    44.300] (II) modeset(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    44.300] (II) modeset(0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[    44.300] (II) modeset(0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[    44.300] (II) modeset(0): Modeline "864x486"x59.9   32.50  864 888 968 1072  486 489 494 506 -hsync +vsync (30.3 kHz d)
[    44.300] (II) modeset(0): Modeline "864x486"x59.6   30.50  864 912 944 1024  486 489 494 500 +hsync -vsync (29.8 kHz d)
[    44.300] (II) modeset(0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[    44.300] (II) modeset(0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[    44.300] (II) modeset(0): Modeline "800x450"x119.9   59.12  800 848 928 1056  450 451 454 467 doublescan -hsync +vsync (56.0 kHz d)
[    44.300] (II) modeset(0): Modeline "800x450"x119.6   48.75  800 824 840 880  450 451 454 463 doublescan +hsync -vsync (55.4 kHz d)
[    44.300] (II) modeset(0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[    44.300] (II) modeset(0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[    44.300] (II) modeset(0): Modeline "700x450"x119.9   51.75  700 740 812 924  450 451 456 467 doublescan -hsync +vsync (56.0 kHz d)
[    44.300] (II) modeset(0): Modeline "700x450"x119.8   43.25  700 724 740 780  450 451 456 463 doublescan +hsync -vsync (55.4 kHz d)
[    44.300] (II) modeset(0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[    44.300] (II) modeset(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    44.300] (II) modeset(0): Modeline "720x405"x59.5   22.50  720 744 808 896  405 408 413 422 -hsync +vsync (25.1 kHz d)
[    44.300] (II) modeset(0): Modeline "720x405"x59.0   21.75  720 768 800 880  405 408 413 419 +hsync -vsync (24.7 kHz d)
[    44.300] (II) modeset(0): Modeline "684x384"x119.8   42.62  684 720 788 892  384 385 390 399 doublescan -hsync +vsync (47.8 kHz d)
[    44.300] (II) modeset(0): Modeline "684x384"x119.7   36.12  684 708 724 764  384 385 390 395 doublescan +hsync -vsync (47.3 kHz d)
[    44.300] (II) modeset(0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[    44.300] (II) modeset(0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[    44.300] (II) modeset(0): Modeline "640x400"x119.8   41.75  640 676 740 840  400 401 404 415 doublescan -hsync +vsync (49.7 kHz d)
[    44.300] (II) modeset(0): Modeline "640x400"x120.0   35.50  640 664 680 720  400 401 404 411 doublescan +hsync -vsync (49.3 kHz d)
[    44.300] (II) modeset(0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[    44.300] (II) modeset(0): Modeline "640x360"x119.7   37.25  640 672 736 832  360 361 364 374 doublescan -hsync +vsync (44.8 kHz d)
[    44.300] (II) modeset(0): Modeline "640x360"x119.7   31.88  640 664 680 720  360 361 364 370 doublescan +hsync -vsync (44.3 kHz d)
[    44.300] (II) modeset(0): Modeline "640x360"x59.8   18.00  640 664 720 800  360 363 368 376 -hsync +vsync (22.5 kHz d)
[    44.300] (II) modeset(0): Modeline "640x360"x59.3   17.75  640 688 720 800  360 363 368 374 +hsync -vsync (22.2 kHz d)
[    44.300] (II) modeset(0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
```

---

### Post by guine on 2022-05-27
Part 2 of 2

```
[    44.300] (II) modeset(0): Modeline "512x288"x120.0   23.25  512 532 580 648  288 289 292 299 doublescan -hsync +vsync (35.9 kHz d)
[    44.300] (II) modeset(0): Modeline "512x288"x119.8   21.00  512 536 552 592  288 289 292 296 doublescan +hsync -vsync (35.5 kHz d)
[    44.300] (II) modeset(0): Modeline "480x270"x119.3   20.38  480 496 544 608  270 271 274 281 doublescan -hsync +vsync (33.5 kHz d)
[    44.300] (II) modeset(0): Modeline "480x270"x119.6   18.62  480 504 520 560  270 271 274 278 doublescan +hsync -vsync (33.3 kHz d)
[    44.300] (II) modeset(0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[    44.300] (II) modeset(0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[    44.300] (II) modeset(0): Modeline "432x243"x119.8   16.25  432 444 484 536  243 244 247 253 doublescan -hsync +vsync (30.3 kHz d)
[    44.300] (II) modeset(0): Modeline "432x243"x119.1   15.25  432 456 472 512  243 244 247 250 doublescan +hsync -vsync (29.8 kHz d)
[    44.300] (II) modeset(0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[    44.300] (II) modeset(0): Modeline "360x202"x119.0   11.25  360 372 404 448  202 204 206 211 doublescan -hsync +vsync (25.1 kHz d)
[    44.300] (II) modeset(0): Modeline "360x202"x118.3   10.88  360 384 400 440  202 204 206 209 doublescan +hsync -vsync (24.7 kHz d)
[    44.300] (II) modeset(0): Modeline "320x180"x119.7    9.00  320 332 360 400  180 181 184 188 doublescan -hsync +vsync (22.5 kHz d)
[    44.300] (II) modeset(0): Modeline "320x180"x118.6    8.88  320 344 360 400  180 181 184 187 doublescan +hsync -vsync (22.2 kHz d)
[    44.300] (II) modeset(0): EDID for output HDMI-1
[    44.300] (II) modeset(0): EDID for output DP-1
[    44.300] (II) modeset(0): EDID for output DP-2
[    44.300] (II) modeset(0): Output eDP-1 connected
[    44.300] (II) modeset(0): Output HDMI-1 disconnected
[    44.300] (II) modeset(0): Output DP-1 disconnected
[    44.300] (II) modeset(0): Output DP-2 disconnected
[    44.300] (II) modeset(0): Using exact sizes for initial modes
[    44.300] (II) modeset(0): Output eDP-1 using initial mode 3840x2400 +0+0
[    44.300] (==) modeset(0): Using gamma correction (1.0, 1.0, 1.0)
[    44.300] (==) modeset(0): DPI set to (96, 96)
[    44.300] (II) Loading sub module "fb"
[    44.300] (II) LoadModule: "fb"
[    44.300] (II) Module "fb" already built-in
[    44.300] (==) NVIDIA(G0): Depth 24, (==) framebuffer bpp 32
[    44.300] (==) NVIDIA(G0): RGB weight 888
[    44.300] (==) NVIDIA(G0): Default visual is TrueColor
[    44.300] (==) NVIDIA(G0): Using gamma correction (1.0, 1.0, 1.0)
[    44.300] (**) Option "AllowNVIDIAGpuScreens"
[    44.300] (II) Applying OutputClass "nvidia" options to /dev/dri/card1
[    44.300] (**) NVIDIA(G0): Option "AllowEmptyInitialConfiguration"
[    44.300] (**) NVIDIA(G0): Enabling 2D acceleration
[    44.300] (II) Loading sub module "glxserver_nvidia"
[    44.300] (II) LoadModule: "glxserver_nvidia"
[    44.300] (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/libglxserver_nvidia.so
[    44.304] (II) Module glxserver_nvidia: vendor="NVIDIA Corporation"
[    44.304] 	compiled for 1.6.99.901, module version = 1.0.0
[    44.304] 	Module class: X.Org Server Extension
[    44.304] (II) NVIDIA GLX Module  510.73.05  Sat May  7 05:24:37 UTC 2022
[    44.304] (II) NVIDIA: The X server supports PRIME Render Offload.
[    44.305] (II) NVIDIA(G0): NVIDIA GPU NVIDIA GeForce RTX 3050 Laptop GPU (GA107-A) at
[    44.305] (II) NVIDIA(G0):     PCI:1:0:0 (GPU-0)
[    44.305] (--) NVIDIA(G0): Memory: 4194304 kBytes
[    44.305] (--) NVIDIA(G0): VideoBIOS: 94.07.3a.00.b6
[    44.305] (II) NVIDIA(G0): Detected PCI Express Link width: 16X
[    44.305] (II) NVIDIA(G0): Validated MetaModes:
[    44.305] (II) NVIDIA(G0):     "NULL"
[    44.305] (II) NVIDIA(G0): Virtual screen size determined to be 640 x 480
[    44.305] (WW) NVIDIA(G0): Unable to get display device for DPI computation.
[    44.305] (==) NVIDIA(G0): DPI set to (75, 75); computed from built-in default
[    44.305] (II) UnloadModule: "nouveau"
[    44.305] (II) Unloading nouveau
[    44.305] (II) UnloadModule: "fbdev"
[    44.305] (II) Unloading fbdev
[    44.305] (II) UnloadSubModule: "fbdevhw"
[    44.305] (II) Unloading fbdevhw
[    44.305] (II) UnloadModule: "vesa"
[    44.305] (II) Unloading vesa
[    44.317] (==) modeset(0): Backing store enabled
[    44.317] (==) modeset(0): Silken mouse enabled
[    44.390] (II) modeset(0): Initializing kms color map for depth 24, 8 bpc.
[    44.390] (==) modeset(0): DPMS enabled
[    44.390] (II) modeset(0): [DRI2] Setup complete
[    44.390] (II) modeset(0): [DRI2]   DRI driver: iris
[    44.390] (II) modeset(0): [DRI2]   VDPAU driver: va_gl
[    44.390] (WW) NVIDIA: Failed to bind sideband socket to
[    44.390] (WW) NVIDIA:     '/var/run/nvidia-xdriver-5dc87ce4' Permission denied
[    44.390] (II) NVIDIA: Reserving 24576.00 MB of virtual memory for indirect memory
[    44.390] (II) NVIDIA:     access.
[    44.408] (II) NVIDIA(G0): Setting mode "NULL"
[    44.410] (==) NVIDIA(G0): Disabling shared memory pixmaps
[    44.410] (==) NVIDIA(G0): Backing store enabled
[    44.410] (==) NVIDIA(G0): Silken mouse enabled
[    44.410] (==) NVIDIA(G0): DPMS enabled
[    44.410] (II) Loading sub module "dri2"
[    44.410] (II) LoadModule: "dri2"
[    44.410] (II) Module "dri2" already built-in
[    44.410] (II) NVIDIA(G0): [DRI2] Setup complete
[    44.410] (II) NVIDIA(G0): [DRI2]   VDPAU driver: nvidia
[    44.410] (II) Initializing extension Generic Event Extension
[    44.410] (II) Initializing extension SHAPE
[    44.410] (II) Initializing extension MIT-SHM
[    44.410] (II) Initializing extension XInputExtension
[    44.410] (II) Initializing extension XTEST
[    44.410] (II) Initializing extension BIG-REQUESTS
[    44.410] (II) Initializing extension SYNC
[    44.410] (II) Initializing extension XKEYBOARD
[    44.411] (II) Initializing extension XC-MISC
[    44.411] (II) Initializing extension SECURITY
[    44.411] (II) Initializing extension XFIXES
[    44.411] (II) Initializing extension RENDER
[    44.411] (II) Initializing extension RANDR
[    44.411] (II) Initializing extension COMPOSITE
[    44.411] (II) Initializing extension DAMAGE
[    44.411] (II) Initializing extension MIT-SCREEN-SAVER
[    44.411] (II) Initializing extension DOUBLE-BUFFER
[    44.411] (II) Initializing extension RECORD
[    44.411] (II) Initializing extension DPMS
[    44.411] (II) Initializing extension Present
[    44.411] (II) Initializing extension DRI3
[    44.411] (II) Initializing extension X-Resource
[    44.411] (II) Initializing extension XVideo
[    44.411] (II) Initializing extension XVideo-MotionCompensation
[    44.411] (II) Initializing extension SELinux
[    44.411] (II) SELinux: Disabled on system
[    44.411] (II) Initializing extension GLX
[    44.411] (II) Initializing extension GLX
[    44.411] (II) Indirect GLX disabled.
[    44.416] (II) AIGLX: Loaded and initialized iris
[    44.416] (II) GLX: Initialized DRI2 GL provider for screen 0
[    44.416] (II) Initializing extension XFree86-VidModeExtension
[    44.416] (II) Initializing extension XFree86-DGA
[    44.416] (II) Initializing extension XFree86-DRI
[    44.416] (II) Initializing extension DRI2
[    44.416] (II) Initializing extension NV-GLX
[    44.416] (II) Initializing extension NV-CONTROL
[    44.416] (II) modeset(0): Damage tracking initialized
[    44.416] (II) modeset(0): Setting screen physical size to 1016 x 635
[    44.437] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    44.437] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    44.437] (II) LoadModule: "libinput"
[    44.437] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    44.438] (II) Module libinput: vendor="X.Org Foundation"
[    44.438] 	compiled for 1.20.14, module version = 1.2.1
[    44.438] 	Module class: X.Org XInput Driver
[    44.438] 	ABI class: X.Org XInput driver, version 24.1
[    44.438] (II) Using input driver 'libinput' for 'Power Button'
[    44.438] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 45 paused 0
[    44.438] (**) Power Button: always reports core events
[    44.438] (**) Option "Device" "/dev/input/event2"
[    44.440] (II) event2  - Power Button: is tagged by udev as: Keyboard
[    44.440] (II) event2  - Power Button: device is a keyboard
[    44.440] (II) event2  - Power Button: device removed
[    44.440] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    44.440] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    44.440] (**) Option "xkb_model" "pc105"
[    44.440] (**) Option "xkb_layout" "us"
[    44.440] (II) event2  - Power Button: is tagged by udev as: Keyboard
[    44.440] (II) event2  - Power Button: device is a keyboard
[    44.441] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    44.441] (**) Video Bus: Applying InputClass "libinput keyboard catchall"
[    44.441] (II) Using input driver 'libinput' for 'Video Bus'
[    44.441] (II) systemd-logind: got fd for /dev/input/event10 13:74 fd 48 paused 0
[    44.441] (**) Video Bus: always reports core events
[    44.441] (**) Option "Device" "/dev/input/event10"
[    44.441] (II) event10 - Video Bus: is tagged by udev as: Keyboard
[    44.441] (II) event10 - Video Bus: device is a keyboard
[    44.441] (II) event10 - Video Bus: device removed
[    44.441] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input12/event10"
[    44.441] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    44.441] (**) Option "xkb_model" "pc105"
[    44.441] (**) Option "xkb_layout" "us"
[    44.442] (II) event10 - Video Bus: is tagged by udev as: Keyboard
[    44.442] (II) event10 - Video Bus: device is a keyboard
[    44.442] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[    44.442] (**) Video Bus: Applying InputClass "libinput keyboard catchall"
[    44.442] (II) Using input driver 'libinput' for 'Video Bus'
[    44.443] (II) systemd-logind: got fd for /dev/input/event9 13:73 fd 49 paused 0
[    44.443] (**) Video Bus: always reports core events
[    44.443] (**) Option "Device" "/dev/input/event9"
[    44.443] (II) event9  - Video Bus: is tagged by udev as: Keyboard
[    44.443] (II) event9  - Video Bus: device is a keyboard
[    44.443] (II) event9  - Video Bus: device removed
[    44.443] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:06/LNXVIDEO:00/input/input11/event9"
[    44.443] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    44.443] (**) Option "xkb_model" "pc105"
[    44.443] (**) Option "xkb_layout" "us"
[    44.444] (II) event9  - Video Bus: is tagged by udev as: Keyboard
[    44.444] (II) event9  - Video Bus: device is a keyboard
[    44.444] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    44.444] (II) No input driver specified, ignoring this device.
[    44.444] (II) This device may have been added with another device file.
[    44.444] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    44.444] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    44.444] (II) Using input driver 'libinput' for 'Power Button'
[    44.444] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 50 paused 0
[    44.444] (**) Power Button: always reports core events
[    44.444] (**) Option "Device" "/dev/input/event1"
[    44.445] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    44.445] (II) event1  - Power Button: device is a keyboard
[    44.445] (II) event1  - Power Button: device removed
[    44.445] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    44.445] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    44.445] (**) Option "xkb_model" "pc105"
[    44.445] (**) Option "xkb_layout" "us"
[    44.445] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    44.445] (II) event1  - Power Button: device is a keyboard
[    44.446] (II) config/udev: Adding input device PixArt USB Optical Mouse (/dev/input/event7)
[    44.446] (**) PixArt USB Optical Mouse: Applying InputClass "libinput pointer catchall"
[    44.446] (II) Using input driver 'libinput' for 'PixArt USB Optical Mouse'
[    44.446] (II) systemd-logind: got fd for /dev/input/event7 13:71 fd 51 paused 0
[    44.446] (**) PixArt USB Optical Mouse: always reports core events
[    44.446] (**) Option "Device" "/dev/input/event7"
[    44.447] (II) event7  - PixArt USB Optical Mouse: is tagged by udev as: Mouse
[    44.447] (II) event7  - PixArt USB Optical Mouse: device set to 1000 DPI
[    44.447] (II) event7  - PixArt USB Optical Mouse: device is a pointer
[    44.447] (II) event7  - PixArt USB Optical Mouse: device removed
[    44.447] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/0003:093A:2510.0003/input/input9/event7"
[    44.447] (II) XINPUT: Adding extended input device "PixArt USB Optical Mouse" (type: MOUSE, id 10)
[    44.447] (**) Option "AccelerationScheme" "none"
[    44.447] (**) PixArt USB Optical Mouse: (accel) selected scheme none/0
[    44.447] (**) PixArt USB Optical Mouse: (accel) acceleration factor: 2.000
[    44.447] (**) PixArt USB Optical Mouse: (accel) acceleration threshold: 4
[    44.448] (II) event7  - PixArt USB Optical Mouse: is tagged by udev as: Mouse
[    44.448] (II) event7  - PixArt USB Optical Mouse: device set to 1000 DPI
[    44.448] (II) event7  - PixArt USB Optical Mouse: device is a pointer
[    44.448] (II) config/udev: Adding input device PixArt USB Optical Mouse (/dev/input/mouse2)
[    44.448] (II) No input driver specified, ignoring this device.
[    44.448] (II) This device may have been added with another device file.
[    44.448] (II) config/udev: Adding input device USB2.0 HD UVC WebCam: USB2.0 HD (/dev/input/event8)
[    44.448] (**) USB2.0 HD UVC WebCam: USB2.0 HD: Applying InputClass "libinput keyboard catchall"
[    44.448] (II) Using input driver 'libinput' for 'USB2.0 HD UVC WebCam: USB2.0 HD'
[    44.449] (II) systemd-logind: got fd for /dev/input/event8 13:72 fd 52 paused 0
[    44.449] (**) USB2.0 HD UVC WebCam: USB2.0 HD: always reports core events
[    44.449] (**) Option "Device" "/dev/input/event8"
[    44.449] (II) event8  - USB2.0 HD UVC WebCam: USB2.0 HD: is tagged by udev as: Keyboard
[    44.449] (II) event8  - USB2.0 HD UVC WebCam: USB2.0 HD: device is a keyboard
[    44.449] (II) event8  - USB2.0 HD UVC WebCam: USB2.0 HD: device removed
[    44.449] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.0/input/input10/event8"
[    44.449] (II) XINPUT: Adding extended input device "USB2.0 HD UVC WebCam: USB2.0 HD" (type: KEYBOARD, id 11)
[    44.449] (**) Option "xkb_model" "pc105"
[    44.449] (**) Option "xkb_layout" "us"
[    44.450] (II) event8  - USB2.0 HD UVC WebCam: USB2.0 HD: is tagged by udev as: Keyboard
[    44.450] (II) event8  - USB2.0 HD UVC WebCam: USB2.0 HD: device is a keyboard
[    44.450] (II) config/udev: Adding input device ASUE1A01:00 04F3:31D4 Mouse (/dev/input/event5)
[    44.450] (**) ASUE1A01:00 04F3:31D4 Mouse: Applying InputClass "libinput pointer catchall"
[    44.450] (II) Using input driver 'libinput' for 'ASUE1A01:00 04F3:31D4 Mouse'
[    44.451] (II) systemd-logind: got fd for /dev/input/event5 13:69 fd 53 paused 0
[    44.451] (**) ASUE1A01:00 04F3:31D4 Mouse: always reports core events
[    44.451] (**) Option "Device" "/dev/input/event5"
[    44.451] (II) event5  - ASUE1A01:00 04F3:31D4 Mouse: is tagged by udev as: Mouse Pointingstick
[    44.451] (II) event5  - ASUE1A01:00 04F3:31D4 Mouse: device is a pointer
[    44.452] (II) event5  - ASUE1A01:00 04F3:31D4 Mouse: device removed
[    44.452] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-2/i2c-ASUE1A01:00/0018:04F3:31D4.0001/input/input7/event5"
[    44.452] (II) XINPUT: Adding extended input device "ASUE1A01:00 04F3:31D4 Mouse" (type: MOUSE, id 12)
[    44.452] (**) Option "AccelerationScheme" "none"
[    44.452] (**) ASUE1A01:00 04F3:31D4 Mouse: (accel) selected scheme none/0
[    44.452] (**) ASUE1A01:00 04F3:31D4 Mouse: (accel) acceleration factor: 2.000
[    44.452] (**) ASUE1A01:00 04F3:31D4 Mouse: (accel) acceleration threshold: 4
[    44.452] (II) event5  - ASUE1A01:00 04F3:31D4 Mouse: is tagged by udev as: Mouse Pointingstick
[    44.452] (II) event5  - ASUE1A01:00 04F3:31D4 Mouse: device is a pointer
[    44.453] (II) config/udev: Adding input device ASUE1A01:00 04F3:31D4 Mouse (/dev/input/mouse0)
[    44.453] (II) No input driver specified, ignoring this device.
[    44.453] (II) This device may have been added with another device file.
[    44.454] (II) config/udev: Adding input device ASUE1A01:00 04F3:31D4 Touchpad (/dev/input/event6)
[    44.454] (**) ASUE1A01:00 04F3:31D4 Touchpad: Applying InputClass "libinput touchpad catchall"
[    44.454] (II) Using input driver 'libinput' for 'ASUE1A01:00 04F3:31D4 Touchpad'
[    44.454] (II) systemd-logind: got fd for /dev/input/event6 13:70 fd 54 paused 0
[    44.454] (**) ASUE1A01:00 04F3:31D4 Touchpad: always reports core events
[    44.454] (**) Option "Device" "/dev/input/event6"
[    44.455] (II) event6  - ASUE1A01:00 04F3:31D4 Touchpad: is tagged by udev as: Touchpad
[    44.455] (II) event6  - ASUE1A01:00 04F3:31D4 Touchpad: device is a touchpad
[    44.456] (II) event6  - ASUE1A01:00 04F3:31D4 Touchpad: device removed
[    44.456] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-2/i2c-ASUE1A01:00/0018:04F3:31D4.0001/input/input8/event6"
[    44.456] (II) XINPUT: Adding extended input device "ASUE1A01:00 04F3:31D4 Touchpad" (type: TOUCHPAD, id 13)
[    44.457] (**) Option "AccelerationScheme" "none"
[    44.457] (**) ASUE1A01:00 04F3:31D4 Touchpad: (accel) selected scheme none/0
[    44.457] (**) ASUE1A01:00 04F3:31D4 Touchpad: (accel) acceleration factor: 2.000
[    44.457] (**) ASUE1A01:00 04F3:31D4 Touchpad: (accel) acceleration threshold: 4
[    44.457] (II) event6  - ASUE1A01:00 04F3:31D4 Touchpad: is tagged by udev as: Touchpad
[    44.458] (II) event6  - ASUE1A01:00 04F3:31D4 Touchpad: device is a touchpad
[    44.458] (II) config/udev: Adding input device ASUE1A01:00 04F3:31D4 Touchpad (/dev/input/mouse1)
[    44.458] (II) No input driver specified, ignoring this device.
[    44.458] (II) This device may have been added with another device file.
[    44.459] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    44.459] (II) No input driver specified, ignoring this device.
[    44.459] (II) This device may have been added with another device file.
[    44.459] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[    44.459] (II) No input driver specified, ignoring this device.
[    44.459] (II) This device may have been added with another device file.
[    44.459] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event13)
[    44.459] (II) No input driver specified, ignoring this device.
[    44.459] (II) This device may have been added with another device file.
[    44.459] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=8 (/dev/input/event14)
[    44.459] (II) No input driver specified, ignoring this device.
[    44.459] (II) This device may have been added with another device file.
[    44.459] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=9 (/dev/input/event15)
[    44.459] (II) No input driver specified, ignoring this device.
[    44.459] (II) This device may have been added with another device file.
[    44.460] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=10 (/dev/input/event16)
[    44.460] (II) No input driver specified, ignoring this device.
[    44.460] (II) This device may have been added with another device file.
[    44.460] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=11 (/dev/input/event17)
[    44.460] (II) No input driver specified, ignoring this device.
[    44.460] (II) This device may have been added with another device file.
[    44.460] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=12 (/dev/input/event18)
[    44.460] (II) No input driver specified, ignoring this device.
[    44.460] (II) This device may have been added with another device file.
[    44.460] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=13 (/dev/input/event19)
[    44.460] (II) No input driver specified, ignoring this device.
[    44.460] (II) This device may have been added with another device file.
[    44.460] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=14 (/dev/input/event20)
[    44.460] (II) No input driver specified, ignoring this device.
[    44.460] (II) This device may have been added with another device file.
[    44.460] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=15 (/dev/input/event21)
[    44.460] (II) No input driver specified, ignoring this device.
[    44.460] (II) This device may have been added with another device file.
[    44.461] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=16 (/dev/input/event22)
[    44.461] (II) No input driver specified, ignoring this device.
[    44.461] (II) This device may have been added with another device file.
[    44.461] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=17 (/dev/input/event23)
[    44.461] (II) No input driver specified, ignoring this device.
[    44.461] (II) This device may have been added with another device file.
[    44.461] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event4)
[    44.461] (**) Asus WMI hotkeys: Applying InputClass "libinput keyboard catchall"
[    44.461] (II) Using input driver 'libinput' for 'Asus WMI hotkeys'
[    44.461] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 55 paused 0
[    44.461] (**) Asus WMI hotkeys: always reports core events
[    44.461] (**) Option "Device" "/dev/input/event4"
[    44.462] (II) event4  - Asus WMI hotkeys: is tagged by udev as: Keyboard
[    44.462] (II) event4  - Asus WMI hotkeys: device is a keyboard
[    44.462] (II) event4  - Asus WMI hotkeys: device removed
[    44.462] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input6/event4"
[    44.462] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 14)
[    44.462] (**) Option "xkb_model" "pc105"
[    44.462] (**) Option "xkb_layout" "us"
[    44.462] (II) event4  - Asus WMI hotkeys: is tagged by udev as: Keyboard
[    44.463] (II) event4  - Asus WMI hotkeys: device is a keyboard
[    44.463] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    44.463] (**) AT Translated Set 2 keyboard: Applying InputClass "libinput keyboard catchall"
[    44.463] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[    44.463] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 56 paused 0
[    44.463] (**) AT Translated Set 2 keyboard: always reports core events
[    44.463] (**) Option "Device" "/dev/input/event3"
[    44.464] (II) event3  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[    44.464] (II) event3  - AT Translated Set 2 keyboard: device is a keyboard
[    44.464] (II) event3  - AT Translated Set 2 keyboard: device removed
[    44.464] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    44.464] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 15)
[    44.464] (**) Option "xkb_model" "pc105"
[    44.464] (**) Option "xkb_layout" "us"
[    44.465] (II) event3  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[    44.465] (II) event3  - AT Translated Set 2 keyboard: device is a keyboard
[    44.542] (II) modeset(0): EDID vendor "SDC", prod id 16733
[    44.542] (II) modeset(0): Printing DDC gathered Modelines:
[    44.542] (II) modeset(0): Modeline "3840x2400"x0.0  572.01  3840 3872 3880 3920  2400 2408 2416 2432 +hsync -vsync (145.9 kHz eP)
[    44.547] (II) modeset(0): EDID vendor "SDC", prod id 16733
[    44.547] (II) modeset(0): Printing DDC gathered Modelines:
[    44.547] (II) modeset(0): Modeline "3840x2400"x0.0  572.01  3840 3872 3880 3920  2400 2408 2416 2432 +hsync -vsync (145.9 kHz eP)
[    44.549] (II) modeset(0): EDID vendor "SDC", prod id 16733
[    44.549] (II) modeset(0): Printing DDC gathered Modelines:
[    44.549] (II) modeset(0): Modeline "3840x2400"x0.0  572.01  3840 3872 3880 3920  2400 2408 2416 2432 +hsync -vsync (145.9 kHz eP)
[    44.553] (II) modeset(0): EDID vendor "SDC", prod id 16733
[    44.554] (II) modeset(0): Printing DDC gathered Modelines:
[    44.554] (II) modeset(0): Modeline "3840x2400"x0.0  572.01  3840 3872 3880 3920  2400 2408 2416 2432 +hsync -vsync (145.9 kHz eP)
[    44.558] (II) modeset(0): EDID vendor "SDC", prod id 16733
[    44.558] (II) modeset(0): Printing DDC gathered Modelines:
[    44.558] (II) modeset(0): Modeline "3840x2400"x0.0  572.01  3840 3872 3880 3920  2400 2408 2416 2432 +hsync -vsync (145.9 kHz eP)
[    44.846] (II) modeset(0): Allocate new frame buffer 320x200 stride
[    44.849] (II) modeset(0): Allocate new frame buffer 3840x2400 stride
[    46.042] (II) modeset(0): EDID vendor "SDC", prod id 16733
[    46.042] (II) modeset(0): Printing DDC gathered Modelines:
[    46.042] (II) modeset(0): Modeline "3840x2400"x0.0  572.01  3840 3872 3880 3920  2400 2408 2416 2432 +hsync -vsync (145.9 kHz eP)
```

---

### Post by Bashing-om on 2022-05-27
guine; Well

Xorg too appears to be in a happy state.

I do not know at this point where else to look for a fault.

I might suggest that you open another terminal and in this terminal watch what the system is doing:
in this new terminal execute
```

journalctl -f

```
key combo ctl+c to quit the journal's output

Might be able to catch the event prior to the failure,

[INDENT][INDENT]sometimes I just do not know
[/INDENT][/INDENT]

---

### Post by guine on 2022-05-27
Got that running to to see if anything shows up there. And who knows, maybe getting dkms installed may have been the missing piece as well. I'll post if theres any updates. Thanks for all the help, I probably would have just bailed on this install and tried over from scratch by now if I had been on my own.

---

### Post by Bashing-om on 2022-05-28
guine; He he he ...

yeah
> 
bailed on this install and tried over from scratch


did that a few times over the years - ---
I have learned how not to break my 'buntu :D

[INDENT]all in the process of learning
[/INDENT]

---

