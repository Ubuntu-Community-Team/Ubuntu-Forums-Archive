---
title: "File permissions on removable drives"
date: 2012-12-31
forum: General Help
---

### Post by grayfox444 on 2012-12-31
Recently I've been unable to cut/rename, etc files from removable drives on Ubuntu. I was able to in the past so I'm not sure what triggered it.

Basically if I put in an SD card of photos, I can't cut the photos, or delete them. But I can copy/paste them.

Similarly I can't rename files or create folders on the drives.

Any help would be great, thanks.

---

### Post by sudodus on 2012-12-31
I agree with the title of your thread: File permissions!

It depends on how Windows's file systems are mounted in linux. The permissions (file attributes) of FAT and NTFS are set when the partition is mounted and cannot be changed for individual files. So you need to make sure the partitions are mounted with correct permissions (you want write permissions).

An alternative is to change to a linux file system, where you would get the same flexibility as with the internal linux partition(s).

Recently I have read some threads here in the Ubuntu Forums about new problems, where these things used to work. Maybe there is a bug in Ubuntu 12.10, but I'm not sure that it affects you.

---

### Post by grayfox444 on 2012-12-31
Interesting, so how would I go about resolving it?

---

### Post by Kirk Schnable on 2012-12-31
> **grayfox444 said:**
> Interesting, so how would I go about resolving it?
The root user on your machine should have full access to your removable media files, regardless of their permissions.

This means, if you use sudo or gksudo in some way, you will be able to manipulate your files.

The most sensible approach would probably be to use sudo to give your own user access to the files.  If your username on the computer is *grayfox444* and your removable media is in */media/thumbdrive*, you would want to do something like...

```
sudo chown -R grayfox444 /media/thumbdrive
```

After doing so, your user should have full access to the files.

---

### Post by fdrake on 2012-12-31
I would check also the fstab and the mtab.
```

less /etc/fstab
mount 

```

---

### Post by grayfox444 on 2012-12-31
> **Kirk Schnable said:**
> The root user on your machine should have full access to your removable media files, regardless of their permissions.

This means, if you use sudo or gksudo in some way, you will be able to manipulate your files.

The most sensible approach would probably be to use sudo to give your own user access to the files.  If your username on the computer is *grayfox444* and your removable media is in */media/thumbdrive*, you would want to do something like...

```
sudo chown -R grayfox444 /media/thumbdrive
```

After doing so, your user should have full access to the files.
I am the root user so I'm not sure why the permissions aren't working. 

I tried running sudo chown -R user/media/SDCardName but it said:
missing operand after (statement)

---

### Post by raja.genupula on 2012-12-31
place the -R after all .

I mean 
sudo chown grayfox444 /media/thumbdrive -R

source:[http://askubuntu.com/questions/234414/jhbuild-sanitycheck-not-moving](http://askubuntu.com/questions/234414/jhbuild-sanitycheck-not-moving)

---

### Post by grayfox444 on 2012-12-31
I get the same error with that syntax.

Is there a way to set up the global permissions for the account? my account is set as admin.

---

### Post by fdrake on 2012-12-31
> **grayfox444 said:**
> I am the root user so I'm not sure why the permissions aren't working. 

I tried running sudo chown -R user/media/SDCardName but it said:
missing operand after (statement)
First you have to put the name of the user then the "-R"

---

### Post by Buntu Bunny on 2012-12-31
I had this problem with a USB stick. Tried to resolve it with an older thread, so I didn't get this particular help. In the end, the only thing for it was to reformat with Gparted.

---

### Post by grayfox444 on 2012-12-31
> **fdrake said:**
> First you have to put the name of the user then the "-R"

The command ran, but the drive is still read only

---

### Post by sudodus on 2013-01-01
> **grayfox444 said:**
> The command ran, but the drive is still read only
I guess that you have a Windows file system on the removable drive, FAT32, exFAT or NTFS. Such file systems have their permissions set when mounted, so to change them, you need to change the mounting.

But first we can check if it is a bug of the version 12.10. What version of Ubuntu are you running? Check with ```
lsb_release -a
```
If you have 12.10, download and try 12.04 LTS. Don't install it, try it live (booted from the CD/DVD/USB drive) and check if you get proper access to your removable drive. If it works you can either wait for the bug to get fixed or save your personal data and install 12.04 LTS instead.

---

### Post by fdrake on 2013-01-01
> **grayfox444 said:**
> The command ran, but the drive is still read only

mount the driver and run the command ```

gksudo nautilus /media

```
edit/rename the files locate in the drive. I succesfull look at my command in post #  . If it fails you may have to reformat the disk; post the outpust of
```

sudo fdisk -l

```
if u use windows partitions, reformat it (try to use FAT32(slow-format)

---

