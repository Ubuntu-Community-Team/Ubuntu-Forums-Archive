---
title: "Use grub4dos to boot ubuntu 18.04"
date: 2018-08-14
forum: General Help
---

### Post by dunhill- on 2018-08-14
[COLOR=#242729][FONT=Arial][CENTER]
[/CENTER]
[/FONT][/COLOR]Iam using grub4dos 0.4.4 to boot Ubuntu 17.04 successfully. Here are lines inthe file MENU.LST
 
*  title Ubuntu 17 (64bit)*
*  fallback 6*
*  find --set-root /iso/ubt1704.iso*
*  map --mem /iso/ubt1704.iso (0xff) || map--heads=0 --sectors-per-track=0 /iso/ubt1704.iso (0xff)*
*  map --hook*
*  root (0xff)*
*  kernel /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casperiso-scan/filename=/iso/ubt1704.iso splash*
*  initrd /casper/initrd.lz*
 
Butfor Ubuntu 18.04, they did not work. The computer restarted after menu Ubuntu18.04 was selected.
 
Pleasehelp me to fix the problem. Thanks in advanced.

---

### Post by oldfred on 2018-08-14
for a while they have used this -*/casper/vmlinuz.efi *, but old versions and now 18.04 use this: [I]/casper/vmlinuz

[/I]I use grub2 to loopmount ISO. I changed my 18.10 to use the label of the partition where I have my ISO on SSD. My old specific device has been changing as I now have several USB drives which may or may not be active and then boot drive number in grub changes.
       [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot) 

    ```

menuentry "Ubuntu 18.04 Bionic amd64" {
    set isofile="/ubuntu-18.04-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd0,5)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile toram
    initrd (loop)/casper/initrd.lz
}


menuentry "Ubuntu 18.10 Cosmic Daily amd64" {
    set isofile="/cosmic-desktop-amd64.iso"
    insmod part_gpt
    search --set=root --label iso_ssd --hint hd0,gpt5
    loopback loop (${root})$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile toram
    initrd (loop)/casper/initrd
}

```

---

### Post by dunhill- on 2018-08-14
> **oldfred said:**
> 
for a while they have used this -*/casper/vmlinuz.efi *, but old versions and now 18.04 use this: [I]/casper/vmlinuz
[/I]

Thank you so much for your idea.

I have changed the content of MENU.LST as bellow and it worked.

    [I]find --set-root /iso/ubt1804.iso
    map --mem /iso/ubt1804.iso (0xff) || map --heads=0 --sectors-per-track=0 /iso/ubt1804.iso (0xff)
    map --hook
    root (0xff)
    kernel **/casper/vmlinuz**  file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/iso/ubt1804.iso splash
    initrd /casper/initrd.lz[/I]

---

### Post by C.S.Cameron on 2018-08-15
vmlinuz.efi was used for Ubuntu 64bit from 14.04 to 17.10.
With 18.04 it is back to vmlinuz.

vmlinuz has always been used for 32bit.

---

