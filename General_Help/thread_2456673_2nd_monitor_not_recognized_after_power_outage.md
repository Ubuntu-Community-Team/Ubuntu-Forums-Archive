---
title: "2nd monitor not recognized after power outage"
date: 2021-01-16
forum: General Help
---

### Post by NertSkull on 2021-01-16
Everything was working, then had a power outage at home.  When I reboot, only one monitor is recognized.

I uninstalled and reinstalled the nvidia proprietary (460) drivers and still the same. Also checked while just using nouveau and still just one monitor.

I'm running kernel 5.4.0-56-generic on kubuntu 20.04.  If I boot into an old kernel (5.4.0-42-generic) then BOTH monitors DO work.  

But in that kernel it appears my nfs mounts didn't mount, don't know why.  When I tried to force mount them with sudo mount -a I got this error:

mount: /boot: cannot mount; probably corrupted filesystem on /dev/sda2.
mount: /boot/efi: mount point does not exist.

I rebooted into the 56 kernel, and my nfs mounts all mount.  But no 2nd monitor.  But I tried mount -a again to see, and I still get the same error in the newer kernel as well. So that may just be a red herring.

Either way, I tried running

```
sudo dosfsck -w -r -l -a -v -t /dev/sda2
```

But that didn't fix anything after a reboot.

If I run sudo lshw -C display I get this :

```
  *-display                 
       description: VGA compatible controller
       product: GM200 [GeForce GTX 980 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:c0000-dffff

```
It doesn't recognize the other one.

Obviously the card/monitor still work.  Because they work in the old kernel. Plus I dual boot, and everything is exactly the same (2 monitors) when I boot into windows.  So I'm pretty sure it's not a hardware issue.  Some setting somewhere got broke. 

What can I do to troubleshoot/fix?

---

### Post by TheFu on 2021-01-16
```
mount: /boot: cannot mount; probably corrupted filesystem on /dev/sda2.
mount: /boot/efi: mount point does not exist.
```
Seems /dev/sda2 needs an fsck run from alternate boot media.
I'd also force the last kernel to be reinstalled and force an initrd-update.

My sda2 is an ext2 file system.
```
Filesystem                            Type  Size  Used Avail Use% Mounted on
/dev/sda2                             ext2  721M  149M  536M  22% /boot
/dev/sda1                             vfat  511M  3.7M  508M   1% /boot/efi

```

While you are looking at this stuff, check that /boot didn't get filled. May want to manually "purge" older kernels. For most people, there isn't much need to keep more than 2-3 kernels.  On some systems, my /boot/ using the old defaults is much too tiny. I'm always having to be careful before any new kernel gets installed.   500MB or a little larger seems to be the happy point these days so kernels don't need to be purged all the time.

Those are the ideas I have.

---

### Post by NertSkull on 2021-01-16
Ok, I booted a live CD and fixed the /boot issues with fsck.  Now that's fine with no errors. And my /boot is 1.1 G and 18% used, so not a running out of space issue.

Still have the same issues with the 2nd monitor not being recognized.

I tried reinstalling the latest kernel

[FONT=monospace][COLOR=#000000]sudo apt install --reinstall linux-image-generic linux-image-5.4.0-56-generic
[FONT=monospace][COLOR=#000000]sudo update-initramfs -u[/COLOR]
sudo update-grub[/FONT]
[/COLOR]
Now it freezes on boot when loading the with the 56 kernel.  And if I boot into the old 42 kernel, my nfs volumes don't mount now (which they did earlier in the old 42 kernel before trying to update). I also noticed it doesn't find my sound drivers and have no audio (that could have been happening before the kernel update on the new kernel as well, I just didn't ever look).

But in the 42 kernel I DO still get both monitors working.  

I'm afraid I'm feeling a reinstall from scratch coming on.
[/FONT]

---

### Post by TheFu on 2021-01-16
kernels have a package name.  Any file tied to the kernel should lead you back to the package name.

For example:
```
hadar:/boot$ ls
config-4.15.0-129-generic      lost+found/
config-4.15.0-132-generic      System.map-4.15.0-129-generic
grub/                          System.map-4.15.0-132-generic
initrd.img-4.15.0-129-generic  vmlinuz-4.15.0-129-generic
initrd.img-4.15.0-132-generic  vmlinuz-4.15.0-132-generic
initrd.img-4.15.0-70-generic
```

The vmlinuz files are part of the kernel.
```
hadar:/boot$ dpkg -S vmlinuz-4.15.0-129-generic
linux-image-4.15.0-129-generic: /boot/vmlinuz-4.15.0-129-generic
```

So the name of the kernel package to reinstall on that system is **linux-image-4.15.0-129-generic**. The command for that is:
```
sudo apt install --reinstall linux-image-4.15.0-129-generic
```

Your answer will almost certainly be different and the most recent vmlin* file is probably the corrupted.

There are other ways to get to the same place.  I think aptitude will let you reinstall a package from a list of installed ones. Synaptic probably will too.

---

### Post by TheFu on 2021-01-16
On 20.04, I have vmlinuz-5.4.0-60-generic and vmlinuz-5.4.0-62-generic, so you are a ways out of patching.  My 20.04 system doesn't have problems with any NFS mounts from either 16.04 or 18.04 NFS servers:

```
$ df -Th
Filesystem                      Type  Size  Used Avail Use% Mounted on
istar:/TV                       nfs4  294G  101G  193G  35% /TV
istar:/d/D1                     nfs4  3.5T  3.5T   25G 100% /d/D1
istar:/d/D2                     nfs4  3.6T  3.5T   15G 100% /d/D2
istar:/d/D3                     nfs4  3.6T  3.6T   13G 100% /d/D3
romulus:/Data/r2                nfs4  1.3T  1.2T   67G  95% /S
romulus:/raid/media             nfs4  1.8T  1.7T   17G 100% /R
```

---

### Post by NertSkull on 2021-01-16
Ok, I tried

```
cd /boot
[FONT=monospace][COLOR=#000000]sudo dpkg -S vmlinuz-5.4.0-56-generic[/COLOR][/FONT]
```[FONT=monospace]
[/FONT]
That seemed to work fine.

Then tried this again (slightly different than what I did above
[FONT=monospace][COLOR=#000000]
```
sudo apt install --reinstall linux-image-5.4.0-56-generic[/COLOR]
```
[/FONT]
However I get this output:

```

[FONT=monospace][COLOR=#000000]eading package lists... Done [/COLOR]
Building dependency tree        
Reading state information... Done 
Reinstallation of linux-image-5.4.0-56-generic is not possible, it cannot be downloaded. 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I'm not sure why it can't be downloaded. I'm obviously on the internet posting this from the same computer, so it's not a connectivity issue.

Also, when I boot into the 56 image, it hangs at 

unattended-upgrades.service

Don't know if that's important.[/FONT]

---

### Post by TheFu on 2021-01-16
```
$ ll /boot/vmlinuz*
lrwxrwxrwx 1 root root       24 Jan 16 15:18 /boot/vmlinuz -> vmlinuz-5.4.0-62-generic
-rw------- 1 root root 11682560 Dec  9 02:30 /boot/vmlinuz-5.4.0-58-generic
-rw------- 1 root root 11686656 Jan  6 05:55 /boot/vmlinuz-5.4.0-60-generic
-rw------- 1 root root 11686656 Jan 12 07:01 /boot/**vmlinuz-5.4.0-62-generic**

$ lsb_release -d
Description:    Ubuntu **20.04.1** LTS

```

So it appears you haven't patched since before Dec 9th!  
I only patch on Saturdays. 
I never allow any automatic patching. I've been burned before and left with an unworking production system.

Why do you have vmlinuz-5.4.0-56-generic still?

---

### Post by NertSkull on 2021-01-16
I don't know.  I've just been running apt update and apt upgrade at times.

```

[FONT=monospace][COLOR=#000000]ll /boot/vmlinuz* [/COLOR]
lrwxrwxrwx 1 root root       24 Dec  8 12:25 [COLOR=#54ffff]**/boot/vmlinuz**[/COLOR][COLOR=#000000] -> vmlinuz-5.4.0-56-generic [/COLOR]
-rw-r--r-- 1 root root 11662080 Jul 31 12:42 /boot/vmlinuz-5.4.0-42-generic 
-rw------- 1 root root 11682560 Nov 23 13:10 /boot/vmlinuz-5.4.0-56-generic 
lrwxrwxrwx 1 root root       24 Dec  8 12:25 [COLOR=#54ffff]**/boot/vmlinuz.old**[/COLOR][COLOR=#000000] -> vmlinuz-5.4.0-42-generic[/COLOR]

lsb_release -d
Description:    Ubuntu 20.04.1 LTS

```
[/FONT]
My system says all packages are up to date.

Is there a way to force to 62?  Because right now it thinks I'm up to date on 56

---

### Post by TheFu on 2021-01-16
try running:
```
sudo apt update
sudo apt full-upgrade
```

System Maintenance for Linux PCs
[https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)
This was republished by a well-known website. I've kept it updated over the years, mostly.

---

### Post by NertSkull on 2021-01-16
[FONT=monospace][COLOR=#000000]```

sudo apt full-upgrade  
```[/COLOR]```

Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Calculating upgrade... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


And I ran an apt update before that
[/FONT]

---

### Post by TheFu on 2021-01-16
Is /etc/apt/sources.list funky? Mine:
```

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse
```

Only PPA is x2go-ubuntu-stable-focal.list - that's for remote NX GUI access.

---

### Post by NertSkull on 2021-01-16
This is mine

```

[FONT=monospace][COLOR=#000000]cat /etc/apt/sources.list [/COLOR]
# deb cdrom:[Kubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731)]/ focal main multiverse restricted universe 

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to 
# newer versions of the distribution. 
deb http://us.archive.ubuntu.com/ubuntu/ focal main restricted 
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal main restricted 

## Major bug fix updates produced after the final release of the 
## distribution. 
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted 
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team. Also, please note that software in universe WILL NOT receive any 
## review or updates from the Ubuntu security team. 
deb http://us.archive.ubuntu.com/ubuntu/ focal universe 
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal universe 
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates universe 
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
## team, and may not be under a free licence. Please satisfy yourself as to  
## your rights to use the software. Also, please note that software in  
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
deb http://us.archive.ubuntu.com/ubuntu/ focal multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-updates multiverse 

## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
deb http://us.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse 

## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. 
## This software is not part of Ubuntu, but is offered by Canonical and the 
## respective vendors as a service to Ubuntu users. 
# deb http://archive.canonical.com/ubuntu focal partner 
# deb-src http://archive.canonical.com/ubuntu focal partner 

deb http://security.ubuntu.com/ubuntu focal-security main restricted 
# deb-src http://security.ubuntu.com/ubuntu focal-security main restricted 
deb http://security.ubuntu.com/ubuntu focal-security universe 
# deb-src http://security.ubuntu.com/ubuntu focal-security universe 
deb http://security.ubuntu.com/ubuntu focal-security multiverse 
# deb-src http://security.ubuntu.com/ubuntu focal-security multiverse 

# This system was installed using small removable media 
# (e.g. netinst, live or single CD). The matching "deb cdrom" 
# entries were disabled at the end of the installation process. 
# For information about how to configure apt package sources, 
# see the sources.list(5) manual. 

```

and without comments for easier reading

```

[FONT=monospace][COLOR=#000000]cat /etc/apt/sources.list [/COLOR]
deb http://us.archive.ubuntu.com/ubuntu/ focal main restricted 
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted 
deb http://us.archive.ubuntu.com/ubuntu/ focal universe 
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates universe 
deb http://us.archive.ubuntu.com/ubuntu/ focal multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse 
deb http://security.ubuntu.com/ubuntu focal-security main restricted 
deb http://security.ubuntu.com/ubuntu focal-security universe 
deb http://security.ubuntu.com/ubuntu focal-security multiverse 
[/FONT]
```

[/FONT]

---

### Post by TheFu on 2021-01-17
We've exceeded my skills. sorry.

---

