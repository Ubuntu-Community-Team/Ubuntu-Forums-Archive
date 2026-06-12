---
title: "Imaging software for linux?????"
date: 2007-10-16
forum: General Help
---

### Post by kdarkentity on 2007-10-16
I need imaging software for linux? i have found a variety of imaging software such as acronis but its all for windows.

any suggestions? 

thanks

---

### Post by r-mo on 2007-10-16
What do you want this for? backups? 'system restore'? cloning your setup to other pc's?

You could have a look at:
[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)
[http://www.desktoplinux.com/articles/AT2280165098.html](http://www.desktoplinux.com/articles/AT2280165098.html)

---

### Post by kdarkentity on 2007-10-16
the purpose is for cloning a system

---

### Post by r-mo on 2007-10-16
In that case go for the first link g4l, should do nicely.  Or you could just copy the filesystem across and reinstall grub :)

---

### Post by kdarkentity on 2007-10-16
Hmm... G4L?... i tried booting a working copy of G4U on my laptop and it failed to load all of the drivers that it needs. Do you have any knowledge of G4L? and If you do how is it different from G4U?

---

### Post by kdarkentity on 2007-10-16
How can i copy files directly off of my partition?... I need a copy of the entire drive including hidden files soo how could i copy both the write protected files and the hidden files?

thanks by the way

---

### Post by r-mo on 2007-10-16
root can read anything, you'd want to run off a live cd to make it easy, mount your 2 drives and then 
sudo cp -R /media/copyfrom /media/copyto

you'd need to make partitions on your new drive, and fstab would have a bit of a wobbly because drives are mounted by UUID in ubuntu.

dd is an interesting utility for this kind of thing as well although it's very slow and I've never been quite sure how to use it, you don't have to install grub if you use that tho ;)

Can't say I've used g4u but everytime I've used g4l it's worked great.  The whole reason I started using it instead of norton ghost was the version of ghost I had didn't support SATA drives g4l handled it fine though.

---

### Post by r-mo on 2007-10-16
Here's a useful dd command, it'll copy your master boot record to a file.  just swap 'if' and 'of' to copy it back

```
sudo dd if=/dev/sda of=/tmp/sda.mbr bs=512 count=1
```

---

### Post by kdarkentity on 2007-10-17
Ok thanks, soo i made a G4L cd and booted it, when the command prompt loaded up i used the command g4u $1, and i choose ftp/or local server (or whatever that option is) and im tring to clone my linux drive 3 off of my hard drive to my usb drive , Im attempting to do this as i am typing this post , and soo far the progress bar has just stayed at zero%, and its been sitting like this for close to 10 minutes , but i get no errors. I beleive everything is set-up correctly soo... what could possibly be wrong?

---

### Post by reza81 on 2007-10-17
Norton Ghost?

---

### Post by newman on 2007-10-17
Ghost doesn't handle EXT3 partitions reliably.

Try a native linux app such as PartImage.

---

### Post by kdarkentity on 2007-10-17
> **r-mo said:**
> root can read anything, you'd want to run off a live cd to make it easy, mount your 2 drives and then 
sudo cp -R /media/copyfrom /media/copyto

you'd need to make partitions on your new drive, and fstab would have a bit of a wobbly because drives are mounted by UUID in ubuntu.

dd is an interesting utility for this kind of thing as well although it's very slow and I've never been quite sure how to use it, you don't have to install grub if you use that tho ;)

Can't say I've used g4u but everytime I've used g4l it's worked great.  The whole reason I started using it instead of norton ghost was the version of ghost I had didn't support SATA drives g4l handled it fine though.

I used that command that you gave me to copy from disk to disk, however the files that i copied were thrown into a folder instead of the root, how can i copy all of the files from the root of a disk to a root of the destination disk?

---

### Post by kdarkentity on 2007-10-18
Is there a way i can make an image of a drive locally rather than uploading it to another machine?

---

### Post by copcrepair on 2007-12-21
> **r-mo said:**
> What do you want this for? backups? 'system restore'? cloning your setup to other pc's?

You could have a look at:
[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)
[http://www.desktoplinux.com/articles/AT2280165098.html](http://www.desktoplinux.com/articles/AT2280165098.html)
Is there a software that i can use on Ubuntu to make copies of other hard drives. I would like to copy customer hard drives from an old hdd to a new and sometimes larger hard drive. I currently use Acronis, or Ghost. Is there something that i can use and run on ubuntu to do the same thing?
I also make images of the factory software using ghost and acronis and then dump the images to new hdds using Acronis or Ghost. Any ideas?

---

### Post by kdarkentity on 2007-12-21
> **copcrepair said:**
> Is there a software that i can use on Ubuntu to make copies of other hard drives. I would like to copy customer hard drives from an old hdd to a new and sometimes larger hard drive. I currently use Acronis, or Ghost. Is there something that i can use and run on ubuntu to do the same thing?
I also make images of the factory software using ghost and acronis and then dump the images to new hdds using Acronis or Ghost. Any ideas?

I'm sorry i actually don't know of anything like that, but if its any help at all i recommend PING for imaging.

---

