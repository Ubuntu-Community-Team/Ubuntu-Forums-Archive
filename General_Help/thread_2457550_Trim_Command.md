---
title: "Trim Command"
date: 2021-02-04
forum: General Help
---

### Post by scriber on 2021-02-04
I have an nvme drive with 5 partitions ( different OS's ) and when I run the trim command, does that just trim the running OS partition or does it trim all partitions, ie the whole drive ?

The command I'm using is   sudo fstrim -a -v

Just curious to know !

---

### Post by Dennis N on 2021-02-04
> **scriber said:**
> I have an nvme drive with 5 partitions ( different OS's ) and when I run the trim command, does that just trim the running OS partition or does it trim all partitions, ie the whole drive ?

The command I'm using is   sudo fstrim -a -v

Just curious to know !
It will trim / and **mounted** partitions. I let systemd manage the trim. The results are in the systemd journal:
```
dmn@Tyana-vm:~$ journalctl | grep fstrim
Dec 28 06:11:02 Tyana-vm fstrim[590]: /mnt/Common-Files: 7.9 GiB (8482734080 bytes) trimmed on /dev/vdb1
Dec 28 06:11:02 Tyana-vm fstrim[590]: /: 7.4 GiB (7945121792 bytes) trimmed on /dev/vda2
Dec 28 06:11:02 Tyana-vm fstrim[590]: /boot/efi: 71 MiB (74432000 bytes) trimmed on /dev/vda1
```
/mnt/Common-Files is my shared data partition on another disk.

---

### Post by scriber on 2021-02-04
So I guess I would just trim the OS that is mounted then, as the other OS's are hidden, and when I check it shows the other partitions as unallocated.

Thanks for the reply, much appreciated !

---

### Post by Dennis N on 2021-02-04
Right. You only trim the OS in use + anything mounted to it at the time the trim is run. I notice the EFI system partition is also trimmed. I missed copying that line (I have edited the original post). You can always run the command shown and see what was trimmed. See below. 

```

dmn@Tyana-vm:~$ journalctl | grep trim
Dec 28 06:11:02 Tyana-vm fstrim[590]: /mnt/Common-Files: 7.9 GiB (8482734080 bytes) trimmed on /dev/vdb1
Dec 28 06:11:02 Tyana-vm fstrim[590]: /boot/efi: 71 MiB (74432000 bytes) trimmed on /dev/vda1
Dec 28 06:11:02 Tyana-vm fstrim[590]: /: 7.4 GiB (7945121792 bytes) trimmed on /dev/vda2

```

---

### Post by scriber on 2021-02-04
Okay, thanks for the useful info !

---

