---
title: "Problems on updating hardy - dpkg was interrupted"
date: 2008-06-03
forum: General Help
---

### Post by rainefan on 2008-06-03
Hi ppl...I'm having serious problem in updating my system. I use Ubuntu Hardy 32bit. On update manager this error:

"[I]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I]"

On shell:
$sudo dpkg --configure -a
[I]
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24.3-custom
Cannot find /lib/modules/2.6.24.3-custom
update-initramfs: failed for /boot/initrd.img-2.6.24.3-custom
dpkg: subprocess post-installation script returned error exit status 1[/I]

What can I do? Is any way to fix this and update normally?

Tnx! Kind regards,
Raine

---

### Post by rainefan on 2008-06-03
OK...making some tests..I found a possible workaround. Do this on console (shell):

Before doing the next step, use last/old working /boot/grub/menu.lst config available. In other words, just not edit anything else from your grub config :D
$ sudo update-grub

$ sudo gedit /etc/initramfs-tools/update-initramfs.conf

Change 'update_initramfs=yes' line to 'update_initramfs=no'
Save changes and exit.

$ sudo dpkg --configure -a

Just update your system as usual (mine is via 'Update Manager')

Again, go to shell and do:
$ sudo dpkg --configure -a

Just to ensure that no error log is output. Edit again update-initramfs.conf:

$ sudo gedit /etc/initramfs-tools/update-initramfs.conf
Change line 'update_initramfs=no' to 'update_initramfs=yes'
Save changes and exit.

That's it.

PD1: If you want, you can in Update Manager do a CHECK if there is any other new update to ensure your system is consistent.

PD2: Please, if there is anyone with a similar problem, can you just confirm if this could be a bug?

Regards,
Raine

---

### Post by giorgio80 on 2008-06-07
I had the same problem, rainefan slution look to work well. thanks!!

---

### Post by jonolumb on 2008-08-20
Thanks so much, sorted all my issues out too!

---

### Post by corbcox on 2008-08-21
This worked for me also.  Have been trying for several days to resolve.  A thousand thanks for your solution.

---

### Post by SunnyFloorSunny on 2008-11-01
I tried the workaround and I still got the error.

---

