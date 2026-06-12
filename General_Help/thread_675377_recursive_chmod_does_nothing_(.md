---
title: "recursive chmod does nothing :("
date: 2008-01-22
forum: General Help
---

### Post by ELD on 2008-01-22
Hi all i try and do this:

"sudo chmod -R 777 /media/sda1/Website"

And it seems to do just do nothing, so when i upload, my website won't load saying permission denied, argh!!

---

### Post by bodhi.zazen on 2008-01-22
You need to move or link your website to 

/var/www

also you almost certainly do not want to chmod -R 777 on that stuff.

If permissions on the usb did not change, most likely you are using either FAT or NTFS, and that is not how to set permissions on a FAT or NTFS partition.

---

### Post by ELD on 2008-01-22
Why would i want to move it there? I am not hosting it on the same machine, i simply want to chmod my website folder and all files in it to 777.
I try it in terminal and it just seems to do nothing :(

---

### Post by bodhi.zazen on 2008-01-22
I updated my first post, I guess I am not understanding what you are trying to do exactly.

What file system is it ? My guess is FAT or NTFS

I assumed :> when i upload, my website won't load saying permission deniedmeans you are having problems connecting to your site.

---

### Post by ELD on 2008-01-22
It is on an NTFS file system, is that why it is not working?

---

### Post by bodhi.zazen on 2008-01-22
yes, that is the problem. NTFS does not support permissions, so you need to set permissions at the time of mounting.

You can use ntfs-config : [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

Or you can use ntfs-3g

sudo mount -t ntfs-3g /dev/xxx /mount/point -o uid=1000,gid=100,umask=007

Or in fstab

/dev/xxx /mount/point ntfs-3g users,uid=1000,gid=100,umask=007 0 0

---

### Post by ELD on 2008-01-22
so one of those lines you gave me will make the permissions right?

---

### Post by bodhi.zazen on 2008-01-22
Yea, but if you do not understand those commands or know how to edit /etc/fstab, go for the link

nfts-config is a gui tool :)

Otherwise, see this link : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by ELD on 2008-01-22
Well it already brings up my drives fine and this is my fstab atm?

# /dev/sda1
UUID=ECFCE211FCE1D5BC /media/sda1     ntfs    defaults,umask=007,gid=46 0       1

---

### Post by bodhi.zazen on 2008-01-22
If you like, 

```
gksu gedit /etc/fstab
```

Change:

> # /dev/sda1
UUID=ECFCE211FCE1D5BC /media/sda1 ntfs defaults,umask=007,gid=46 0 1

To:

```
# /dev/sda1
UUID=ECFCE211FCE1D5BC /media/sda1 ntfs-3g defaults,umask=007,gid=100,uid=1000 0 0
```

Save and exit gedit

Then:

```
sudo apt-get install ntfs-3g

sudo umount /media/sda1
sudo mount /media/sda1
```

---

