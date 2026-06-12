---
title: "mounting iso"
date: 2006-10-17
forum: General Help
---

### Post by Magiczero on 2006-10-17
Hi

I want to put dsl on my flash drive and I read that I have to mount the iso and then copy the files to my flash drive i have used this comand and I get an error:

[QUOTEtanner@tanner-desktop:~$ mkdir /mnt/iso
mkdir: cannot create directory `/mnt/iso': Permission denied
tanner@tanner-desktop:~$ mount -o loop ds.iso /mnt/iso
mount: only root can do that
tanner@tanner-desktop:~$ mkdir /mnt/iso
mkdir: cannot create directory `/mnt/iso': Permission denied
tanner@tanner-desktop:~$ mount -o loop ds.iso /mnt/iso
mount: only root can do that
tanner@tanner-desktop:~$








][/QUOTE]

---

### Post by ianmacgregor on 2006-10-17
> **Magiczero said:**
> Hi

I want to put dsl on my flash drive and I read that I have to mount the iso and then copy the files to my flash drive i have used this comand and I get an error:

[QUOTEtanner@tanner-desktop:~$ mkdir /mnt/iso
mkdir: cannot create directory `/mnt/iso': Permission denied
tanner@tanner-desktop:~$ mount -o loop ds.iso /mnt/iso
mount: only root can do that
tanner@tanner-desktop:~$ mkdir /mnt/iso
mkdir: cannot create directory `/mnt/iso': Permission denied
tanner@tanner-desktop:~$ mount -o loop ds.iso /mnt/iso
mount: only root can do that
tanner@tanner-desktop:~$



You have to use sudo for that:

```

sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop ds.iso /mnt/iso

```You have to use sudo when manipulating almost all directories other than your $HOME.

---

