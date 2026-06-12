---
title: "Re-compiling Ubuntu kernel then can not restart os with new kernel"
date: 2016-05-12
forum: General Help
---

### Post by Turisla on 2016-05-12
The ubuntu os on my PC is Ubuntu 10.04 with linux kernel 2.6.32.21 and I want to learn how to compiling linux kernel,so I re-compiling kernel 2.6.32.27.
I use make defconfig to access a .config and i modified nothing.
then, i use make --> make modules_install -->make install -->[COLOR=#362E2B][FONT=&#23435]mkinitramfs -o /boot/initrd.img-2.6.32.27 --->[/FONT][/COLOR][COLOR=#362E2B][FONT=&#23435]update-initramfs -c -k 2.6.32.27 to compile and install the new kernel
but when i restat the os,it show me like this:[/FONT][/COLOR][IMG]file:///C:\Users\lenovo\Documents\Tencent Files\295954168\Image\C2C\11852C4C155D56E01E31C8DD6AE075DC.jpg[/IMG][IMG]http://i4.buimg.com/155d56e01e31c8dd.jpg[/IMG]

and my grub.cfg (partly) like this:

```
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32.27' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b3f3786d-7431-409b-b43d-de7f455721f6
	linux	/boot/vmlinuz-2.6.32.27 root=UUID=b3f3786d-7431-409b-b43d-de7f455721f6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32.27
}
menuentry 'Ubuntu, with Linux 2.6.32.27 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b3f3786d-7431-409b-b43d-de7f455721f6
	echo	'Loading Linux 2.6.32.27 ...'
	linux	/boot/vmlinuz-2.6.32.27 root=UUID=b3f3786d-7431-409b-b43d-de7f455721f6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32.27
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b3f3786d-7431-409b-b43d-de7f455721f6
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b3f3786d-7431-409b-b43d-de7f455721f6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b3f3786d-7431-409b-b43d-de7f455721f6
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b3f3786d-7431-409b-b43d-de7f455721f6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b3f3786d-7431-409b-b43d-de7f455721f6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b3f3786d-7431-409b-b43d-de7f455721f6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=10
    else
      set timeout=10
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=10
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```



i don't know how to solve this problem,please help me,thank you.

---

