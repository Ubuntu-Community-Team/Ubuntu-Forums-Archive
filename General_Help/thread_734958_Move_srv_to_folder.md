---
title: "Move /srv to folder ?"
date: 2008-03-25
forum: General Help
---

### Post by ixlam on 2008-03-25
Im looking to format my second HD (sdb)currently  with 2 partitions on it (/files,  & /srv) 
Can I move the /srv files on to ie. sda/some/fire/ and configure fstab or dependent services to use files from there?


thanks.

---

### Post by warp99 on 2008-03-25
Yes you can but I would copy the files just in case, then change the drive and the mount points in you fstab for the new location. Your system will look for the files at that new mount location.

---

### Post by ixlam on 2008-03-25
im not exactly clear on that..
Im simply loosing my SDB but need to preserve and use the files. 
curently /SRV is a partition... sdb2
If I move all the contents of the /SRV partition into a folder on sda3 (sda3/svr) 
wouldnt I NOT need to mount it as a partition but rather deletie the FSTAB entry?  
then change system preffs to read from sda3/srv somehow??

---

### Post by warp99 on 2008-03-25
Here is what you would do:

1) Rename the /srv directory /srv_files

```
sudo mv srv srv_files
```

2) Unmount the partition /srv

```
sudo umount /srv
```

3) Mount the new location with your new drive

```
sudo mount /dev/sdb3 /srv
```

4) Copy files from /srv_files to /srv

```
sudo cp -pr /srv_files/* /srv
```

If everything appears correct then make the changes to the fstab. Be sure to use the uuid instead of /dev/sdb* convention. To obtain the uuid type the following:

```
sudo vol_id -u /dev/sdb3
```

Reboot to make sure the new drive is mounted at /dev/sdb3, then delete the directory srv_files. :)

Edit:

You have to make the directory /srv before mounting it in step 3.

---

### Post by warp99 on 2008-03-25
Another way would be the following:

1) Unmount /srv

```
sudo umount /srv
```

2) Mount the new drive partition

```
sudo mount /dev/sdb3 /srv
```

3) Mount the /dev/sdb2 partition at a new mount point

```
sudo mkdir /srv_files

sudo mount /dev/sdb2 /srv_files
```

4) Copy the file from srv_files to srv

```
sudo cp -pr /srv_files/* /srv
```

If everything looks good then make the changes to the fstab and reboot. Your original /srv files will still be on /dev/sdb2 if you need them, but just not mounted. :)

---

### Post by ixlam on 2008-03-25
I already have 4 partitions on sda
sda1 /
sda2 /usr
sda3 /swap
sda4 /home

Can I mount a folder under /usr as a partition 

ie>   sudo mount /dev/sda2/usr/srv /srv

or can I  point to a folder as beeing the default srv location?

---

### Post by warp99 on 2008-03-25
> Can I mount a folder under /usr as a partition

ie> sudo mount /dev/sda2/usr/srv /srv

or can I point to a folder as beeing the default srv location?

No because /dev/sda2 is a device while /srv or /usr/srv is a file system. The directory /dev and the terminal points (/dev/sda , dev/dsp, dev/fd0, etc.) are a pseudo directory. It does not normally exist but only when the system is booted.

You don't need to mount the files inside of the /usr directory, All you have to do is move the files to /usr/srv and symlink the folder. You can move the files to **any** partition and symlink the folder if you wanted.

So to recap first you would move the files to /usr/srv:

```
sudo mv /srv /usr/srv
```

then unmount the /srv mount point:

```
sudo umount /srv
```

make the symlink to /usr/srv:

```
sudo ln -s /usr/srv /srv
```

remove the entries in you fstab for the mount point /srv and reboot. Now any requests made to /srv will be redirected to /usr/srv,  :)

---

