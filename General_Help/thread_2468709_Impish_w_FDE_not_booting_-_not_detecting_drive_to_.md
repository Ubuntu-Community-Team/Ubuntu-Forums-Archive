---
title: "Impish w/ FDE not booting - not detecting drive to decrypt"
date: 2021-11-08
forum: General Help
---

### Post by fragged on 2021-11-08
I moved to Ubuntu 21.10 and ever since then, I'm unable to boot without manually decrypting the NVME partition where Ubuntu is installed. My partition layout is as follows:

[HTML]
/dev/nvme0
/dev/nvme0n1 # Encrypted non-bootable volume
/dev/nvme1
/dev/nvme1n1
/dev/nvme1n1p1 # EFI
/dev/nvme1n1p2 # Grub
/dev/nvme1n1p3 # Ubuntu install 
[/HTML]

When starting up, my system drops me to an init emergency shell, from there I type 

[HTML]
cryptsetup /dev/nvme1n1p3 somename
exit
[HTML]

at which point my system continues through the boot process.

My grub.cfg is as follows

[HTML]menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-366041df-2bf9-44dc-a97a-efcf22d3c096' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_gpt
	insmod ext2
	if [ x$feature_platform_search_hint = xy ]; then
	 search --no-floppy --fs-uuid --set=root  69a0107e-6072-4294-b84a-71f62d58e0da
	else
	 search --no-floppy --fs-uuid --set=root 69a0107e-6072-4294-b84a-71f62d58e0da
	fi
	linux	/vmlinuz-5.13.0-21-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro  
	initrd	/initrd.img-5.13.0-21-generic
}[/HTML]

I'm not super familiar with the inner workings of  grub, historically I remember needing crypt_root, but I've checked on other devices and that is  no longer the case.


How can I fix this? :(

---

