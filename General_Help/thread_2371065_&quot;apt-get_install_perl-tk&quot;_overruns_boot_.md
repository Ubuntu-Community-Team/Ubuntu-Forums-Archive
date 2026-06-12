---
title: "&quot;apt-get install perl-tk&quot; overruns /boot with plural firmwares"
date: 2017-09-10
forum: General Help
---

### Post by aplonis2 on 2017-09-10
When calling "apt-get install perl-tk", even when add "=1:804.033-1build1" thinking to constrain the version to Xenial, still it will over-run /boot for insisting to install plural firmwares (of which I absolutely require only 4.4.0-93-generic. It tells me this is happening like so...

Setting up linux-firmware (1.157.12) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-93-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-83-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-123-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-107-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-85-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-53-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-44-generic


So next I ran...
```
sudo rm /boot/*-3*
```
...to delete the bulk of unused and recover that space, followed by...
```
sudo apt autoremove --purge
```
...which only remade all those same files again, once more failing when it over-ran /boot.

I read somewhere, that this would provide useful info...
```
dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+' | grep -Fv $(uname -r)
pi  linux-image-3.13.0-107-generic 3.13.0-107.154      amd64     Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-123-generic 3.13.0-123.172      amd64     Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-32-generic  3.13.0-32.57   amd64     Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-44-generic  3.13.0-44.73   amd64     Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-53-generic  3.13.0-53.89   amd64     Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-85-generic  3.13.0-85.129  amd64     Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-83-generic   4.4.0-83.106   amd64     Linux kernel image for version 4.4.0 on 64 bit x86 SMP
```

...but I don't know quite what to make of it, myself.

Thus my question is: how to prevent such /boot over-runs, particularly how to obtain perl-tk and not over-run /boot?

Info: this is on a Dell Vostro 1520 with a 250GB SSD and the whole installation is encrypted with LUKS. The install was from an ISO originally, as 14.04 LTS then later updated to 16.04 LTS via the built-in updater. I'm hoping to avoid the pain of having to Clonezilla the whole encrypted SSD and then run GParted to expand /boot only because these out-of-date firmwares (which I'd only later delete in any case) get installed via apt-get for no very obvious reason.

---

### Post by ajgreeny on 2017-09-10
Unless you know exactly what you're doing you should **never remove any files from /boot using the rm command** as you did; doing so may make the package management system very confused and unstable, which may be why the autoremove command did not apparently work as it should, leaving just two kernels in the system.

As you are using the 16.04 version now you do not need any 3.13 kernels, and if the autoremove command is not removing them it could be a result of your rm command making the kernels corrupt and not removable due to missing files; do you get any error messages related to kernels when running autoremove?

You may now find the easiest way to remove the kernels no longer needed is to use synaptic package manager, searching by name only for **-3.13.0-** which may show the **linux-image** and **linux-headers** packages, but even that may fail.  Try this and come back again if you get any errors, showing us exactly what those errors are.

---

### Post by aplonis2 on 2017-09-10
Thank you! The Synmaptic Package Manager was indeed what I needed. It allowed me to remove kernels one at a time, without trying to update the entire lot first. I did get an error while trying to install SNP itself, but nevertheless it came up, I tried it as-was, and all seemed to work. 

I shall heed your advice on -rm in the future.

---

### Post by ajgreeny on 2017-09-11
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

