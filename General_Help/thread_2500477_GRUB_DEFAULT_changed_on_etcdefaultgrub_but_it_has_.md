---
title: "GRUB_DEFAULT changed on /etc/default/grub but it has no effect (I did update-grub)"
date: 2024-09-03
forum: General Help
---

### Post by nicoeverquest on 2024-09-03
Hello all

I have installed a new version of the kernel, just to test, I don't want to boot on it by default.


I want to boot on my previous kernel, so I change


GRUB_DEFAULT="1>2"



In the /etc/default/grub file


1>2 is the default ubuntu 24.04 kernek which is 6.8


And then of course i do update-grub


But when I reboot, select the first entry "ubuntu" stil boot on the newest kernel.


On my /boot/grub.cfg I see :


menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-1cd1e1a5-61f4-4207-b60f-dbf239eafb78' {
	recordfail
	savedefault
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_gpt
	insmod ext2
	search --no-floppy --fs-uuid --set=root 1cd1e1a5-61f4-4207-b60f-dbf239eafb78
	linux	/boot/vmlinuz-6.10.7 root=UUID=1cd1e1a5-61f4-4207-b60f-dbf239eafb78 ro  quiet splash systemd.restore_state=0 $vt_handoff
	initrd	/boot/initrd.img-6.10.7
}



Grub still associates my newest kernel 6.10.7 to the Ubuntu entry...


Any clue?


Thanks

---

### Post by tea for one on 2024-09-03
> **nicoeverquest said:**
> But when I reboot, select the first entry "ubuntu" stil boot on the newest kernel.
If you select the first entry, you choose the latest installed kernel i.e. you have overridden your recent grub edit.
Reboot and do not select anything.
Your new choice should be respected if you have the correct syntax in /etc/default/grub.

---

### Post by nicoeverquest on 2024-09-03
OK I understrand what you mean.  I will keep the default "ubuntu" entry behavior et move my newest kernel, that I don't want to use anyway, out from the /boot directory
thanks

---

### Post by tea for one on 2024-09-03
Playing around with kernels (adding/moving/deleting) may lead to unintended consequences.
e.g. unable to boot the PC

Please ensure that you have recent backups of your personal data.

---

