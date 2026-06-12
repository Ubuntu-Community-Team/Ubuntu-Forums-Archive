---
title: "Dual Boot Ubuntu and Android-x86"
date: 2016-04-09
forum: General Help
---

### Post by Trevor_Owen on 2016-04-09
Lubuntu has given new life to an old netbook, and now I'd like to experiment with Android-x86 by dual booting it on the netbook.  I have followed the directions given in response to posts similar to mine on this and other forums, and installed android-4.4-rc2 in a separate partition /dev/sda8.  I then created /etc/grub.d/40-custom and ran update-grub. Android did not appear in my Grub 2 menu on start-up.  I have tried many tweaks I have found on line without success.

Here is what I added to 40_custom after running sudo gedit /etc/grub.d/40_custom:

menuentry "Android-x86" {
set root=(hd0,8)
linux /android-4.4-r2/kernel quiet root=/dev/ram0 androidboot.hardware=generic_x86 acpi_sleep=s3_bios,s3_mode SRC=/android-4.4-r2 DATA= DPI=160
initrd /android-4.4-r2/initrd.img
}

I'd be grateful for any assistance

---

### Post by grahammechanical on 2016-04-09
Did you make the file 40_custom executable before running update-grub?

Regards

---

### Post by yancek on 2016-04-09
When you run sudo update-grub, you will see output in the terminal.  If you didn't see android in the output there is no point in rebooting because it won't be in the menu.

I've never used android but the entries for the linux and initrd lines indicate that you have a directory in the root of sda8 named "android-4.4-r2" and the kernel (actually named kernel) is in that directory as is the initrd.img file.  Check that first.

---

### Post by Trevor_Owen on 2016-04-09
Yes.  Sorry, I forgot to include that.

Trevor

---

### Post by Trevor_Owen on 2016-04-09
Yes, I do have a directory named android-4.4-rc2 in the root of sda8, and the kernel and intrd.img are in that directory.

Trevor

---

