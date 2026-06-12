---
title: "dual bootin xubuntu and a linux"
date: 2006-08-09
forum: General Help
---

### Post by mrtuesday42 on 2006-08-09
hey im installing xubuntu and id like to do an install of auditor as well...ive created a parition for x at / and another parition for aud that i didnt mount...there is the swap as well...soooo when im done installing xubu can i just go and install aud telling it to use the unmounted partition? makes sense to me...but how do i choose which one to boot to? any help is greatly appreciated

---

### Post by vijirajan on 2006-08-09
You could definitely do that. To choose which one to boot to, you will have to install a boot loader like GRUB to Master Boot Record (MBR). You could install GRUB to MBR either in the xubuntu installation or the other linux installation. Once you install GRUB, reboot the machine and boot to the OS that is available in the boot menu. This will be the OS that you choose to install GRUB from. Goto /boot/grub directory and menu.lst to have an entry for the other OS.

Lets assume that you installed Xubuntu and the other linux in this order. Also assume that you installed GRUB to MBR on the other linux installation. So when you reboot the machine the GRUB boot menu will only show "the other linux". Boot to that OS and open a terminal client. Edit /boot/grub/menu.lst in your favorite editor to include a menu entry for Xubuntu. All you have to do is copy the existing menu item and change **root** entry and **kernel** entries.

e.g
If this were the only menu item in menu.lst:

title           Auditor, kernel 2.6.15-26-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-686
boot

you would add the following to the above menu entry:

title           Xubuntu, kernel 2.6.15-26-686
root            **(hd0,2)**
kernel          /boot/vmlinuz-2.6.15-26-686 root=**/dev/sda2** ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-686
boot

Bolded entries need to be changed according to your partition setup.

Hope this helps

---

### Post by mrtuesday42 on 2006-08-09
thanks...i havent gotten around to installin number two cuz i ate my apps menu so i had to fix that...and now my wireless card doesnt work...it says the hardware is there and the drivers are good but no lights...gjklajfkals...not cool...ill try tomorrow

---

### Post by skale on 2006-08-09
Be sure to check the real kernel path, otherwise it won't boot.

---

### Post by mrtuesday42 on 2006-08-10
hey...just finished installing the second one...it asked for a floppy and i told it no...it put the grub to the mbr but ubuntu is the only one on the list and the one that boots up...help? did i do something wrong? can i go back and make another floppy?

---

### Post by vijirajan on 2006-08-10
That should be fine. I think the other linux is missing an entry in the menu.lst.

Follow the steps below to fix this:

1) Boot to Xubuntu
2) Open /boot/grub/menu.lst in your favorite editor
3) Add the entry for the other linux in this file based on the example in my previous post (you need to know the partition where the other linux is installed for this)

---

