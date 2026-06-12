---
title: "GRUB loader / Boot-Repair / GRUB2 / Login LOOP"
date: 2020-02-08
forum: General Help
---

### Post by kemelbek123 on 2020-02-08
Hi all! 
Recently I've deleted windows partition from my Lenovo Z50-70 laptop, which lead to crushing of GRUB loader. I tried to install boot-repair and fix the issue, however the resulting message now is [HTML]Please enable a repository containing the [grub2] packages in the software sources of Ubuntu 18.04.3 LTS (sda1). Then try again.[/HTML]

After manually installing GRUB loader by ```
  sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev/
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
grub-install /dev/sda
grub-install --recheck /dev/sda
update-grub
exit
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev/pts

```

I got stuck at Login LOOP

Please, help me regain access to Ubuntu.

Here is boot-repair summary, which may be useful: [http://paste.ubuntu.com/p/jdZzvTDKSG/](http://paste.ubuntu.com/p/jdZzvTDKSG/)

---

### Post by cmcanulty on 2020-02-08
I successfully fixed the login loop using this fix from the web

[https://www.maketecheasier.com/fix-ubuntu-login-loop/]("https://www.maketecheasier.com/fix-ubuntu-login-loop/")

---

### Post by yancek on 2020-02-08
I'm not sure what you did but deleting a windows partition should have absolutely no effect on the Grub bootloader since none of the Grub files should ever be on a windows partition.  Which windows OS did you have?  Was it an older windows non UEFI? Or windows 8/10?  Did you enable a repository with Grub files as suggested and if so, which one.  I see there is another post while writing this, hopefully that suggestion will help.

---

