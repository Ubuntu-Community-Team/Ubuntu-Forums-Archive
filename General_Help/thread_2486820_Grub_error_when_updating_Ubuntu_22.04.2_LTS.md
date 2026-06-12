---
title: "Grub error when updating Ubuntu 22.04.2 LTS"
date: 2023-05-12
forum: General Help
---

### Post by tolomea33 on 2023-05-12
I have a 22.04 install that is very generic.
It's on a Thinkpad, single boot with drive encryption, I've never tinkered with any of the partitioning or grub stuff, or much else, it's my work machine, so mostly chrome, sublime and python.
The other day I did normal package updates and got a grub error, unfortunately I don't have that error, but it's made me very nervous about rebooting.
I tried grub-emu and the grub menu comes up but it fails when selecting Ubutnu with
```

error: sparse file not allowed.
error: no such device: 33f85d1765e46c75
error: can't find command `linux'.
error: can't find command `initrd'.

```

Is this a problem? what will happen if I reboot?


Other info:

in /dev/disk/by-uuid/ I have
```

3418580241224042994 -> ../../nvme0n1p4
3744845445233667189 -> ../../nvme0n1p3
6ccd863d-f4c5-47dc-af54-34a8165f7f7e -> ../../dm-0
7624fd34-c1b1-45a9-ac93-8a151db99e5b -> ../../dm-1
A68D-0A8E -> ../../nvme0n1p1
c99ff2d3-f6b5-4d5e-8dda-b3eb0e576e25 -> ../../zd0

```

I note that 3744845445233667189 is the decimal equiv of 33f85d1765e46c75

sudo update-grub
```

Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: vmlinuz-5.19.0-41-generic in rpool/ROOT/ubuntu_58gwiz
Found initrd image: initrd.img-5.19.0-41-generic in rpool/ROOT/ubuntu_58gwiz
Found linux image: vmlinuz-5.19.0-40-generic in rpool/ROOT/ubuntu_58gwiz
Found initrd image: initrd.img-5.19.0-40-generic in rpool/ROOT/ubuntu_58gwiz
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done

```


sudo grub-install --recheck
```

Installing for x86_64-efi platform.
Installation finished. No error reported.

```


uname -a
```

Linux Lappy-E15 5.19.0-40-generic #41~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Fri Mar 31 16:00:14 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by tolomea33 on 2023-05-12
actually grub-emu fails immediately with the below, then when selecting Ubuntu it does the above

error: can't  find command `hwmatch'.
error: sparse file not allowed.
error: no such device: 33f85d1765e46c75
error: can't find command `linux'.
error: can't find command `initrd'.

---

### Post by MAFoElffen on 2023-05-13
Well, if I use grub-emu... (grub emulator) The Grub Menu displays, like it should... Though If I press enter, I get the same messages, even though my Grub Menu is fine.

Try to reboot, and see if it works. It may just be normal. The message on not finding things may just be that the same env vars do not exist from a terminal windows, as they do on a fresh boot, solely from grub.

---

