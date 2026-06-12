---
title: "Booting encrypted squashfs filesystem with busybox + dropbear ssh"
date: 2014-01-02
forum: General Help
---

### Post by stufn on 2014-01-02
I'm trying to boot a custom ubuntu live cd image  manually. It loads fine if just boot a virtual machine with the iso. However, I also need to boot it manually. For this purpose I installed dropbear so I can ssh into the VM from the host. I get a busybox shell and enter the following commands:

```

/sbin/cryptsetup luksOpen /dev/loop0 luksloop
mount -t ext3 /dev/mapper/luksloop /mnt
losetup /dev/loop1 /mnt/filesystem.squashfs
mkdir /filesystem.squashfs
mount -t squashfs /dev/loop1  /filesystem.squashfs 
mount --move /sys /filesystem.squashfs/sys
mount --move /proc /filesystem.squashfs/proc
mount --move /dev /filesystem.squashfs/dev
```


As you can see the original filesystem.squashfs is encrypted. The container is opened and the unencrypted filesystem which resides in the container is then mounted. My (new) root file system is now mounted at /filesystem.squashfs. But I don't know how to go from there. I tried stuff like switch_root or run-init but I could not boot the system. I don't even know if I need these commands :confused:. 

If I go the 'VM-only-way" without ssh into the vm, I just press ctrl + F1 to get a terminal. Enter my password and the VM continues booting. But if I go the "ssh-way" and enter "echo password > /dev/tty1" the password just is printed on the command line in the vm but not entered into the password prompt. This would probably be the easiest way to boot the vm, but I guess I am also doing something wrong there :|

---

### Post by stufn on 2014-01-03
bump

---

