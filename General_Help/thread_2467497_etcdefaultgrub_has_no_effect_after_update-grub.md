---
title: "/etc/default/grub has no effect after update-grub"
date: 2021-09-28
forum: General Help
---

### Post by philchambers on 2021-09-28
I have a desktop and laptop both with 18.04. /etc/default/grub and the files in /etc/grub.d are identical on both.

The desktop is fine and boots straight to ubuntu but the laptop always puts up the grub menu at boot and waits 10 seconds. After stripping all comments /etc/default/grub is:

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

I have tried changing various values and always do 'sudo update-grub' but nothing has any effect on the laptop behaviour!

I am at a loss as to what is wrong.

---

### Post by ajgreeny on 2021-09-28
Let's start by checking what OS partitions you have in both machines by running the terminal command ```
sudo fdisk -l
``` which will show us all the partitions on the disk or disks you have and any differences may help us figure out why there is a different behaviour showing in the two computers.

Are there any other differences in the /etc/default/grub files in the two machines or are they otherwise identical as well as those 6 lines you show.

---

### Post by grahammechanical on 2021-09-28
GRUB_DEFAULT=0 means the first OS in grub.cfg is the default OS. GRUB_TIMEOUT=0 means boot the default OS without any time delay. It effectively prevents the Grub boot menu for displaying. Or, it should do that.

Ubuntu defaults to having GRUB_TIMEOUT=10 when there is more than one OS on the machine. It in effect means show the Grub menu for 10 seconds and then boot the default OS. Actually it is the grub-mkconfig script that sets both GRUB_DEFAULT and GRUB_TIMEOUT. Ubuntu has a script called update-grub that calls grub-mkconfig to be run.

As you know, with GRUB_TIMEOUT=0 there should be no delay in booting Ubuntu and the Grub boot menu should not appear. Unless there is a backup copy that has a different setting or your changes to /etc/default/grub are not being saved. I cannot think of any other cause.

Regards

---

### Post by ajgreeny on 2021-09-29
Are both machines using BIOS, UEFI, or do you have one of each?

---

