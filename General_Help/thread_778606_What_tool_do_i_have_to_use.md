---
title: "What tool do i have to use?"
date: 2008-05-02
forum: General Help
---

### Post by reyhan on 2008-05-02
Hello i just finished download System rescue CD and i want 
to reinstall the MBR what tool do i have to use...? , 
Because i dont have Windows xp Cd...

---

### Post by Vermind on 2008-05-02
Hello,
hmm, so what is Your setup?
If You have an Ubuntu/Windows dual boot, Your MBR has GRUB, and fixing that is done with grub-install.
If Your Windows refuses to boot, then Your Windows boot record on the Windows partition might be broken. If you want to fix that, the best way to go is a Windows XP cd, and the fixboot command. There are also other cds, free to download, that are able to fix Windows boot.
This is also possible from Linux with a tool called msys, though I cannot give any guarantees on it.

---

### Post by Zorael on 2008-05-02
[list][*]To restore a "standard" MBR (such as Window's), I'd suggest you download **testdisk** from the repositories and run it as superuser. You'll need to enable the universe repos under Software Sources (or in Synaptic).
```
$ sudo aptitude install testdisk
$ sudo testdisk
```
Choose if you want to log your actions (irrelevant), pick your harddrive, choose Intel (unless you're on a Mac), then MBR Code. Done.


[*]To restore GRUB, do this.
```
$ sudo grub
> find /boot/grub/stage1
> root *<whatever was listed by the above command, such as (hd0,0)>*
> setup *<whatever was listed by the above command BUT only the first digit, such as (hd0)>*
> quit
$ sudo update-grub
$ sudo update-initramfs -u -k all
```
Done.[/list]

---

