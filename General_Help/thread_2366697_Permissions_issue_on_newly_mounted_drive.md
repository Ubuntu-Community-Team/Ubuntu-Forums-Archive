---
title: "Permissions issue on newly mounted drive"
date: 2017-07-20
forum: General Help
---

### Post by Steve_Corman on 2017-07-20
I have a new /dev/sdb drive I added to my 16.04 box.  I tried to get this mounted using an edit to fstab, but made an error (I guess) in the record and it wouldn't boot so I revered to the original fstab to get going again.  Following advice I found through research I installed gnome-disks and used that to mount the partition.  It worked but only root could to anything with the mounted drive.  

So as root I changed the permissions on the mount point to rw-rw-rw, and changed both the ownership and group to myself.  Still I could not write to it as me, nor even cd to it.  Also the gui file manager (thunar) shows an X in the folder icon, so something is obviously not right.  

Another strange thing is that there's no record in fstab for this drive at all, even though it's mounted and shows a record via mount:
```

/dev/sdb1 on /video type xfs (rw,nosuid,nodev,relatime,attr2,inode64,noquota)
```
Maybe those aren't the right options.  They're the ones created by gnome-disks.

I'm a little flummoxed here.  Can anyone tell me how to straighten this out?

---

### Post by vocx on 2017-07-20
> **Steve_Corman said:**
> I have a new /dev/sdb drive I added to my 16.04 box.  I tried to get this mounted using an edit to fstab, but made an error (I guess) in the record and it wouldn't boot so I revered to the original fstab to get going again.  Following advice I found through research I installed gnome-disks and used that to mount the partition.  It worked but only root could to anything with the mounted drive.  

So as root I changed the permissions on the mount point to rw-rw-rw, and changed both the ownership and group to myself.  Still I could not write to it as me, nor even cd to it.  Also the gui file manager (thunar) shows an X in the folder icon, so something is obviously not right.  

Another strange thing is that there's no record in fstab for this drive at all, even though it's mounted and shows a record via mount:
```

/dev/sdb1 on /video type xfs (rw,nosuid,nodev,relatime,attr2,inode64,noquota)
```
Maybe those aren't the right options.  They're the ones created by gnome-disks.

I'm a little flummoxed here.  Can anyone tell me how to straighten this out?
I haven't used an XFS filesystem, but I think it should be simple as adding the right entries in the "/etc/fstab". I haven't used gnome-disks, so I have no idea what it does, but it should not be more complicated than adding the right options to fstab.

First of all, before changing permissions or editing fstab, unmount the drive and make sure the drive stays unmounted. In your description it is not clear if you were changing the options and testing things before or after using gnome-disks and mounting the device.

Create the mount points, change ownership with "chown", and permissions with "chmod".
```

sudo mkdir -p /video
sudo chown steve:steve /video
sudo chmod u+rwx /video

```
The owner becomes "steve", the group becomes "steve". The user "u", actually the owner of the directory which is "steve", gets "+", read, write, and execute permissions, "rwx".
The execute permissions for directories are needed because it means the user can enter and browse the directory. A directory without execute permissions means it is there, but you cannot enter it from the file manager.
Use the appropriate username instead of "steve", of course.

Then in "/etc/fstab"
```

# notice there is no space after the commas
/dev/sdb1     /video       xfs    auto,umask=0022,gid=1000,uid=1000    0   2

```
where the "gid" and "uid" are the id numbers of your user. You can check this by
```

id

```

Then you can mount
```

sudo mount /video

```
If everything went okay, it should be mounted, and you can verify with the command "mount".

If it didn't work, then unmount the drive, change some options, and try again.
```

sudo umount /video

```

You can test different options using the "mount" command, before actually writing the options to "/etc/fstab".
```

# no space after the commas. The entire string is an argument passed to the "-o" option
sudo mount -t xfs /dev/sdb1 /video -o auto,umask=0022,gid=1000,uid=1000

```

---

### Post by Dennis N on 2017-07-20
> Also the gui file manager (thunar) shows an X in the folder icon, so something is obviously not right.

You need execute permission on a folder in order to open it. 

I mount my data partition on my second HD with this. I haven't used XFS, so can't comment on your entry.

```
UUID=d97e2feb-1bf6-429b-bba5-943264ec1474 /mnt/Common-Files ext4 defaults 0 2
```

---

### Post by Steve_Corman on 2017-07-21
Thanks for the help.  I got it to work with the right fstab entry and the permissions, as you guys suggested.

---

