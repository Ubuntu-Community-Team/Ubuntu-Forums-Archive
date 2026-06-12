---
title: "grub rescue error: no such partition"
date: 2019-07-10
forum: General Help
---

### Post by mortenbolstad on 2019-07-10
Hello

So I have recently bought an old Asus Eee PC Seashell series laptop and on it, I have windows 10 and ubuntu mate.

I think that the problem is that I deleted the partition of the D drive on windows and grub can only work if both partitions are there since both partitions were there when I installed ubuntu mate. But I am no expert so I have no idea if this is the real reason that I have this problem.

I can get into the grub menu with the lines below but I don't want to type this every time I want to use the laptop
[B]set boot=(hd0,msdos5)
set prefix=(hd0,msdos5)/boot/grub
insmod normal
normal[/B]

Grub versjon=2.02

---

### Post by oldfred on 2019-07-10
If entry in fstab, you need to edit that. Can just add # to beginning of line to convert to comment or delete.

Compare UUID to UUIDs in fstab.
Shows UUIDs by partition:
lsblk -f
sudoedit /etc/fstab
or 
sudo nano /etc/fstab

---

### Post by Impavidus on 2019-07-11
My guess: Deleting one partition changed the numbers of other partitions. That probably happens when you use logical partitions on an mbr drive. Not very common on Win10 systems, but it may the case here.

It seems that you still manage to boot Ubuntu. Check the UUIDs in /etc/fstab as oldfred indicated and update grub:```
sudo update-grub
```

---

