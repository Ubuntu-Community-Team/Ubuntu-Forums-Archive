---
title: "Grub 2.0+ long entries and missing device designations"
date: 2013-01-05
forum: General Help
---

### Post by kansasnoob on 2013-01-05
I began noticing in Quantal, and now notice while testing Raring, that the newest 'grub-pc' displays very long entries, lacks device designations, and sometimes creates multiple - perhaps even nonsensical - menu entries :(

I'm curious how others are dealing with this in complex multi-boots. What I've been doing is just keeping my Precise grub in control of boot, and then booting into the freshly installed Quantal (or Raring), and then just installing 'grub' which automatically removes 'grub-pc' and other dependencies, then I can run "update-grub" and allow the creation of a menu.lst.

Then the Precise grub2 reads the info from menu.lst so I can see what I want to boot ........... very, very sloppy way of doing things :redface:

Here's a link to my boot repair output - run from Precise on /dev/sda2 - warning it'll blow your brain up:

[http://paste.ubuntu.com/1499814/](http://paste.ubuntu.com/1499814/)

BTW the only OS that's not been sort of converted from the newest grub2 to legacy grub is the one on /dev/sdb1.

Oh and here's one bug report:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1065801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1065801)

There is another that's pertinent to this but I can't find it ATM.

Edit: [Thanks to *dino99*]("http://ubuntuforums.org/showpost.php?p=12439782&postcount=2") I found that other bug report:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1050774](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1050774)

---

### Post by Pjotr123 on 2013-01-05
You mean the UUID's for the partitions? What's wrong with them?

---

### Post by kansasnoob on 2013-01-05
> **Pjotr123 said:**
> You mean the UUID's for the partitions? What's wrong with them?

No, I mean the actual boot menu titles. Like I'm using Precise on sda2 with it's native grub2 to boot, and if you look at it's grub.cfg "/etc/grub.d/30_os-prober" once it reads the new grub2 on sdb1 the entries are super long:

```
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a6e52bd9-488c-4f5e-8dab-59c506d246e0 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root a6e52bd9-488c-4f5e-8dab-59c506d246e0
	linux /boot/vmlinuz-3.7.0-7-generic root=UUID=a6e52bd9-488c-4f5e-8dab-59c506d246e0 ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.7.0-7-generic
}
menuentry "Ubuntu, with Linux 3.7.0-7-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.7.0-7-generic-advanced-a6e52bd9-488c-4f5e-8dab-59c506d246e0 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root a6e52bd9-488c-4f5e-8dab-59c506d246e0
	linux /boot/vmlinuz-3.7.0-7-generic root=UUID=a6e52bd9-488c-4f5e-8dab-59c506d246e0 ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.7.0-7-generic
}
menuentry "Ubuntu, with Linux 3.7.0-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.7.0-7-generic-recovery-a6e52bd9-488c-4f5e-8dab-59c506d246e0 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root a6e52bd9-488c-4f5e-8dab-59c506d246e0
	linux /boot/vmlinuz-3.7.0-7-generic root=UUID=a6e52bd9-488c-4f5e-8dab-59c506d246e0 ro recovery nomodeset
	initrd /boot/initrd.img-3.7.0-7-generic
}
menuentry "Ubuntu 12.10, memtest86+ (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root a6e52bd9-488c-4f5e-8dab-59c506d246e0
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu Raring Ringtail (development branch) (13.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root a6e52bd9-488c-4f5e-8dab-59c506d246e0
	linux /boot/vmlinuz-3.7.0-7-generic root=UUID=cd5ab3a7-b267-437d-b917-bc75157d02bc ro quiet splash
	initrd /boot/initrd.img-3.7.0-7-generic
}
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic--cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root a6e52bd9-488c-4f5e-8dab-59c506d246e0
	linux /boot/vmlinuz-3.7.0-7-generic root=UUID=cd5ab3a7-b267-437d-b917-bc75157d02bc ro quiet splash
	initrd /boot/initrd.img-3.7.0-7-generic
}
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic-root=UUID=cd5ab3a7-b267-437d-b917-bc75157d02bc ro single-cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root a6e52bd9-488c-4f5e-8dab-59c506d246e0
	linux /boot/vmlinuz-3.7.0-7-generic root=UUID=cd5ab3a7-b267-437d-b917-bc75157d02bc ro single
	initrd /boot/initrd.img-3.7.0-7-generic
}
menuentry "Ubuntu Raring Ringtail (development branch), memtest86+ (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root a6e52bd9-488c-4f5e-8dab-59c506d246e0
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu Raring Ringtail (development branch) (13.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root a6e52bd9-488c-4f5e-8dab-59c506d246e0
	linux /boot/vmlinuz-3.7.0-7-generic root=UUID=680f4e58-9146-4b2e-9444-40e973542c68 ro quiet splash
	initrd /boot/initrd.img-3.7.0-7-generic
}
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic--680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root a6e52bd9-488c-4f5e-8dab-59c506d246e0
	linux /boot/vmlinuz-3.7.0-7-generic root=UUID=680f4e58-9146-4b2e-9444-40e973542c68 ro quiet splash
	initrd /boot/initrd.img-3.7.0-7-generic
}
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic-root=UUID=680f4e58-9146-4b2e-9444-40e973542c68 ro single-680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root a6e52bd9-488c-4f5e-8dab-59c506d246e0
	linux /boot/vmlinuz-3.7.0-7-generic root=UUID=680f4e58-9146-4b2e-9444-40e973542c68 ro single
	initrd /boot/initrd.img-3.7.0-7-generic
}
menuentry "Ubuntu Raring Ringtail (development branch), memtest86+ (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root a6e52bd9-488c-4f5e-8dab-59c506d246e0
	linux /boot/memtest86+.bin 
}
```

And some of those are actually even just wrong, meaning they try to boot the wrong OS.

If you look at the grub.cfg in that newest install with the newest grub2 there are no device designations so you have to guess what OS you might be booting:

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 11.10 (11.10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-9534c4a3-d3d3-446d-af2d-fa4875c29f5c' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9534c4a3-d3d3-446d-af2d-fa4875c29f5c
	else
	  search --no-floppy --fs-uuid --set=root 9534c4a3-d3d3-446d-af2d-fa4875c29f5c
	fi
	linux /boot/vmlinuz-3.0.0-27-generic root=UUID=9534c4a3-d3d3-446d-af2d-fa4875c29f5c ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-27-generic
}
submenu 'Advanced options for Ubuntu 11.10 (11.10)' $menuentry_id_option 'osprober-gnulinux-advanced-9534c4a3-d3d3-446d-af2d-fa4875c29f5c' {
	menuentry 'Ubuntu, with Linux 3.0.0-27-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-27-generic--9534c4a3-d3d3-446d-af2d-fa4875c29f5c' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9534c4a3-d3d3-446d-af2d-fa4875c29f5c
		else
		  search --no-floppy --fs-uuid --set=root 9534c4a3-d3d3-446d-af2d-fa4875c29f5c
		fi
		linux /boot/vmlinuz-3.0.0-27-generic root=UUID=9534c4a3-d3d3-446d-af2d-fa4875c29f5c ro quiet splash vt.handoff=7
		initrd /boot/initrd.img-3.0.0-27-generic
	}
	menuentry 'Ubuntu, with Linux 3.0.0-27-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-27-generic-root=UUID=9534c4a3-d3d3-446d-af2d-fa4875c29f5c ro recovery nomodeset-9534c4a3-d3d3-446d-af2d-fa4875c29f5c' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9534c4a3-d3d3-446d-af2d-fa4875c29f5c
		else
		  search --no-floppy --fs-uuid --set=root 9534c4a3-d3d3-446d-af2d-fa4875c29f5c
		fi
		linux /boot/vmlinuz-3.0.0-27-generic root=UUID=9534c4a3-d3d3-446d-af2d-fa4875c29f5c ro recovery nomodeset
		initrd /boot/initrd.img-3.0.0-27-generic
	}
	menuentry 'Ubuntu, with Linux 3.0.0-26-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-26-generic--9534c4a3-d3d3-446d-af2d-fa4875c29f5c' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9534c4a3-d3d3-446d-af2d-fa4875c29f5c
		else
		  search --no-floppy --fs-uuid --set=root 9534c4a3-d3d3-446d-af2d-fa4875c29f5c
		fi
		linux /boot/vmlinuz-3.0.0-26-generic root=UUID=9534c4a3-d3d3-446d-af2d-fa4875c29f5c ro quiet splash vt.handoff=7
		initrd /boot/initrd.img-3.0.0-26-generic
	}
	menuentry 'Ubuntu, with Linux 3.0.0-26-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-26-generic-root=UUID=9534c4a3-d3d3-446d-af2d-fa4875c29f5c ro recovery nomodeset-9534c4a3-d3d3-446d-af2d-fa4875c29f5c' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9534c4a3-d3d3-446d-af2d-fa4875c29f5c
		else
		  search --no-floppy --fs-uuid --set=root 9534c4a3-d3d3-446d-af2d-fa4875c29f5c
		fi
		linux /boot/vmlinuz-3.0.0-26-generic root=UUID=9534c4a3-d3d3-446d-af2d-fa4875c29f5c ro recovery nomodeset
		initrd /boot/initrd.img-3.0.0-26-generic
	}
	menuentry 'Ubuntu, with Linux 3.0.0-24-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-24-generic--9534c4a3-d3d3-446d-af2d-fa4875c29f5c' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9534c4a3-d3d3-446d-af2d-fa4875c29f5c
		else
		  search --no-floppy --fs-uuid --set=root 9534c4a3-d3d3-446d-af2d-fa4875c29f5c
		fi
		linux /boot/vmlinuz-3.0.0-24-generic root=UUID=9534c4a3-d3d3-446d-af2d-fa4875c29f5c ro quiet splash vt.handoff=7
		initrd /boot/initrd.img-3.0.0-24-generic
	}
	menuentry 'Ubuntu, with Linux 3.0.0-24-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-24-generic-root=UUID=9534c4a3-d3d3-446d-af2d-fa4875c29f5c ro recovery nomodeset-9534c4a3-d3d3-446d-af2d-fa4875c29f5c' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9534c4a3-d3d3-446d-af2d-fa4875c29f5c
		else
		  search --no-floppy --fs-uuid --set=root 9534c4a3-d3d3-446d-af2d-fa4875c29f5c
		fi
		linux /boot/vmlinuz-3.0.0-24-generic root=UUID=9534c4a3-d3d3-446d-af2d-fa4875c29f5c ro recovery nomodeset
		initrd /boot/initrd.img-3.0.0-24-generic
	}
	menuentry 'Ubuntu, with Linux 3.0.0-23-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-23-generic--9534c4a3-d3d3-446d-af2d-fa4875c29f5c' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9534c4a3-d3d3-446d-af2d-fa4875c29f5c
		else
		  search --no-floppy --fs-uuid --set=root 9534c4a3-d3d3-446d-af2d-fa4875c29f5c
		fi
		linux /boot/vmlinuz-3.0.0-23-generic root=UUID=9534c4a3-d3d3-446d-af2d-fa4875c29f5c ro quiet splash vt.handoff=7
		initrd /boot/initrd.img-3.0.0-23-generic
	}
	menuentry 'Ubuntu, with Linux 3.0.0-23-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-23-generic-root=UUID=9534c4a3-d3d3-446d-af2d-fa4875c29f5c ro recovery nomodeset-9534c4a3-d3d3-446d-af2d-fa4875c29f5c' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9534c4a3-d3d3-446d-af2d-fa4875c29f5c
		else
		  search --no-floppy --fs-uuid --set=root 9534c4a3-d3d3-446d-af2d-fa4875c29f5c
		fi
		linux /boot/vmlinuz-3.0.0-23-generic root=UUID=9534c4a3-d3d3-446d-af2d-fa4875c29f5c ro recovery nomodeset
		initrd /boot/initrd.img-3.0.0-23-generic
	}
}

menuentry 'Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-0e96c168-b836-48dc-8561-288d75c3bc01' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos10'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  0e96c168-b836-48dc-8561-288d75c3bc01
	else
	  search --no-floppy --fs-uuid --set=root 0e96c168-b836-48dc-8561-288d75c3bc01
	fi
	linux /boot/vmlinuz-3.2.0-33-generic root=UUID=0e96c168-b836-48dc-8561-288d75c3bc01 ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-33-generic
}
submenu 'Advanced options for Ubuntu 12.04.1 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-0e96c168-b836-48dc-8561-288d75c3bc01' {
	menuentry 'Ubuntu, with Linux 3.2.0-33-generic (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-33-generic--0e96c168-b836-48dc-8561-288d75c3bc01' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  0e96c168-b836-48dc-8561-288d75c3bc01
		else
		  search --no-floppy --fs-uuid --set=root 0e96c168-b836-48dc-8561-288d75c3bc01
		fi
		linux /boot/vmlinuz-3.2.0-33-generic root=UUID=0e96c168-b836-48dc-8561-288d75c3bc01 ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-33-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-33-generic (recovery mode) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-33-generic-root=UUID=0e96c168-b836-48dc-8561-288d75c3bc01 ro recovery nomodeset-0e96c168-b836-48dc-8561-288d75c3bc01' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  0e96c168-b836-48dc-8561-288d75c3bc01
		else
		  search --no-floppy --fs-uuid --set=root 0e96c168-b836-48dc-8561-288d75c3bc01
		fi
		linux /boot/vmlinuz-3.2.0-33-generic root=UUID=0e96c168-b836-48dc-8561-288d75c3bc01 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-33-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-23-generic (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-23-generic--0e96c168-b836-48dc-8561-288d75c3bc01' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  0e96c168-b836-48dc-8561-288d75c3bc01
		else
		  search --no-floppy --fs-uuid --set=root 0e96c168-b836-48dc-8561-288d75c3bc01
		fi
		linux /boot/vmlinuz-3.2.0-23-generic root=UUID=0e96c168-b836-48dc-8561-288d75c3bc01 ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-23-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-23-generic-root=UUID=0e96c168-b836-48dc-8561-288d75c3bc01 ro recovery nomodeset-0e96c168-b836-48dc-8561-288d75c3bc01' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos10'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos10 --hint-efi=hd0,msdos10 --hint-baremetal=ahci0,msdos10  0e96c168-b836-48dc-8561-288d75c3bc01
		else
		  search --no-floppy --fs-uuid --set=root 0e96c168-b836-48dc-8561-288d75c3bc01
		fi
		linux /boot/vmlinuz-3.2.0-23-generic root=UUID=0e96c168-b836-48dc-8561-288d75c3bc01 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-23-generic
	}
}

menuentry 'Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-b03a64b1-370b-4e00-a510-7f7d460f3190' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos11'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  b03a64b1-370b-4e00-a510-7f7d460f3190
	else
	  search --no-floppy --fs-uuid --set=root b03a64b1-370b-4e00-a510-7f7d460f3190
	fi
	linux /boot/vmlinuz-3.2.0-34-generic-pae root=UUID=b03a64b1-370b-4e00-a510-7f7d460f3190 ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-34-generic-pae
}
submenu 'Advanced options for Ubuntu 12.04.1 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-b03a64b1-370b-4e00-a510-7f7d460f3190' {
	menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-34-generic-pae--b03a64b1-370b-4e00-a510-7f7d460f3190' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  b03a64b1-370b-4e00-a510-7f7d460f3190
		else
		  search --no-floppy --fs-uuid --set=root b03a64b1-370b-4e00-a510-7f7d460f3190
		fi
		linux /boot/vmlinuz-3.2.0-34-generic-pae root=UUID=b03a64b1-370b-4e00-a510-7f7d460f3190 ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-34-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae (recovery mode) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-34-generic-pae-root=UUID=b03a64b1-370b-4e00-a510-7f7d460f3190 ro recovery nomodeset-b03a64b1-370b-4e00-a510-7f7d460f3190' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos11'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos11 --hint-efi=hd0,msdos11 --hint-baremetal=ahci0,msdos11  b03a64b1-370b-4e00-a510-7f7d460f3190
		else
		  search --no-floppy --fs-uuid --set=root b03a64b1-370b-4e00-a510-7f7d460f3190
		fi
		linux /boot/vmlinuz-3.2.0-34-generic-pae root=UUID=b03a64b1-370b-4e00-a510-7f7d460f3190 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-34-generic-pae
	}
}

menuentry 'Ubuntu 12.10 (12.10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos12'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf
	else
	  search --no-floppy --fs-uuid --set=root a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf
	fi
	linux /boot/vmlinuz-3.5.0-21-generic root=UUID=a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf ro quiet splash
	initrd /boot/initrd.img-3.5.0-21-generic
}
submenu 'Advanced options for Ubuntu 12.10 (12.10)' $menuentry_id_option 'osprober-gnulinux-advanced-a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf' {
	menuentry 'Ubuntu 12.10, kernel 3.5.0-21-generic (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic--a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos12'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf
		else
		  search --no-floppy --fs-uuid --set=root a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf
		fi
		linux /boot/vmlinuz-3.5.0-21-generic root=UUID=a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf ro quiet splash
		initrd /boot/initrd.img-3.5.0-21-generic
	}
	menuentry 'Ubuntu 12.10, kernel 3.5.0-21-generic (recovery mode) (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic-root=UUID=a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf ro single-a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos12'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf
		else
		  search --no-floppy --fs-uuid --set=root a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf
		fi
		linux /boot/vmlinuz-3.5.0-21-generic root=UUID=a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf ro single
		initrd /boot/initrd.img-3.5.0-21-generic
	}
	menuentry 'Ubuntu 12.10, kernel 3.5.0-19-generic (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-19-generic--a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos12'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf
		else
		  search --no-floppy --fs-uuid --set=root a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf
		fi
		linux /boot/vmlinuz-3.5.0-19-generic root=UUID=a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf ro quiet splash
		initrd /boot/initrd.img-3.5.0-19-generic
	}
	menuentry 'Ubuntu 12.10, kernel 3.5.0-19-generic (recovery mode) (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-19-generic-root=UUID=a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf ro single-a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos12'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf
		else
		  search --no-floppy --fs-uuid --set=root a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf
		fi
		linux /boot/vmlinuz-3.5.0-19-generic root=UUID=a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf ro single
		initrd /boot/initrd.img-3.5.0-19-generic
	}
	menuentry 'Ubuntu 12.10, kernel 3.5.0-17-generic (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos12'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf
		else
		  search --no-floppy --fs-uuid --set=root a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf
		fi
		linux /boot/vmlinuz-3.5.0-17-generic root=UUID=a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf ro quiet splash
		initrd /boot/initrd.img-3.5.0-17-generic
	}
	menuentry 'Ubuntu 12.10, kernel 3.5.0-17-generic (recovery mode) (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf ro single-a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos12'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf
		else
		  search --no-floppy --fs-uuid --set=root a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf
		fi
		linux /boot/vmlinuz-3.5.0-17-generic root=UUID=a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf ro single
		initrd /boot/initrd.img-3.5.0-17-generic
	}
	menuentry 'Ubuntu 12.10, memtest86+ (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos12'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf
		else
		  search --no-floppy --fs-uuid --set=root a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf
		fi
		linux /boot/memtest86+.bin 
	}
}

menuentry 'Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-86248151-b203-4971-bdc8-f095cf3a10d8' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos13'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  86248151-b203-4971-bdc8-f095cf3a10d8
	else
	  search --no-floppy --fs-uuid --set=root 86248151-b203-4971-bdc8-f095cf3a10d8
	fi
	linux /boot/vmlinuz-3.2.0-33-generic-pae root=UUID=86248151-b203-4971-bdc8-f095cf3a10d8 ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-33-generic-pae
}
submenu 'Advanced options for Ubuntu 12.04.1 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-86248151-b203-4971-bdc8-f095cf3a10d8' {
	menuentry 'Ubuntu, with Linux 3.2.0-33-generic-pae (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-33-generic-pae--86248151-b203-4971-bdc8-f095cf3a10d8' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos13'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  86248151-b203-4971-bdc8-f095cf3a10d8
		else
		  search --no-floppy --fs-uuid --set=root 86248151-b203-4971-bdc8-f095cf3a10d8
		fi
		linux /boot/vmlinuz-3.2.0-33-generic-pae root=UUID=86248151-b203-4971-bdc8-f095cf3a10d8 ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-33-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-33-generic-pae (recovery mode) (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-33-generic-pae-root=UUID=86248151-b203-4971-bdc8-f095cf3a10d8 ro recovery nomodeset-86248151-b203-4971-bdc8-f095cf3a10d8' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos13'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  86248151-b203-4971-bdc8-f095cf3a10d8
		else
		  search --no-floppy --fs-uuid --set=root 86248151-b203-4971-bdc8-f095cf3a10d8
		fi
		linux /boot/vmlinuz-3.2.0-33-generic-pae root=UUID=86248151-b203-4971-bdc8-f095cf3a10d8 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-33-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-32-generic-pae--86248151-b203-4971-bdc8-f095cf3a10d8' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos13'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  86248151-b203-4971-bdc8-f095cf3a10d8
		else
		  search --no-floppy --fs-uuid --set=root 86248151-b203-4971-bdc8-f095cf3a10d8
		fi
		linux /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=86248151-b203-4971-bdc8-f095cf3a10d8 ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-32-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode) (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-32-generic-pae-root=UUID=86248151-b203-4971-bdc8-f095cf3a10d8 ro recovery nomodeset-86248151-b203-4971-bdc8-f095cf3a10d8' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos13'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  86248151-b203-4971-bdc8-f095cf3a10d8
		else
		  search --no-floppy --fs-uuid --set=root 86248151-b203-4971-bdc8-f095cf3a10d8
		fi
		linux /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=86248151-b203-4971-bdc8-f095cf3a10d8 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-32-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-29-generic-pae--86248151-b203-4971-bdc8-f095cf3a10d8' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos13'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  86248151-b203-4971-bdc8-f095cf3a10d8
		else
		  search --no-floppy --fs-uuid --set=root 86248151-b203-4971-bdc8-f095cf3a10d8
		fi
		linux /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=86248151-b203-4971-bdc8-f095cf3a10d8 ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-29-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode) (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-29-generic-pae-root=UUID=86248151-b203-4971-bdc8-f095cf3a10d8 ro recovery nomodeset-86248151-b203-4971-bdc8-f095cf3a10d8' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos13'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  86248151-b203-4971-bdc8-f095cf3a10d8
		else
		  search --no-floppy --fs-uuid --set=root 86248151-b203-4971-bdc8-f095cf3a10d8
		fi
		linux /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=86248151-b203-4971-bdc8-f095cf3a10d8 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-29-generic-pae
	}
}

menuentry 'Ubuntu Raring Ringtail (development branch) (13.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-cd5ab3a7-b267-437d-b917-bc75157d02bc' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos14'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos14 --hint-efi=hd0,msdos14 --hint-baremetal=ahci0,msdos14  cd5ab3a7-b267-437d-b917-bc75157d02bc
	else
	  search --no-floppy --fs-uuid --set=root cd5ab3a7-b267-437d-b917-bc75157d02bc
	fi
	linux /boot/vmlinuz-3.7.0-7-generic root=UUID=cd5ab3a7-b267-437d-b917-bc75157d02bc ro quiet splash
	initrd /boot/initrd.img-3.7.0-7-generic
}
submenu 'Advanced options for Ubuntu Raring Ringtail (development branch) (13.04)' $menuentry_id_option 'osprober-gnulinux-advanced-cd5ab3a7-b267-437d-b917-bc75157d02bc' {
	menuentry 'Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic--cd5ab3a7-b267-437d-b917-bc75157d02bc' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos14'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos14 --hint-efi=hd0,msdos14 --hint-baremetal=ahci0,msdos14  cd5ab3a7-b267-437d-b917-bc75157d02bc
		else
		  search --no-floppy --fs-uuid --set=root cd5ab3a7-b267-437d-b917-bc75157d02bc
		fi
		linux /boot/vmlinuz-3.7.0-7-generic root=UUID=cd5ab3a7-b267-437d-b917-bc75157d02bc ro quiet splash
		initrd /boot/initrd.img-3.7.0-7-generic
	}
	menuentry 'Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic-root=UUID=cd5ab3a7-b267-437d-b917-bc75157d02bc ro single-cd5ab3a7-b267-437d-b917-bc75157d02bc' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos14'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos14 --hint-efi=hd0,msdos14 --hint-baremetal=ahci0,msdos14  cd5ab3a7-b267-437d-b917-bc75157d02bc
		else
		  search --no-floppy --fs-uuid --set=root cd5ab3a7-b267-437d-b917-bc75157d02bc
		fi
		linux /boot/vmlinuz-3.7.0-7-generic root=UUID=cd5ab3a7-b267-437d-b917-bc75157d02bc ro single
		initrd /boot/initrd.img-3.7.0-7-generic
	}
	menuentry 'Ubuntu Raring Ringtail (development branch), memtest86+ (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--cd5ab3a7-b267-437d-b917-bc75157d02bc' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos14'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos14 --hint-efi=hd0,msdos14 --hint-baremetal=ahci0,msdos14  cd5ab3a7-b267-437d-b917-bc75157d02bc
		else
		  search --no-floppy --fs-uuid --set=root cd5ab3a7-b267-437d-b917-bc75157d02bc
		fi
		linux /boot/memtest86+.bin 
	}
}

menuentry 'Ubuntu Raring Ringtail (development branch) (13.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-680f4e58-9146-4b2e-9444-40e973542c68' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos15'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos15 --hint-efi=hd0,msdos15 --hint-baremetal=ahci0,msdos15  680f4e58-9146-4b2e-9444-40e973542c68
	else
	  search --no-floppy --fs-uuid --set=root 680f4e58-9146-4b2e-9444-40e973542c68
	fi
	linux /boot/vmlinuz-3.7.0-7-generic root=UUID=680f4e58-9146-4b2e-9444-40e973542c68 ro quiet splash
	initrd /boot/initrd.img-3.7.0-7-generic
}
submenu 'Advanced options for Ubuntu Raring Ringtail (development branch) (13.04)' $menuentry_id_option 'osprober-gnulinux-advanced-680f4e58-9146-4b2e-9444-40e973542c68' {
	menuentry 'Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic--680f4e58-9146-4b2e-9444-40e973542c68' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos15'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos15 --hint-efi=hd0,msdos15 --hint-baremetal=ahci0,msdos15  680f4e58-9146-4b2e-9444-40e973542c68
		else
		  search --no-floppy --fs-uuid --set=root 680f4e58-9146-4b2e-9444-40e973542c68
		fi
		linux /boot/vmlinuz-3.7.0-7-generic root=UUID=680f4e58-9146-4b2e-9444-40e973542c68 ro quiet splash
		initrd /boot/initrd.img-3.7.0-7-generic
	}
	menuentry 'Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic-root=UUID=680f4e58-9146-4b2e-9444-40e973542c68 ro single-680f4e58-9146-4b2e-9444-40e973542c68' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos15'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos15 --hint-efi=hd0,msdos15 --hint-baremetal=ahci0,msdos15  680f4e58-9146-4b2e-9444-40e973542c68
		else
		  search --no-floppy --fs-uuid --set=root 680f4e58-9146-4b2e-9444-40e973542c68
		fi
		linux /boot/vmlinuz-3.7.0-7-generic root=UUID=680f4e58-9146-4b2e-9444-40e973542c68 ro single
		initrd /boot/initrd.img-3.7.0-7-generic
	}
	menuentry 'Ubuntu Raring Ringtail (development branch), memtest86+ (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--680f4e58-9146-4b2e-9444-40e973542c68' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos15'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos15 --hint-efi=hd0,msdos15 --hint-baremetal=ahci0,msdos15  680f4e58-9146-4b2e-9444-40e973542c68
		else
		  search --no-floppy --fs-uuid --set=root 680f4e58-9146-4b2e-9444-40e973542c68
		fi
		linux /boot/memtest86+.bin 
	}
}

menuentry 'Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-c1dc4187-4170-406f-8b8e-c1a3904e1315' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  c1dc4187-4170-406f-8b8e-c1a3904e1315
	else
	  search --no-floppy --fs-uuid --set=root c1dc4187-4170-406f-8b8e-c1a3904e1315
	fi
	linux /boot/vmlinuz-3.2.0-35-generic-pae root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-35-generic-pae
}
submenu 'Advanced options for Ubuntu 12.04.1 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-c1dc4187-4170-406f-8b8e-c1a3904e1315' {
	menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic-pae--c1dc4187-4170-406f-8b8e-c1a3904e1315' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  c1dc4187-4170-406f-8b8e-c1a3904e1315
		else
		  search --no-floppy --fs-uuid --set=root c1dc4187-4170-406f-8b8e-c1a3904e1315
		fi
		linux /boot/vmlinuz-3.2.0-35-generic-pae root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-35-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode) (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic-pae-root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro recovery nomodeset-c1dc4187-4170-406f-8b8e-c1a3904e1315' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  c1dc4187-4170-406f-8b8e-c1a3904e1315
		else
		  search --no-floppy --fs-uuid --set=root c1dc4187-4170-406f-8b8e-c1a3904e1315
		fi
		linux /boot/vmlinuz-3.2.0-35-generic-pae root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-35-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-34-generic-pae--c1dc4187-4170-406f-8b8e-c1a3904e1315' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  c1dc4187-4170-406f-8b8e-c1a3904e1315
		else
		  search --no-floppy --fs-uuid --set=root c1dc4187-4170-406f-8b8e-c1a3904e1315
		fi
		linux /boot/vmlinuz-3.2.0-34-generic-pae root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-34-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae (recovery mode) (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-34-generic-pae-root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro recovery nomodeset-c1dc4187-4170-406f-8b8e-c1a3904e1315' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  c1dc4187-4170-406f-8b8e-c1a3904e1315
		else
		  search --no-floppy --fs-uuid --set=root c1dc4187-4170-406f-8b8e-c1a3904e1315
		fi
		linux /boot/vmlinuz-3.2.0-34-generic-pae root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-34-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-33-generic-pae (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-33-generic-pae--c1dc4187-4170-406f-8b8e-c1a3904e1315' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  c1dc4187-4170-406f-8b8e-c1a3904e1315
		else
		  search --no-floppy --fs-uuid --set=root c1dc4187-4170-406f-8b8e-c1a3904e1315
		fi
		linux /boot/vmlinuz-3.2.0-33-generic-pae root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-33-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-33-generic-pae (recovery mode) (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-33-generic-pae-root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro recovery nomodeset-c1dc4187-4170-406f-8b8e-c1a3904e1315' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  c1dc4187-4170-406f-8b8e-c1a3904e1315
		else
		  search --no-floppy --fs-uuid --set=root c1dc4187-4170-406f-8b8e-c1a3904e1315
		fi
		linux /boot/vmlinuz-3.2.0-33-generic-pae root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-33-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-32-generic-pae--c1dc4187-4170-406f-8b8e-c1a3904e1315' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  c1dc4187-4170-406f-8b8e-c1a3904e1315
		else
		  search --no-floppy --fs-uuid --set=root c1dc4187-4170-406f-8b8e-c1a3904e1315
		fi
		linux /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-32-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode) (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-32-generic-pae-root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro recovery nomodeset-c1dc4187-4170-406f-8b8e-c1a3904e1315' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  c1dc4187-4170-406f-8b8e-c1a3904e1315
		else
		  search --no-floppy --fs-uuid --set=root c1dc4187-4170-406f-8b8e-c1a3904e1315
		fi
		linux /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-32-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-31-generic-pae (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-31-generic-pae--c1dc4187-4170-406f-8b8e-c1a3904e1315' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  c1dc4187-4170-406f-8b8e-c1a3904e1315
		else
		  search --no-floppy --fs-uuid --set=root c1dc4187-4170-406f-8b8e-c1a3904e1315
		fi
		linux /boot/vmlinuz-3.2.0-31-generic-pae root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-31-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-31-generic-pae (recovery mode) (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-31-generic-pae-root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro recovery nomodeset-c1dc4187-4170-406f-8b8e-c1a3904e1315' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  c1dc4187-4170-406f-8b8e-c1a3904e1315
		else
		  search --no-floppy --fs-uuid --set=root c1dc4187-4170-406f-8b8e-c1a3904e1315
		fi
		linux /boot/vmlinuz-3.2.0-31-generic-pae root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-31-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-30-generic-pae (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-30-generic-pae--c1dc4187-4170-406f-8b8e-c1a3904e1315' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  c1dc4187-4170-406f-8b8e-c1a3904e1315
		else
		  search --no-floppy --fs-uuid --set=root c1dc4187-4170-406f-8b8e-c1a3904e1315
		fi
		linux /boot/vmlinuz-3.2.0-30-generic-pae root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-30-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-30-generic-pae (recovery mode) (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-30-generic-pae-root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro recovery nomodeset-c1dc4187-4170-406f-8b8e-c1a3904e1315' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  c1dc4187-4170-406f-8b8e-c1a3904e1315
		else
		  search --no-floppy --fs-uuid --set=root c1dc4187-4170-406f-8b8e-c1a3904e1315
		fi
		linux /boot/vmlinuz-3.2.0-30-generic-pae root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-30-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-29-generic-pae--c1dc4187-4170-406f-8b8e-c1a3904e1315' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  c1dc4187-4170-406f-8b8e-c1a3904e1315
		else
		  search --no-floppy --fs-uuid --set=root c1dc4187-4170-406f-8b8e-c1a3904e1315
		fi
		linux /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-29-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode) (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-29-generic-pae-root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro recovery nomodeset-c1dc4187-4170-406f-8b8e-c1a3904e1315' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  c1dc4187-4170-406f-8b8e-c1a3904e1315
		else
		  search --no-floppy --fs-uuid --set=root c1dc4187-4170-406f-8b8e-c1a3904e1315
		fi
		linux /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-29-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-27-generic-pae--c1dc4187-4170-406f-8b8e-c1a3904e1315' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  c1dc4187-4170-406f-8b8e-c1a3904e1315
		else
		  search --no-floppy --fs-uuid --set=root c1dc4187-4170-406f-8b8e-c1a3904e1315
		fi
		linux /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-27-generic-pae
	}
	menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (recovery mode) (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-27-generic-pae-root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro recovery nomodeset-c1dc4187-4170-406f-8b8e-c1a3904e1315' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  c1dc4187-4170-406f-8b8e-c1a3904e1315
		else
		  search --no-floppy --fs-uuid --set=root c1dc4187-4170-406f-8b8e-c1a3904e1315
		fi
		linux /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-27-generic-pae
	}
}

menuentry 'Ubuntu 12.10 (12.10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-7c4147e0-e51a-4e42-a243-d07e7300b7fe' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos3'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  7c4147e0-e51a-4e42-a243-d07e7300b7fe
	else
	  search --no-floppy --fs-uuid --set=root 7c4147e0-e51a-4e42-a243-d07e7300b7fe
	fi
	linux /boot/vmlinuz-3.5.0-21-generic root=UUID=7c4147e0-e51a-4e42-a243-d07e7300b7fe ro quiet splash
	initrd /boot/initrd.img-3.5.0-21-generic
}
submenu 'Advanced options for Ubuntu 12.10 (12.10)' $menuentry_id_option 'osprober-gnulinux-advanced-7c4147e0-e51a-4e42-a243-d07e7300b7fe' {
	menuentry 'Ubuntu 12.10, kernel 3.5.0-21-generic (on /dev/sda3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic--7c4147e0-e51a-4e42-a243-d07e7300b7fe' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  7c4147e0-e51a-4e42-a243-d07e7300b7fe
		else
		  search --no-floppy --fs-uuid --set=root 7c4147e0-e51a-4e42-a243-d07e7300b7fe
		fi
		linux /boot/vmlinuz-3.5.0-21-generic root=UUID=7c4147e0-e51a-4e42-a243-d07e7300b7fe ro quiet splash
		initrd /boot/initrd.img-3.5.0-21-generic
	}
	menuentry 'Ubuntu 12.10, kernel 3.5.0-21-generic (recovery mode) (on /dev/sda3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic-root=UUID=7c4147e0-e51a-4e42-a243-d07e7300b7fe ro single-7c4147e0-e51a-4e42-a243-d07e7300b7fe' {
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  7c4147e0-e51a-4e42-a243-d07e7300b7fe
		else
		  search --no-floppy --fs-uuid --set=root 7c4147e0-e51a-4e42-a243-d07e7300b7fe
		fi
		linux /boot/vmlinuz-3.5.0-21-generic root=UUID=7c4147e0-e51a-4e42-a243-d07e7300b7fe ro single
		initrd /boot/initrd.img-3.5.0-21-generic
	}
}

### END /etc/grub.d/30_os-prober ###
```

It's much easier to see in the boot repair ouput because the menu entries are highlighted :D

---

### Post by grahammechanical on 2013-01-05
This issue got solved for me by work done on Grub 2.0 by, I think, Colin Watson.

[https://launchpad.net/~cjwatson]("https://launchpad.net/~cjwatson")

My apologies if I am naming the wrong person.

I made one of my 12.10 installs (now converted to 13.104) into the controlling install for Grub. And over the weeks the updates to Grub cleared the mess away.

12.04 will get Grub 2.0 at the end of January. This was tested some months ago. I tried it out with a another install of 12.04 and then using this PPA to bring in Grub 2.0

```
sudo add-apt-repository ppa:cjwatson/grub
sudo apt-get update
sudo apt-get install grub2
```

And it did not cause any problems. I still have 12.04 with Grub 1.99 and it still works fine. I do not let Grub 1.99 get control over the Grub menu. I am confident that when the change over to Grub 2.0 comes there will not be any issues. Not on my machine.

There is still the issue of not knowing what partition we are booting into. For example, my Ubuntu Raring is listed at the top as 'Ubuntu'. My Gnome Remix Raring is listed as 'Raring Ringtail 13.04 development branch.' And I have two items called 'ubuntu 12.04.1 LTS.' But which partition are they on?

All the old kernels are in the Advanced Options sub-menu. which is a good thing and when we enter the sub-menu we get the sda designations.

I have taken to using a white plastic sheet such as we get as a divider for a ring binder. I have put numbered lines on it in ink and I write out in pencil where each OS is in the menu order. I can then erase entries as I remove or put in new installs.

It is not quite stone age but not far from it in the 21st century.

Oh, have you noticed that this

> set root='hd0,msdos1'

msdos1, msdos2 etc., are now the designations for sda1, sda2, etc.

Regards.

---

### Post by oldfred on 2013-01-05
I followed Ranchhand's advice nicely documented and extended by cavsfan. Also some of the grub2 info from drs305. You boot directly to the updated link in / (root) not any specific kernel.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

    
First thing I do is turnoff os-prober and copy my own 40_custom from an older install. Then make whatever minor updates are required. That way I can have my own titles & with multi-booting, I only have to run the update-grub in the system I am booting into, not also in the one I use to boot from.

quick version:
       In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
    
this was Rachhand's, he must have used sda13 as his test partition for daily changes in alpha or beta. Uses link in /.
```
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}
    
```

Also partitions can be gpt. I use gpt with BIOS, but all UEFI systems are gpt also.
These are required if booting into a gpt partition, especially if booting msdos and chain loading to gpt.
       insmod part_gpt
              set root='(hd0,gpt2)'

---

### Post by YannBuntu on 2013-01-05
Hi
The longest entries you have are development versions, eg: 
'Advanced options for Ubuntu Raring Ringtail (development branch) (13.04)'
which are not used by basic users.
Other entries are shorter, eg:
'Ubuntu 12.10 (12.10)'
'Advanced options for Ubuntu 12.04.1 LTS (12.04)'

IMHO there is no length problem with non-dev entries.

However, i totally agree that GRUB should display the partition name (eg sda4, or sdb7), when there are several distributions.

---

### Post by kansasnoob on 2013-01-05
> **oldfred said:**
> I followed Ranchhand's advice nicely documented and extended by cavsfan. Also some of the grub2 info from drs305. You boot directly to the updated link in / (root) not any specific kernel.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

    
First thing I do is turnoff os-prober and copy my own 40_custom from an older install. Then make whatever minor updates are required. That way I can have my own titles & with multi-booting, I only have to run the update-grub in the system I am booting into, not also in the one I use to boot from.

quick version:
       In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
    
this was Rachhand's, he must have used sda13 as his test partition for daily changes in alpha or beta. Uses link in /.
```
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}
    
```

Also partitions can be gpt. I use gpt with BIOS, but all UEFI systems are gpt also.
These are required if booting into a gpt partition, especially if booting msdos and chain loading to gpt.
       insmod part_gpt
              set root='(hd0,gpt2)'

I like using this general method for creating a custom menu if my installs have any permanency whatsoever:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

But I use this specific box for SRU and iso testing to such a degree that some of the installations last only minutes or hours at best :D

---

### Post by kansasnoob on 2013-01-05
> **YannBuntu said:**
> Hi
The longest entries you have are development versions, eg: 
'Advanced options for Ubuntu Raring Ringtail (development branch) (13.04)'
which are not used by basic users.
Other entries are shorter, eg:
'Ubuntu 12.10 (12.10)'
'Advanced options for Ubuntu 12.04.1 LTS (12.04)'

IMHO there is no length problem with non-dev entries.

However, i totally agree that GRUB should display the partition name (eg sda4, or sdb7), when there are several distributions.

I'm curious, is there a command that a person can use to display only boot menu items as they'll actually appear on the monitor?

Like if I'm booted into a Quantal or Raring install and I want to see what the boot menu will display?

I can use a camera as I did here:

[https://launchpadlibrarian.net/127629067/no_dev.JPG](https://launchpadlibrarian.net/127629067/no_dev.JPG)

But I'm such a shaky old fart that many of my photos are almost worthless.

I'm thinking there must be a way to "grep" the menu entries from grub2's "30_os-prober" so they can be clearly parsed :confused:

---

### Post by kansasnoob on 2013-01-05
> **grahammechanical said:**
> This issue got solved for me by work done on Grub 2.0 by, I think, Colin Watson.

[https://launchpad.net/~cjwatson]("https://launchpad.net/~cjwatson")

My apologies if I am naming the wrong person.

I made one of my 12.10 installs (now converted to 13.104) into the controlling install for Grub. And over the weeks the updates to Grub cleared the mess away.

12.04 will get Grub 2.0 at the end of January. This was tested some months ago. I tried it out with a another install of 12.04 and then using this PPA to bring in Grub 2.0

```
sudo add-apt-repository ppa:cjwatson/grub
sudo apt-get update
sudo apt-get install grub2
```

And it did not cause any problems. I still have 12.04 with Grub 1.99 and it still works fine. I do not let Grub 1.99 get control over the Grub menu. I am confident that when the change over to Grub 2.0 comes there will not be any issues. Not on my machine.

There is still the issue of not knowing what partition we are booting into. For example, my Ubuntu Raring is listed at the top as 'Ubuntu'. My Gnome Remix Raring is listed as 'Raring Ringtail 13.04 development branch.' And I have two items called 'ubuntu 12.04.1 LTS.' But which partition are they on?

All the old kernels are in the Advanced Options sub-menu. which is a good thing and when we enter the sub-menu we get the sda designations.

I have taken to using a white plastic sheet such as we get as a divider for a ring binder. I have put numbered lines on it in ink and I write out in pencil where each OS is in the menu order. I can then erase entries as I remove or put in new installs.

It is not quite stone age but not far from it in the 21st century.

Oh, have you noticed that this



msdos1, msdos2 etc., are now the designations for sda1, sda2, etc.

Regards.

Thanks I didn't know that PPA existed :)

---

### Post by kansasnoob on 2013-01-05
My other test box doubles as a loaner while I'm fixing other peoples boxes and it's out on loan right now while I'm waiting for parts. When I get it back I'll be able to show much better how this works in a simpler multi-boot ........ like just Win XP + Precise + Quantal :D

---

### Post by oldfred on 2013-01-05
You can just list the menu entries:

       List entries in grub
cat /boot/grub/grub.cfg  | grep menuentry


> I like using this general method for creating a custom menu if my installs have any permanency whatsoever:

[http://sourceforge.net/apps/mediawik...ms:Custom_Menu]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu")
 
    

Long time ago I saw meierfra.'s Custom menu approach and I guess I was still learning grub2 at the time and did not understand it. But drs305 mentioned it in the middle of a long thread on booting ISO's from a hard drive. I found the custom menu to be much easier as the ISO's change a lot. So in my 40_custom is an entry to a custom menu for ISO on my hard drive.

```
menuentry 'Live ISOs' {
configfile (hd2,gpt4)/iso/livecdimage.cfg
} 

```

---

### Post by kansasnoob on 2013-01-05
> **oldfred said:**
> You can just list the menu entries:

       List entries in grub
cat /boot/grub/grub.cfg  | grep menuentry



Long time ago I saw meierfra.'s Custom menu approach and I guess I was still learning grub2 at the time and did not understand it. But drs305 mentioned it in the middle of a long thread on booting ISO's from a hard drive. I found the custom menu to be much easier as the ISO's change a lot. So in my 40_custom is an entry to a custom menu for ISO on my hard drive.

```
menuentry 'Live ISOs' {
configfile (hd2,gpt4)/iso/livecdimage.cfg
} 

```

I'll give that a whirl :D

This is totally off-topic but you mentioned using this:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

I'm using it on about 30 PC's with no problem and I know it'll live until April 2017 but things are changing almost so rapidly that it makes a head spin. So please do stick with 12.04 for a while :D

Or maybe I should say; keep what you know works until you're sure the next thing works, things are fluid right now:

[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)

Even since I wrote that MATE has gotten a basic thumbs-up regarding inclusion in the repos and others are still contemplating a fork of the Gnome 3 fallback session.

Must. Get. New. Time-machine :lolflag:

---

### Post by grahammechanical on 2013-01-05
> I'm curious, is there a command that a person can use to display only boot menu items as they'll actually appear on the monitor?

I am not sure if this will do what you want.

[https://help.ubuntu.com/community/Grub2/Displays#Testing_Fonts_and_Splash_Images]("https://help.ubuntu.com/community/Grub2/Displays#Testing_Fonts_and_Splash_Images")

> Rather than rebooting to test the color combinations, the user can see the changes by using GRUB 2's command line during the boot process. It is also a good way to ensure the color combinations are visible and the command settings are correct. Settings tested in a GRUB 2 terminal are not saved.

Regards.

---

### Post by kansasnoob on 2013-01-05
Just for poops and giggles:

```
lance@lance-desktop:~$  cat /boot/grub/grub.cfg | grep menuentry
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-33-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-33-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-31-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-31-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Ubuntu, with Linux 3.0.0-27-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.0.0-27-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.0.0-26-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.0.0-26-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.0.0-24-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.0.0-24-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.0.0-23-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.0.0-23-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.2.0-33-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.2.0-33-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.2.0-23-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.2.0-23-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.2.0-34-generic-pae (on /dev/sda11)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.2.0-34-generic-pae (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, kernel 3.5.0-21-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, kernel 3.5.0-21-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, kernel 3.5.0-19-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, kernel 3.5.0-19-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, kernel 3.5.0-17-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, kernel 3.5.0-17-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, memtest86+ (on /dev/sda12)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.2.0-33-generic-pae (on /dev/sda13)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.2.0-33-generic-pae (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.2.0-32-generic-pae (on /dev/sda13)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.2.0-29-generic-pae (on /dev/sda13)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda14)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda14)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), memtest86+ (on /dev/sda14)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda15)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda15)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), memtest86+ (on /dev/sda15)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, kernel 3.5.0-21-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, kernel 3.5.0-21-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a6e52bd9-488c-4f5e-8dab-59c506d246e0 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.7.0-7-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.7.0-7-generic-advanced-a6e52bd9-488c-4f5e-8dab-59c506d246e0 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.7.0-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.7.0-7-generic-recovery-a6e52bd9-488c-4f5e-8dab-59c506d246e0 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, memtest86+ (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch) (13.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic--cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic-root=UUID=cd5ab3a7-b267-437d-b917-bc75157d02bc ro single-cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), memtest86+ (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch) (13.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic--680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic-root=UUID=680f4e58-9146-4b2e-9444-40e973542c68 ro single-680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), memtest86+ (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
lance@lance-desktop:~$ 

```

Now ... wait for an edit. I'm going to change that 13.04 install to legacy grub - just enough to create a menu.lst - and I'm sure you'll see that all entries following the first one for sdb1 are supposed to be a different device/OS :D

Edit: first of all I'm going to do some badly needed kernel cleanup so it's easier to read.

---

### Post by kansasnoob on 2013-01-06
After some badly needed cleanup:

```
lance@lance-desktop:~$ cat /boot/grub/grub.cfg | grep menuentry
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Ubuntu, with Linux 3.0.0-29-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.0.0-29-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.2.0-35-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.2.0-35-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.2.0-35-generic-pae (on /dev/sda11)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, kernel 3.5.0-21-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, kernel 3.5.0-21-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.2.0-35-generic-pae (on /dev/sda13)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda14)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda14)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda15)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda15)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, kernel 3.5.0-21-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, kernel 3.5.0-21-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a6e52bd9-488c-4f5e-8dab-59c506d246e0 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.7.0-7-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.7.0-7-generic-advanced-a6e52bd9-488c-4f5e-8dab-59c506d246e0 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.7.0-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.7.0-7-generic-recovery-a6e52bd9-488c-4f5e-8dab-59c506d246e0 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, memtest86+ (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch) (13.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic--cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic-root=UUID=cd5ab3a7-b267-437d-b917-bc75157d02bc ro single-cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), memtest86+ (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch) (13.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic--680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic-root=UUID=680f4e58-9146-4b2e-9444-40e973542c68 ro single-680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), memtest86+ (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {

```

The troublesome part begins with the Raring on sdb1:

```
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a6e52bd9-488c-4f5e-8dab-59c506d246e0 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.7.0-7-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.7.0-7-generic-advanced-a6e52bd9-488c-4f5e-8dab-59c506d246e0 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.7.0-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.7.0-7-generic-recovery-a6e52bd9-488c-4f5e-8dab-59c506d246e0 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, memtest86+ (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch) (13.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic--cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic-root=UUID=cd5ab3a7-b267-437d-b917-bc75157d02bc ro single-cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), memtest86+ (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch) (13.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic--680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic-root=UUID=680f4e58-9146-4b2e-9444-40e973542c68 ro single-680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), memtest86+ (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {

```

But I now need to check out the PPA that *dino99* was talking about, and also show what happens with Quantal - it's basically the same as Raring ;)

Edit: Oops, it was *grahammechanical* that mentioned that PPA.

---

### Post by oldfred on 2013-01-06
Kansasnoob, you have a lot of entries. :)

You might want to house clean a few kernels, copy your grub.cfg into 40_custom and edit out all the recovery and extra boot entries. And turn off os-prober. Then it might be manageable.

I also like to add spacers and links to boot other drives as I have different versions of grub booting other systems that may or may not be in my 40_custom.

```
menuentry " " {
set root= 
}
menuentry "Chainboot hd1" {
set root=(hd1)
chainloader +1
}

menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

```

You mentioned grub legacy. My last entry is to my old grub legacy. I still have but do not use a grub only partition and used it to chain load to all my other installs with grub legacy in the PBR.

---

### Post by kansasnoob on 2013-01-06
Just parsing that last chunk again:

```
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a6e52bd9-488c-4f5e-8dab-59c506d246e0 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.7.0-7-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.7.0-7-generic-advanced-a6e52bd9-488c-4f5e-8dab-59c506d246e0 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.7.0-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.7.0-7-generic-recovery-a6e52bd9-488c-4f5e-8dab-59c506d246e0 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, memtest86+ (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch) (13.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic--cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic-root=UUID=cd5ab3a7-b267-437d-b917-bc75157d02bc ro single-cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), memtest86+ (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--cd5ab3a7-b267-437d-b917-bc75157d02bc (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch) (13.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic--680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic-root=UUID=680f4e58-9146-4b2e-9444-40e973542c68 ro single-680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Raring Ringtail (development branch), memtest86+ (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--680f4e58-9146-4b2e-9444-40e973542c68 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
```

After the fourth or fifith line things get garbled like this:

```
menuentry "Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) **[COLOR="Red"](on /dev/sda14)[/COLOR]**' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic-root=UUID=cd5ab3a7-b267-437d-b917-bc75157d02bc ro single-cd5ab3a7-b267-437d-b917-bc75157d02bc **[COLOR="Red"](on /dev/sdb1)[/COLOR]**" --class gnu-linux --class gnu --class os {
```

There are more garbled entries like that :(

---

### Post by kansasnoob on 2013-01-06
Hmmmm, I totally don't understand this from Raring on sdb1:

```
lance@lance-desktop:~$ cat /boot/grub/grub.cfg | grep menuentry
if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
  menuentry_id_option=""
export menuentry_id_option
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a6e52bd9-488c-4f5e-8dab-59c506d246e0' {
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-a6e52bd9-488c-4f5e-8dab-59c506d246e0' {
	menuentry 'Ubuntu, with Linux 3.7.0-7-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.7.0-7-generic-advanced-a6e52bd9-488c-4f5e-8dab-59c506d246e0' {
	menuentry 'Ubuntu, with Linux 3.7.0-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.7.0-7-generic-recovery-a6e52bd9-488c-4f5e-8dab-59c506d246e0' {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry 'Ubuntu 11.10 (11.10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-9534c4a3-d3d3-446d-af2d-fa4875c29f5c' {
submenu 'Advanced options for Ubuntu 11.10 (11.10)' $menuentry_id_option 'osprober-gnulinux-advanced-9534c4a3-d3d3-446d-af2d-fa4875c29f5c' {
	menuentry 'Ubuntu, with Linux 3.0.0-29-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-29-generic--9534c4a3-d3d3-446d-af2d-fa4875c29f5c' {
	menuentry 'Ubuntu, with Linux 3.0.0-29-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-29-generic-root=UUID=9534c4a3-d3d3-446d-af2d-fa4875c29f5c ro recovery nomodeset-9534c4a3-d3d3-446d-af2d-fa4875c29f5c' {
menuentry 'Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-0e96c168-b836-48dc-8561-288d75c3bc01' {
submenu 'Advanced options for Ubuntu 12.04.1 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-0e96c168-b836-48dc-8561-288d75c3bc01' {
	menuentry 'Ubuntu, with Linux 3.2.0-35-generic (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic--0e96c168-b836-48dc-8561-288d75c3bc01' {
	menuentry 'Ubuntu, with Linux 3.2.0-35-generic (recovery mode) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic-root=UUID=0e96c168-b836-48dc-8561-288d75c3bc01 ro recovery nomodeset-0e96c168-b836-48dc-8561-288d75c3bc01' {
menuentry 'Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-b03a64b1-370b-4e00-a510-7f7d460f3190' {
submenu 'Advanced options for Ubuntu 12.04.1 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-b03a64b1-370b-4e00-a510-7f7d460f3190' {
	menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic-pae--b03a64b1-370b-4e00-a510-7f7d460f3190' {
	menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic-pae-root=UUID=b03a64b1-370b-4e00-a510-7f7d460f3190 ro recovery nomodeset-b03a64b1-370b-4e00-a510-7f7d460f3190' {
menuentry 'Ubuntu 12.10 (12.10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf' {
submenu 'Advanced options for Ubuntu 12.10 (12.10)' $menuentry_id_option 'osprober-gnulinux-advanced-a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf' {
	menuentry 'Ubuntu 12.10, kernel 3.5.0-21-generic (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic--a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf' {
	menuentry 'Ubuntu 12.10, kernel 3.5.0-21-generic (recovery mode) (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic-root=UUID=a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf ro single-a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf' {
menuentry 'Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-86248151-b203-4971-bdc8-f095cf3a10d8' {
submenu 'Advanced options for Ubuntu 12.04.1 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-86248151-b203-4971-bdc8-f095cf3a10d8' {
	menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic-pae--86248151-b203-4971-bdc8-f095cf3a10d8' {
	menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode) (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic-pae-root=UUID=86248151-b203-4971-bdc8-f095cf3a10d8 ro recovery nomodeset-86248151-b203-4971-bdc8-f095cf3a10d8' {
menuentry 'Ubuntu Raring Ringtail (development branch) (13.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-cd5ab3a7-b267-437d-b917-bc75157d02bc' {
submenu 'Advanced options for Ubuntu Raring Ringtail (development branch) (13.04)' $menuentry_id_option 'osprober-gnulinux-advanced-cd5ab3a7-b267-437d-b917-bc75157d02bc' {
	menuentry 'Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic--cd5ab3a7-b267-437d-b917-bc75157d02bc' {
	menuentry 'Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic-root=UUID=cd5ab3a7-b267-437d-b917-bc75157d02bc ro single-cd5ab3a7-b267-437d-b917-bc75157d02bc' {
menuentry 'Ubuntu Raring Ringtail (development branch) (13.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-680f4e58-9146-4b2e-9444-40e973542c68' {
submenu 'Advanced options for Ubuntu Raring Ringtail (development branch) (13.04)' $menuentry_id_option 'osprober-gnulinux-advanced-680f4e58-9146-4b2e-9444-40e973542c68' {
	menuentry 'Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic--680f4e58-9146-4b2e-9444-40e973542c68' {
	menuentry 'Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic-root=UUID=680f4e58-9146-4b2e-9444-40e973542c68 ro single-680f4e58-9146-4b2e-9444-40e973542c68' {
menuentry 'Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-c1dc4187-4170-406f-8b8e-c1a3904e1315' {
submenu 'Advanced options for Ubuntu 12.04.1 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-c1dc4187-4170-406f-8b8e-c1a3904e1315' {
	menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic-pae--c1dc4187-4170-406f-8b8e-c1a3904e1315' {
	menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode) (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic-pae-root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro recovery nomodeset-c1dc4187-4170-406f-8b8e-c1a3904e1315' {
menuentry 'Ubuntu 12.10 (12.10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-7c4147e0-e51a-4e42-a243-d07e7300b7fe' {
submenu 'Advanced options for Ubuntu 12.10 (12.10)' $menuentry_id_option 'osprober-gnulinux-advanced-7c4147e0-e51a-4e42-a243-d07e7300b7fe' {
	menuentry 'Ubuntu 12.10, kernel 3.5.0-21-generic (on /dev/sda3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic--7c4147e0-e51a-4e42-a243-d07e7300b7fe' {
	menuentry 'Ubuntu 12.10, kernel 3.5.0-21-generic (recovery mode) (on /dev/sda3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic-root=UUID=7c4147e0-e51a-4e42-a243-d07e7300b7fe ro single-7c4147e0-e51a-4e42-a243-d07e7300b7fe' {
```

But wait ;)

Edit: I actually think I do get it ......... just ignore the "submenu" stuff and that's about what the actual boot menu looks like.

---

### Post by kansasnoob on 2013-01-06
No noticeable change after recent Raring updates:

```
lance@lance-desktop:~$ cat /boot/grub/grub.cfg | grep menuentry
if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
  menuentry_id_option=""
export menuentry_id_option
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a6e52bd9-488c-4f5e-8dab-59c506d246e0' {
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-a6e52bd9-488c-4f5e-8dab-59c506d246e0' {
	menuentry 'Ubuntu, with Linux 3.7.0-7-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.7.0-7-generic-advanced-a6e52bd9-488c-4f5e-8dab-59c506d246e0' {
	menuentry 'Ubuntu, with Linux 3.7.0-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.7.0-7-generic-recovery-a6e52bd9-488c-4f5e-8dab-59c506d246e0' {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry 'Ubuntu 11.10 (11.10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-9534c4a3-d3d3-446d-af2d-fa4875c29f5c' {
submenu 'Advanced options for Ubuntu 11.10 (11.10)' $menuentry_id_option 'osprober-gnulinux-advanced-9534c4a3-d3d3-446d-af2d-fa4875c29f5c' {
	menuentry 'Ubuntu, with Linux 3.0.0-29-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-29-generic--9534c4a3-d3d3-446d-af2d-fa4875c29f5c' {
	menuentry 'Ubuntu, with Linux 3.0.0-29-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-29-generic-root=UUID=9534c4a3-d3d3-446d-af2d-fa4875c29f5c ro recovery nomodeset-9534c4a3-d3d3-446d-af2d-fa4875c29f5c' {
menuentry 'Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-0e96c168-b836-48dc-8561-288d75c3bc01' {
submenu 'Advanced options for Ubuntu 12.04.1 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-0e96c168-b836-48dc-8561-288d75c3bc01' {
	menuentry 'Ubuntu, with Linux 3.2.0-35-generic (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic--0e96c168-b836-48dc-8561-288d75c3bc01' {
	menuentry 'Ubuntu, with Linux 3.2.0-35-generic (recovery mode) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic-root=UUID=0e96c168-b836-48dc-8561-288d75c3bc01 ro recovery nomodeset-0e96c168-b836-48dc-8561-288d75c3bc01' {
menuentry 'Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-b03a64b1-370b-4e00-a510-7f7d460f3190' {
submenu 'Advanced options for Ubuntu 12.04.1 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-b03a64b1-370b-4e00-a510-7f7d460f3190' {
	menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic-pae--b03a64b1-370b-4e00-a510-7f7d460f3190' {
	menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode) (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic-pae-root=UUID=b03a64b1-370b-4e00-a510-7f7d460f3190 ro recovery nomodeset-b03a64b1-370b-4e00-a510-7f7d460f3190' {
menuentry 'Ubuntu 12.10 (12.10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf' {
submenu 'Advanced options for Ubuntu 12.10 (12.10)' $menuentry_id_option 'osprober-gnulinux-advanced-a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf' {
	menuentry 'Ubuntu 12.10, kernel 3.5.0-21-generic (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic--a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf' {
	menuentry 'Ubuntu 12.10, kernel 3.5.0-21-generic (recovery mode) (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic-root=UUID=a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf ro single-a5f9484a-70d0-4e30-afa8-f7c8a1bc25bf' {
menuentry 'Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-86248151-b203-4971-bdc8-f095cf3a10d8' {
submenu 'Advanced options for Ubuntu 12.04.1 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-86248151-b203-4971-bdc8-f095cf3a10d8' {
	menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic-pae--86248151-b203-4971-bdc8-f095cf3a10d8' {
	menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode) (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic-pae-root=UUID=86248151-b203-4971-bdc8-f095cf3a10d8 ro recovery nomodeset-86248151-b203-4971-bdc8-f095cf3a10d8' {
menuentry 'Ubuntu Raring Ringtail (development branch) (13.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-cd5ab3a7-b267-437d-b917-bc75157d02bc' {
submenu 'Advanced options for Ubuntu Raring Ringtail (development branch) (13.04)' $menuentry_id_option 'osprober-gnulinux-advanced-cd5ab3a7-b267-437d-b917-bc75157d02bc' {
	menuentry 'Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic--cd5ab3a7-b267-437d-b917-bc75157d02bc' {
	menuentry 'Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic-root=UUID=cd5ab3a7-b267-437d-b917-bc75157d02bc ro single-cd5ab3a7-b267-437d-b917-bc75157d02bc' {
menuentry 'Ubuntu Raring Ringtail (development branch) (13.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-680f4e58-9146-4b2e-9444-40e973542c68' {
submenu 'Advanced options for Ubuntu Raring Ringtail (development branch) (13.04)' $menuentry_id_option 'osprober-gnulinux-advanced-680f4e58-9146-4b2e-9444-40e973542c68' {
	menuentry 'Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic--680f4e58-9146-4b2e-9444-40e973542c68' {
	menuentry 'Ubuntu Raring Ringtail (development branch), kernel 3.7.0-7-generic (recovery mode) (on /dev/sda15)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.7.0-7-generic-root=UUID=680f4e58-9146-4b2e-9444-40e973542c68 ro single-680f4e58-9146-4b2e-9444-40e973542c68' {
menuentry 'Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-c1dc4187-4170-406f-8b8e-c1a3904e1315' {
submenu 'Advanced options for Ubuntu 12.04.1 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-c1dc4187-4170-406f-8b8e-c1a3904e1315' {
	menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic-pae--c1dc4187-4170-406f-8b8e-c1a3904e1315' {
	menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode) (on /dev/sda2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-35-generic-pae-root=UUID=c1dc4187-4170-406f-8b8e-c1a3904e1315 ro recovery nomodeset-c1dc4187-4170-406f-8b8e-c1a3904e1315' {
menuentry 'Ubuntu 12.10 (12.10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-7c4147e0-e51a-4e42-a243-d07e7300b7fe' {
submenu 'Advanced options for Ubuntu 12.10 (12.10)' $menuentry_id_option 'osprober-gnulinux-advanced-7c4147e0-e51a-4e42-a243-d07e7300b7fe' {
	menuentry 'Ubuntu 12.10, kernel 3.5.0-21-generic (on /dev/sda3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic--7c4147e0-e51a-4e42-a243-d07e7300b7fe' {
	menuentry 'Ubuntu 12.10, kernel 3.5.0-21-generic (recovery mode) (on /dev/sda3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic-root=UUID=7c4147e0-e51a-4e42-a243-d07e7300b7fe ro single-7c4147e0-e51a-4e42-a243-d07e7300b7fe' {

```

---

### Post by kansasnoob on 2013-01-06
Here's a better photo of a typical Quantal or Raring multi-boot menu:

[ATTACH]229699[/ATTACH]

You can see there are no device designations, but I've figured out that if I choose the "advanced option" just below any menu item then I can read the device designation and the just Esc back to the menu and proceed.

It's sloppy but it gets the job done ;)

---

### Post by kansasnoob on 2013-01-06
Finally got around to testing the Precise version of grub2 from this PPA:

[https://launchpad.net/~cjwatson/+archive/grub](https://launchpad.net/~cjwatson/+archive/grub)

It cures the "long and sometimes nonsensical menu entries" problem but displays no device designations so it's not a real solution.

---

### Post by monkeybrain2012 on 2013-01-18
> **kansasnoob said:**
> Finally got around to testing the Precise version of grub2 from this PPA:

[https://launchpad.net/~cjwatson/+archive/grub](https://launchpad.net/~cjwatson/+archive/grub)

It cures the "long and sometimes nonsensical menu entries" problem but displays no device designations so it's not a real solution.

Thanks! Installing the ppa in Precise finally solves my problem.

[http://ubuntuforums.org/showthread.php?t=2077707](http://ubuntuforums.org/showthread.php?t=2077707)

But installing from the ppa remove apport, which is not a big deal anyhow.

Edited:
It seems that I had grub 1.99.2.1 from precise proposed I could have solved the problem by downgrading.

---

