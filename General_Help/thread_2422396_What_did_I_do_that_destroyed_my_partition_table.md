---
title: "What did I do that destroyed my partition table?"
date: 2019-07-07
forum: General Help
---

### Post by khanson679 on 2019-07-07
While trying to debug/fix various things I inadvertently destroyed the partition table on my SSD (sdb), which has since been fixed. Now I'm trying to figure out what it is that might have been the problem. I saved my shell history (abridged), which I'll paste below. Other than that, I also resized a couple of LVM logical volumes in KDE Partition Manager (a neat new feature). Any ideas?

```

381  man hdparm
382  hdparm  -t
383  hdparm -t /dev/sdb
...
390  sudo hdparm -t /dev/sdb
...
401  fstrim /dev/sba
402  fstrim /dev/sdb
403  man fstrim
404  sudo fstrim -a
405  sudo hdparm -t /dev/sdb
406  lvmdiskscan
407  sudo lvmdiskscan
408  sudo lvdisplay 
409  kate /etc/lvm/lvm.conf
410  cryptsetup benchmark
411  cryptsetup status
412  cryptsetup status luks-data
413  sudo cryptsetup status luks-main
...
418  dd if=/dev/zero of=tempfile bs=1M count=1024 conv=fdatasync,notrunc
419  rm temp
420  rm tempfile
421  cryptsetup
422  cryptsetup status
...
427  sudo apt install flashbench
428  flashbench
429  flashbench -a /dev/sdb
430  sudo flashbench -a /dev/sdb
431  sudo flashbench -a /dev/sdb --blocksize=1024
432  man flashbench
...
440  flashbench | less
441  flashbench -h
442  sudo flashbench /dev/sdb
443  sudo flashbench -f /dev/sdb
444  kate /etc/lvm/lvm.conf
445  vgdisplay vg1
446  sudo vgdisplay vg1
447  pvscan
448  sudo pvscan
449  sudo pvscan -v
450  man pvsan
451  man pvscan
452  sudo pvscan -vvv
453  sudo pvscan -vv
454  cat /etc/initramfs-tools/modules
455  sudo smartctl /dev/sda -a
456  sudo apt install smartmontools
457  sudo aptfile search 
458  sudo apt-file search 
459  sudo apt-cache search smartctl
460  sudo apt install smartmontools
...
470  sudo smartctl /dev/sda -a
471  sudo smartctl /dev/sdb -a
472  cat /etc/crypt
473  cat /etc/crypttab
...
482  sudo grub-install /dev/sdb1
483  sudo grub-install /dev/sdb
484  man update-grub
485  man grub-mkconfig
486  man grub-install
487  kate /etc/grub.d/30_uefi-firmware 
488  sudo grub-install --target=x86_64-efi
489  cat /boot/grub/device.map 
490  cat /boot/grub/grub.cfg
491  ll /boot/efi
492  man grub-set-default
493  man grub-probe
494  sudo grub-probe
495  sudo grub-probe /dev/sdb
496  sudo grub-probe /dev/sdb1
...
499  sudo grub-probe
500  sudo grub-probe -d /dev/sdb
501  sudo grub-probe -d /dev/sdb1
...
510  man grub-probe
511  sudo ls /boot/efi
512  sudo ls /boot/efi/EFI
513  sudo ls /boot/efi/EFI/ubuntu
514  man efibootmgr
515  cat /etc/fstab
516  [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 
517  sudo mount /dev/sdb1 /mount/efi2
518  sudo mkdir sdbefi
519  sudo rmdir sdbefi
520  sudo mkdir /mnt/sdbefi
521  sudo mount /dev/sdb1 /mnt/sdbefi
522  man mount
523  sudo mount -t fat32 /dev/sdb1 /mnt/sdbefi
524  sudo mount -t fat /dev/sdb1 /mnt/sdbefi
525  man moun
526  man mount
527  fsck.vfat /dev/sdb1
528  sudo fsck.vfat /dev/sdb1
529  sudo mount -t vfat /dev/sdb1 /mnt/sdbefi
530  fdisk -l /dev/sdb
531  sudo fdisk -l /dev/sdb
532  lsblk
533  man fdisk
534  parted
535  sudo parte
536  sudo parted
537  history

```

[s] EDIT: apologies, but I cannot figure out how to keep the forum software from eating all the line breaks. Google is no help either. I have the source in a text editor, so I will fix it if someone tells me how. [/s]

EDIT: Formatting should be fixed now.

---

### Post by freemedia2018 on 2019-07-07
I can't figure out why your code tags didnt work:

```
 
381  man hdparm 
382  hdparm  -t 
383  hdparm -t /dev/sdb ... 
390  sudo hdparm -t /dev/sdb ... 
401  fstrim /dev/sba 
402  fstrim /dev/sdb 
403  man fstrim 
404  sudo fstrim -a 
405  sudo hdparm -t /dev/sdb 
406  lvmdiskscan 
407  sudo lvmdiskscan 
408  sudo lvdisplay  
409  kate /etc/lvm/lvm.conf 
410  cryptsetup benchmark 
411  cryptsetup status 
412  cryptsetup status luks-data 
413  sudo cryptsetup status luks-main ... 
418  dd if=/dev/zero of=tempfile bs=1M count=1024 conv=fdatasync,notrunc 
419  rm temp 
420  rm tempfile 
421  cryptsetup 
422  cryptsetup status ... 
427  sudo apt install flashbench 
428  flashbench 
429  flashbench -a /dev/sdb 
430  sudo flashbench -a /dev/sdb 
431  sudo flashbench -a /dev/sdb --blocksize=1024 
432  man flashbench ... 
440  flashbench | less 
441  flashbench -h 
442  sudo flashbench /dev/sdb 
443  sudo flashbench -f /dev/sdb 
444  kate /etc/lvm/lvm.conf 
445  vgdisplay vg1 
446  sudo vgdisplay vg1 
447  pvscan 
448  sudo pvscan 
449  sudo pvscan -v 
450  man pvsan 
451  man pvscan
452  sudo pvscan -vvv 
453  sudo pvscan -vv 
454  cat /etc/initramfs-tools/modules 
455  sudo smartctl /dev/sda -a 
456  sudo apt install smartmontools 
457  sudo aptfile search  
458  sudo apt-file search  
459  sudo apt-cache search smartctl 
460  sudo apt install smartmontools ... 
470  sudo smartctl /dev/sda -a 
471  sudo smartctl /dev/sdb -a 
472  cat /etc/crypt 
473  cat /etc/crypttab ... 
482  sudo grub-install /dev/sdb1 
483  sudo grub-install /dev/sdb 
484  man update-grub 
485  man grub-mkconfig 
486  man grub-install 
487  kate /etc/grub.d/30_uefi-firmware  
488  sudo grub-install --target=x86_64-efi 
489  cat /boot/grub/device.map  
490  cat /boot/grub/grub.cfg 
491  ll /boot/efi 
492  man grub-set-default 
493  man grub-probe 
494  sudo grub-probe 
495  sudo grub-probe /dev/sdb 
496  sudo grub-probe /dev/sdb1 ... 
499  sudo grub-probe 
500  sudo grub-probe -d /dev/sdb 
501  sudo grub-probe -d /dev/sdb1 ... 
510  man grub-probe 
511  sudo ls /boot/efi 
512  sudo ls /boot/efi/EFI 
513  sudo ls /boot/efi/EFI/ubuntu 
514  man efibootmgr 
515  cat /etc/fstab 
516  [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"  
517  sudo mount /dev/sdb1 /mount/efi2 
518  sudo mkdir sdbefi 
519  sudo rmdir sdbefi 
520  sudo mkdir /mnt/sdbefi 
521  sudo mount /dev/sdb1 /mnt/sdbefi 
522  man mount 
523  sudo mount -t fat32 /dev/sdb1 /mnt/sdbefi 
524  sudo mount -t fat /dev/sdb1 /mnt/sdbefi 
525  man moun 
526  man mount 
527  fsck.vfat /dev/sdb1 
528  sudo fsck.vfat /dev/sdb1 
529  sudo mount -t vfat /dev/sdb1 /mnt/sdbefi 
530  fdisk -l /dev/sdb 
531  sudo fdisk -l /dev/sdb 
532  lsblk 
533  man fdisk 
534  parted 
535  sudo parte 
536  sudo parted 
537  history 
```

---

### Post by khanson679 on 2019-07-08
Figured out the formatting problem! It was NoScript. It also blocks the fancy editor, but I would have expected such things to work even without that. (I'll fix the original post now.)

---

