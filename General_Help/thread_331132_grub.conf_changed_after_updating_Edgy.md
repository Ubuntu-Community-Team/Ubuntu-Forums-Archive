---
title: "grub.conf changed after updating Edgy?"
date: 2007-01-04
forum: General Help
---

### Post by sk8er3810 on 2007-01-04
I finally turned on my Edgy machine after a 2 months. It booted perfectly fine.  Then I ran the update manager and rebooted.  Only one problem, it wouldn't.  Short story is my grub.conf file had changed from root (hd0,0) to root (hd0,1) and root=/dev/sda1 to root=/dev/hda2.  I've fixed the problem but is this a bug or did someone mess with my computer?

---

### Post by Bigbluecat on 2007-01-04
I had something similar with a Kernel upgrade. 

To avoid this open your menu.lst file in the grub folder and set the default root drive.

First backup /boot/grub/menu.lst

Then open menu.lst in your preferred editor.

Look for the line that says "Default grub root device" and set it appropriately.

For reference here is my section:

> ## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)In this case my default root is (hd2,0)

---

### Post by kEinstein on 2007-01-04
I experienced the same issue after installing the latest kernel update. The update procedure added some lines, using the same kernel parameters (indeed, the same kernel) except for the default root device: hd0,8 instead of hd0,0. Actually, hd0,8 is in the middle of nowhere. :-k 
Thank you for the hint...

---

### Post by Bigbluecat on 2007-01-04
KEinstein,

There is another section you may wish to adjust. Kopt sets the default location for the kernel. With EDGY it is not so easy to read. I set mine with Dapper and it used the conventional /dev/sda nomenclature. Now it uses UUID. You should be able to copy the appropriate UUID from the automagic section.

Again for reference mine is pasted below and don't forget to backup menu.lst before making changes just in case.

> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=43e559ee-40c1-4aaa-9a74-f9c17dd835a6 roLastly if you are dual booting as I am I also set updatedefaultentry to true. My default is windows for my wife to use. When kernel updates are added it can change the boot count as my default is not entry 0. If your default boot kernel is the first entry then you do not need to worry about this.

> ## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

---

### Post by kEinstein on 2007-01-04
@Bigbluecat: Thanks a lot for your post! Now that I understand the reason for grub's behavior, I implemented your suggestions.
Waiting for a kernel update :D

Cheers!

---

