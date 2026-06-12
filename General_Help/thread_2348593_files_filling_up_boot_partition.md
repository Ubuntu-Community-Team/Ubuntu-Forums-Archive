---
title: "files filling up /boot partition"
date: 2017-01-05
forum: General Help
---

### Post by Steve_Kellett on 2017-01-05
I'm also stymied by this same problem which started occurring about a month ago. Previously I simply cleared out my boot directory by "sudo rm" for the images I no longer required.

I'm using Ubuntu 16.10 and my **dpkg -l linux-image*** output is as follows:

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-image    <none>       <none>       (no description available)
un  linux-image-3. <none>       <none>       (no description available)
rc  linux-image-3. 3.11.0-12.19 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.11.0-13.20 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.11.0-14.21 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.11.0-15.25 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.11.0-17.31 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.11.0-18.32 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.11.0-19.33 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.13.0-24.47 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-27.50 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-29.53 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-30.55 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-32.57 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-33.58 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-34.60 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-35.62 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-36.63 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-37.64 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-39.66 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-40.69 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-43.72 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-44.73 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-45.74 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-46.79 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-48.80 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-49.83 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-51.84 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-52.86 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-53.89 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-54.91 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-55.94 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-57.95 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-58.97 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-59.98 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-61.10 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-62.10 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-63.10 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-65.10 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-66.10 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-67.11 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-68.11 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-71.11 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.13.0-74.11 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-76.12 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-77.12 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-79.12 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-83.12 i386         Linux kernel image for version 3.
rc  linux-image-3. 3.5.0-17.28  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.5.0-23.35  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.5.0-24.37  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.5.0-25.39  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.5.0-26.42  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.5.0-27.46  i386         Linux kernel image for version 3.
ii  linux-image-3. 3.5.0-30.51  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.8.0-21.32  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.8.0-22.33  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.8.0-23.34  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.8.0-25.37  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.8.0-26.38  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.8.0-27.40  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.8.0-29.42  i386         Linux kernel image for version 3.
rc  linux-image-3. 3.8.0-30.44  i386         Linux kernel image for version 3.
ii  linux-image-3. 3.8.0-31.46  i386         Linux kernel image for version 3.
rc  linux-image-4. 4.2.0-34.39  i386         Linux kernel image for version 4.
rc  linux-image-4. 4.2.0-35.40  i386         Linux kernel image for version 4.
rc  linux-image-4. 4.2.0-36.41  i386         Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-22.40  i386         Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-24.43  i386         Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-28.47  i386         Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-31.50  i386         Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-34.53  i386         Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-36.55  i386         Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-38.57  i386         Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-43.63  i386         Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-45.66  i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-47.68  i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-53.74  i386         Linux kernel image for version 4.
rc  linux-image-ex 3.11.0-12.19 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.11.0-13.20 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.11.0-14.21 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.11.0-15.25 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.11.0-17.31 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.11.0-18.32 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.11.0-19.33 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.13.0-24.47 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-27.50 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-29.53 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-30.55 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-32.57 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-33.58 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-34.60 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-35.62 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-36.63 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-37.64 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-39.66 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-40.69 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-43.72 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-44.73 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-45.74 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-46.79 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-48.80 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-49.83 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-51.84 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-52.86 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-53.89 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-54.91 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-55.94 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-57.95 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-58.97 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-59.98 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-61.10 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-62.10 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-63.10 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-65.10 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-66.10 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-67.11 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-68.11 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-71.11 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.13.0-74.11 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-76.12 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-77.12 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-79.12 i386         Linux kernel extra modules for ve
ii  linux-image-ex 3.13.0-83.12 i386         Linux kernel extra modules for ve
rc  linux-image-ex 3.5.0-17.28  i386         Linux kernel image for version 3.
rc  linux-image-ex 3.5.0-23.35  i386         Linux kernel image for version 3.
rc  linux-image-ex 3.5.0-24.37  i386         Linux kernel image for version 3.
rc  linux-image-ex 3.5.0-25.39  i386         Linux kernel image for version 3.
rc  linux-image-ex 3.5.0-26.42  i386         Linux kernel image for version 3.
rc  linux-image-ex 3.5.0-27.46  i386         Linux kernel image for version 3.
ii  linux-image-ex 3.5.0-30.51  i386         Linux kernel image for version 3.
rc  linux-image-ex 3.8.0-21.32  i386         Linux kernel image for version 3.
rc  linux-image-ex 3.8.0-22.33  i386         Linux kernel image for version 3.
rc  linux-image-ex 3.8.0-23.34  i386         Linux kernel image for version 3.
rc  linux-image-ex 3.8.0-25.37  i386         Linux kernel image for version 3.
rc  linux-image-ex 3.8.0-26.38  i386         Linux kernel image for version 3.
rc  linux-image-ex 3.8.0-27.40  i386         Linux kernel image for version 3.
rc  linux-image-ex 3.8.0-29.42  i386         Linux kernel image for version 3.
rc  linux-image-ex 3.8.0-30.44  i386         Linux kernel image for version 3.
ii  linux-image-ex 3.8.0-31.46  i386         Linux kernel image for version 3.
rc  linux-image-ex 4.2.0-34.39  i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.2.0-35.40  i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.2.0-36.41  i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-22.40  i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-24.43  i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-28.47  i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-31.50  i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-34.53  i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-36.55  i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-38.57  i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-43.63  i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-45.66  i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-47.68  i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-53.74  i386         Linux kernel extra modules for ve
ii  linux-image-ge 4.4.0.53.56  i386         Generic Linux kernel image
```

If I attempt to use "sudo apt-get autoremove" I get the following:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 34 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.122ubuntu8.5) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-firmware (1.157.6) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-47-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-83-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-79-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-77-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-76-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-74-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_Wnx3hq/lib/modules/3.13.0-74-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_Wnx3hq/lib/modules/3.13.0-74-generic/modules.builtin: No such file or directory
update-initramfs: Generating /boot/initrd.img-3.13.0-71-generic


gzip: stdout: No space left on device
E: mkinitramfs failure find 141 cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-71-generic with 1.
dpkg: error processing package linux-firmware (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for initramfs-tools (0.122ubuntu8.5) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic


gzip: stdout: No space left on device
E: mkinitramfs failure find 141 cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-53-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-firmware
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any help appreciated. I'm using LVM because I originally set this up as a multiple OS machine. I'm on the verge of backing up my data and doing a clean install!

---

### Post by ajgreeny on 2017-01-05
*Post moved to its own thread**General Help**.* which is more appropriate for the problem as may not be exactly the same as the thread you added it to, and could therefore be confusing for both of you.

You have more kernels shown as still installed than I think I have ever seen before; 33 in total, but having already removed old initrd-images manually you may find that dpkg commands will not work, though I have never been in this position before.
```
ii  linux-image-3. 3.13.0-27.50 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-29.53 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-30.55 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-32.57 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-33.58 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-34.60 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-35.62 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-36.63 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-37.64 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-39.66 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-40.69 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-43.72 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-44.73 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-45.74 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-46.79 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-48.80 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-49.83 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-51.84 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-52.86 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-53.89 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-54.91 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-55.94 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-57.95 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-58.97 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-59.98 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-61.10 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-62.10 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-63.10 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-65.10 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-66.10 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-67.11 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-68.11 i386         Linux kernel image for version 3.
ii  linux-image-3. 3.13.0-71.11 i386         Linux kernel image for version 3.
```
Let's start with a test command ```
sudo dpkg -P  linux-image-generic-3.13.0-29 linux-image-extra-3.13.0-29
``` and we'll then move on depending on what that shows.

---

### Post by King of Heart 4711 on 2017-01-05
UbuntuHandbook.org has a nice manual procedure for manually removing old kernels: [http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/)

It's written for 16.04, but the idea will work on any apt/dpkg (read Debian) based system..

Standard disclaimers should be adhered to, not responsible for dataloss, unbootable systems, cats on keyboard, etc. Commands posted are run at your own risk :)


The manual portion below (should the link ever become broken):

[B]Remove Old Kernels via DPKG:
[/B]
 If your /boot partition has already full while doing an upgrade or package install, and apt *(the script above uses apt)*  can’t remove packages due to broken dependency, here you can manually  find out the old kernel packages and remove them via DPKG:
 **1.** Run command to check out current kernel and DON’T REMOVE it:

 ```
uname -r
```

**2.** List all kernels excluding the current booted:

 ```
dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+' | grep -Fv $(uname -r) 
```

Example output:
 ```
[COLOR=red]rc  linux-image-4.4.0-15-generic[/COLOR]               4.4.0-15.31                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
[COLOR=red]ii  linux-image-4.4.0-18-generic[/COLOR]               4.4.0-18.34                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
[COLOR=red]rc  linux-image-4.6.0-040600rc3-generic[/COLOR]        4.6.0-040600rc3.201604120934                        amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP
``` 

There will be three status in the listed kernel images:
 
[LIST]
[*]**rc**: means it has already been removed. 
[*]**ii**: means installed, eligible for removal. 
[*]**iU**: DON’T REMOVE. It means not installed, but queued for install in apt. 
[/LIST]

 **3.** Remove old kernel images in status [COLOR=red]ii[/COLOR], it’s “linux-image-4.4.0-18-generic” in the example above:

 ```
sudo dpkg --purge [COLOR=red]linux-image-4.4.0-18-generic[/COLOR]
``` 

If the command fails, remove the dependency packages that the output tells you via 
```
sudo dpkg --purge PACKAGE.
```

 And also try to remove the respective header and common header packages (Don’t worry if the command fails):

 ```
sudo dpkg --purge [COLOR=red]linux-image-4.4.0-18[/COLOR]-header [COLOR=red]linux-image-4.4.0-18[/COLOR]
``` 

Finally you may fix the apt broken dependency via command:
 ```
sudo apt -f install
```

---

### Post by ian-weisser on 2017-01-05
> **Steve_Kellett said:**
> Previously I simply cleared out my boot directory by "sudo rm" for the images I no longer required.

And now you're going to pay the price for doing that. Sorry.
Every single kernel image package that you try to remove using dpkg or apt will error with 'file not found'
Each time that happens, create a dummy file (using the 'touch' command) for the package manager to remove.

Lesson: Never manually remove files placed by the package manager. Use the package manager for it's intended purpose.

Enabling autoremove will prevent accumulation of old kernels in 14.04 and earlier. A different fix was implemented in 16.04 and later.

---

### Post by Steve_Kellett on 2017-01-12
Thanks for the help.

Unfortunately that test simply resulted in t he following:

sudo dpkg -P  linux-image-generic-3.13.0-29 linux-image-extra-3.13.0-29
[sudo] password for steve: 
dpkg: warning: ignoring request to remove linux-image-generic-3.13.0-29 which isn't installed
dpkg: warning: ignoring request to remove linux-image-extra-3.13.0-29 which isn't installed

Regards - Steve

---

### Post by Steve_Kellett on 2017-01-12
Thanks everyone. Following the procedure outlined in the Ubuntu handbook (Ubuntuhandbook.org) allowed me to tidy up the installed Kernels & dependencies, all be it after running 60+ "dpkg --purge PACKAGE" commands!

Cheers - Steve

---

### Post by jis on 2017-04-10
The UbuntuHandbook article has its substance copied from [this Community Help Wiki page]("https://help.ubuntu.com/community/RemoveOldKernels"), which I have largely edited. (I have edited the article somewhat even after the release of the UbuntuHandbook article.) Instead of (or besides) channeling money to the UbuntuHandbook author Ji m via the dating advertisements on the site, you could consider donating me (on my home page), or you could post a small bounty in [here]("https://www.bountysource.com/issues/38300038-feature-request-the-command-should-work-like-this") to crowdfund a tool - which I have already written - to make kernel removing fast, convenient and more thorough to do even in trickier cases for Ubuntu users.

---

