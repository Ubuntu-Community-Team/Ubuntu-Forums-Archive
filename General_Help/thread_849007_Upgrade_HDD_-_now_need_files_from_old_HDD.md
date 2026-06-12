---
title: "Upgrade HDD - now need files from old HDD"
date: 2008-07-04
forum: General Help
---

### Post by jaggyone on 2008-07-04
I've upgraded my HDD to Ubuntu 8.04.  Now that I've got the new system up and running, I would like to take files off of my old HDD - Fedora 7.

I am mounting the old HDD as an external usb drive but can only see the first partition sdb1.  I am looking to mount the second partition sdb2 -LVM  but have not had any luck.  Can anyone help.

Thanks in advance,
jaggyone

---

### Post by iaculallad on 2008-07-04
We could not directly mount LVM volumes in Ubuntu.

Drop to your terminal and install lvm2:

```
sudo apt-get install lvm2
```

Load the modules:

```
sudo modprobe dm-mod
```

Scan Ubuntu for LVM volumes:

```
sudo vgscan
```

Output would either be **VolGroup00**, **VolGroup01**, **VolGroup02**. It depends on how many LVM volumes Ubuntu can detect.

Locate the logical volume that has LVM root filesystem:

```
sudo lvs
```

Output would either be **LogVol00**, **LogVol01**, **LogVol02**...

Create the mountpoint on your Ubuntu system:

```
sudo mkdir /mnt/fromfedora
```

Then, try mounting the volume:

```
sudo mount /dev/VolGroup00/LogVol00 /mnt/fromfedora -o ro,user
```

---

### Post by jaggyone on 2008-07-04
Could not mount the partition.  Here are the steps I followed:


root@pitch:~# modprobe dm-mod
root@pitch:~# sudo modprobe dm-mod
root@pitch:~# vgscan
  Reading all physical volumes.  This may take a while...
Found volume group "VolGroup00" using metadata type lvm2
root@pitch:~# lvs
  LV       VG         Attr   LSize  Origin Snap%  Move Log Copy%
LogVol00 VolGroup00 -wi--- 41.81G
LogVol01 VolGroup00 -wi---  1.00G
root@pitch:~# mkdir /mnt/fromfedora
root@pitch:~# mount /dev/VolGroup00/LogVol00 /mnt/fromfedora -o ro,user
mount: special device /dev/VolGroup00/LogVol00 does not exist

Is there anything else I can try?

-jaggyone

---

### Post by jaggyone on 2008-07-12
Found the solution on another forum post: [http://baudizm.blogsome.com/2008/06/05/retrieving-lvm-volume-data-with-ubuntu-and-backup-to-nfs-server/](http://baudizm.blogsome.com/2008/06/05/retrieving-lvm-volume-data-with-ubuntu-and-backup-to-nfs-server/)

After install LVM2, running the commands below allowed me to access the LVM prtition on my external USB drive.

root@linux:~# mkdir /mnt/myLVM
root@linux:~# vgscan
root@linux:~# modprobe dm-mod
root@linux:~# vgchange -ay VolGroup00
root@linux:~# lvs
root@linux:~# mount /dev/VolGroup00/LogVol00 /mnt/myLVM

whew - glad that if finally worked.

jaggyone:

---

