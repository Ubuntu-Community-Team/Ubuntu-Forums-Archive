---
title: "External disk full (not)... can't find out"
date: 2012-11-12
forum: General Help
---

### Post by cromefx on 2012-11-12
Gents,

I am having an issue with my backup disk, an external 500GiB (465.11 GiB according to GParted) formatted as ext4.

It has only a few backup files, but last night in order to save some space I deleted an img file and from the redundant backup disk (also external and ntfs formatted) sent the same image but now compressed:

> root@N55SL-xubuntu-12-4:/media/500USB2# pv /media/tera/Backup/W7-Xub12-Nov2012.img | pigz > /media/500USB2/W7-Xub12-Nov2012.img.gz
write error code 289MB/s] [=======================>            ] 69% ETA 0:21:29
pigz abort: write error on <stdout>
 154GB 0:47:58 [54.9MB/s] [=======================>            ] 69% I had more than enough space on the 500GiB disk and something went wrong, the disk is now full with something I can't find:

- GParted says the disk is full
- Thunar says the disk is full
- I run the disk usage tool on Krusader and it tells me:
  -- total size (used) 250GiB 
but Krusader properties for the 500USB2 disk is:
  -- 0 B free of 457.8 GiB (100% used)
- I run

> root@N55SL-xubuntu-12-4:/media/500USB2# ls -h -R -l
.:
total 24K
drwxr-xr-x 2 root root 4.0K Nov 11 19:13 1225B
drwx------ 2 root root  16K Nov  8 13:43 lost+found
drwxr-xr-x 3 root root 4.0K Nov 11 23:43 N55S

./1225B:
total 42G
-rw-r--r-- 1 root root 27G Nov  8 16:03 1225B-500GiB-disk-factory-original.img.gz
-rw------- 1 root root 15G Nov  3 15:41 W7-1225B-usb-factory.img

./lost+found:
total 0

./N55S:
total 175G
drwxr-xr-x 2 root    root    4.0K Nov 11 18:53 Factory reset DVDs Win7 ASUS N55S
-rw------- 1 tsunami tsunami 103G Nov  9 02:14 N55S-750GiB-disk-factory-original.img.gz
-rw-r--r-- 1 root    root     73G Nov 12 00:32 N55S-W7-Xub12-Nov2012.img.gz

./N55S/Factory reset DVDs Win7 ASUS N55S:
total 19G
-rw------- 1 tsunami tsunami 3.8G Sep 12 22:58 CD1.iso
-rw------- 1 tsunami tsunami 3.7G Sep 12 23:01 CD2.iso
-rw------- 1 tsunami tsunami 3.7G Sep 12 23:04 CD3.iso
-rw------- 1 tsunami tsunami 3.7G Sep 12 23:07 CD4.iso
-rw------- 1 tsunami tsunami 3.7G Sep 12 23:09 CD5.iso
-rw------- 1 tsunami tsunami 127M Sep 12 23:09 CD6.iso- Then I run:
> root@N55SL-xubuntu-12-4:/media/500USB2# df /media/500USB2/ --total -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdc1       458G  458G     0 100% /media/500USB2
total           458G  458G     0 100%- Then I run:
> root@N55SL-xubuntu-12-4:/media/500USB2# du -s -h * |sort -n
4.0K    size.txt
16K    lost+found
42G    1225B
193G    N55SWhat am I missing here? This is my first post on a linux forum. I have always sorted out things through search, Google and coffee, but I can't get it straight and I don't want to format the disk just because I can't sort it out, so it's time to get out of the closet and join the community.

Thanks for your time and help,
Cromefx

---

### Post by philinux on 2012-11-12
This might help.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by cromefx on 2012-11-12
> **philinux said:**
> This might help.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

Thank you philinux, it did help:

I did:
```
root@N55SL-xubuntu-12-4:/media/500USB2# du -h --max-depth=1
225G    ./.Trash-0
16K    ./lost+found
42G    ./1225B
193G    ./N55S
458G    .
```this was the only command that revealed the Trash folder...

is there a reason why it didn't show up earlier? And was not in the system trash as the trash bin on the Desktop or on Thunar?

Thank you,
cromefx

---

### Post by philinux on 2012-11-12
As you can see that's root's trash folder as opposed to a user's trash. If you been deleting files as root or gksu nautilus thats where they go.

---

### Post by cromefx on 2012-11-12
Humm... Didn't know that root also had a trash, and yes it was deleted with Thunar as root.

But does it also explains this?:

```
root@N55SL-xubuntu-12-4:/media/500USB2# du -s -h * |sort -n
4.0K    size.txt
16K    lost+found
42G    1225B
193G    N55S
root@N55SL-xubuntu-12-4:/media/500USB2# du -h --max-depth=1
225G    ./.Trash-0
16K    ./lost+found
42G    ./1225B
193G    ./N55S
458G    .

```from the du man I can't see why these outputs are different (as in one showing trash and not the other).

---

