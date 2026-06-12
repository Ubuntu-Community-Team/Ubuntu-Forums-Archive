---
title: "Permissions for /var/"
date: 2008-06-20
forum: General Help
---

### Post by marshal on 2008-06-20
hi,

i set up a new hdd today to move some stuff there. my main goal was to mount /var/ onto a partition on the new drive, which actually worked fine. to keep the folders i copied the old /var/ using 

```
sudo cp -r /var/ /temp/
```

and after mounting everything back

```
sudo cp -r /temp/var/* /var/
```

but this procedure messed something with the permissions, because several services (lighttpd, mysql, ...) won't work anymore, because they can't access logs or other files always with permissions errors.

is there a way to move files while keeping the permissions, or how can i rebuild the old permissions, hopefully without doing chmod on every single file =)

fstab looks like this:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9219b517-a9ad-4c3a-89ce-94dc4a805cdd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=cbeaecba-a418-4e94-118c-ef8c7014530d none            swap    sw              0       0
/dev/sdb1       /var    ext3    defaults        0       0




hopefully i put every necessary information. (xubuntu 8.04)

thx for help

---

### Post by dracayr on 2008-06-20
yep, copying with cp changes permissions. you could tar var to keep permissions. But the cp to /temp already changed the permissions, so copying from there won't help, you have to copy the files from the original /var (if they still exists).

dracayr

---

### Post by chrisccoulson on 2008-06-20
Yeah, your best bet is to do the copy again if you still have the original copy. If not, then I'd probably go for a re-install. The permissions and ownership are quite complicated under /var and can't be fixed with a simple recursive chown or chmod.

Use [this]("http://ubuntuforums.org/showthread.php?t=35087") method of backing up and restoring a system to copy your contents of /var (it uses tar, as already suggested by dracayr)

Was /var on a separate partition before, or was it just on the root partition? If this is your first time moving /var on to it's own partition, you may have another unforeseen problem (/var/run and /var/lock not mounting at boot), which I can help you with

---

### Post by marshal on 2008-06-20
if i unmount the new partition i can access the original /var/ folder, so i still got an original copy.

the first install was "one partition + swap"
what kind of problems are there regarding the /var/run, /var/lock issue. is there a easy fix? otherwise i'll maybe do a reinstall

---

### Post by chrisccoulson on 2008-06-20
Was the original /var just on the root filesystem, or a dedicated partition? If it was on it's own filesystem, you could just mount the old partition under a temporary folder in /mnt, and then tar the contents of it. If it was on the root filesystem (which I think it probably is from your post above), you could perhaps bind mount the root filesystem to get access to the old /var folder (although I can't check it yet to give you a guarantee that it will give you access to the old folder as opposed to the new mounted /var filesystem). Try:
```
sudo mkdir /mnt/root
sudo mount --bind / /mnt/root
```
...then check to make sure that /mnt/root/var contains the correct (old) contents and tar them.

The issues with /var/run and /var/lock not mounting when /var is on a dedicated partition may not happen on later versions. But if it does, it is an easy fix and might happen regardless of whether it was a fresh install or not.

---

### Post by dracayr on 2008-06-20
here's an easy command to copy the contents of /var to /foo/bar/ using tar:

```
cd /var
tar cf - . | ( cd /foo/bar/ ; tar xfp - ) 
```

dracayr

---

### Post by marshal on 2008-07-03
hi, sorry for not answering.

i actually did a new installation, because i messed several other things ](*,)

but first i tried the tar... way. it works

---

