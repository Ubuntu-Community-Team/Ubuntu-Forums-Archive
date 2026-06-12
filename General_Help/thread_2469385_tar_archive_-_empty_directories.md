---
title: "tar archive - empty directories"
date: 2021-11-27
forum: General Help
---

### Post by gebseng on 2021-11-27
Hey there,

I have a home server running Ubuntu Server 20.04. I tried to do a system backup from / using:

```
sudo tar -cvpzf /[target directory]/[target file].tar.gz --exclude=/home --exclude=/media --exclude=/tmp --exclude=/swapfile --one-file-system /
```

This worked fine. But when unpacking the .tar.gz, I saw that some directories that had content originally were empty in the backup:

dev
proc
run
sys

What am I missing?

thanks, 

geb

---

### Post by ActionParsnip on 2021-11-27
Those are system directories that help the system access the hardware and the processes that are running. They should also be excluded

---

### Post by Impavidus on 2021-11-27
/dev, /proc, /run and /sys are real directories in your root directory, used as mountpoints for pseudofilesystems. As you used the --one-file-system option, their contents were not included in the archive. And rightly so, as creating backups of those would be pointless.

---

### Post by gebseng on 2021-11-27
> **Impavidus said:**
> /dev, /proc, /run and /sys are real directories in your root directory, used as mountpoints for pseudofilesystems. As you used the --one-file-system option, their contents were not included in the archive. And rightly so, as creating backups of those would be pointless.

I see thanks! So, the content of these directories is not necessary for system restore in case of a drive failure?

---

### Post by ActionParsnip on 2021-11-27
No. They are generated every boot up.

---

### Post by gebseng on 2021-11-27
Perfect, thanks again!

---

### Post by HermanAB on 2021-11-28
W0t? You don’t keep a backup of /dev/random? ;)

---

