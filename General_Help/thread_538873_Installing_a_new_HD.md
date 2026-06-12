---
title: "Installing a new HD"
date: 2007-08-30
forum: General Help
---

### Post by shrumhead on 2007-08-30
I  have Ubuntu booting on a 40gb HD and used to have Windows on a 120gb HD but I did away with windows and now I would like to use that 120gb HD in for linux.  I'm curious what I should do in terms of partitioning and how it will appear in the filesystem?

---

### Post by prince_niceguy on 2007-08-30
Not sure if I understand the question.

You just put in the drive as secondary ... check the jumper setting on the disk.

Once it is put in as secondary and connected properly just boot up and it should be detected. Now use gparted and parition the disk to your need.

If you want to make this as primary and boot from this disk then refer to 

[http://www.xlntsolution.com/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/](http://www.xlntsolution.com/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/)

keep the boot around 300MB if you are going to have different kernels on your computer.

---

### Post by southernman on 2007-08-30
Do not reposition your drives as to what is primary or secondary or you'll have to edit several other files to make it work right.

Howto coming up... brb

---

### Post by southernman on 2007-08-30
I will assume for this brief tutorial that you will want to use this drive as a storage space to hold music, movies, or something of your choosing.

This will involve the command line (aka terminal) which you get by going to Applications > Accessories > Terminal. Don't worry, I'll walk you through it bit by bit. ;)

Open the terminal and run these commands:

> sudo fdisk /dev/hda
Assuming Windows was installed in /dev/hda which simply means the primary hdd on your system.
The above command will dump you into a fdisk prompt, while here simply press "m" for a list of commands you can use.

If, and ONLY if you are sure you want to wipe out your entire hard disk (the one with windows on it) proceed as follows...

press d and it will ask you which partition to delete.. a general practce of mine is to start with 4 and work my way down. If you only have one partition it will assume that partition is the one your want to blast and do it for you. Rinse and repeat as needed.

Now it's time to make a new partition(s) I will assume you only want one partition on this drive. 

n (for new partition)
p (make it primary and not extended)
1 (number the partiton)
enter (accept the default starting point of the partition)
enter (accept to use the default setting of using all the space on the drive)
w (will write the new partition table data)
q (quit the fdisk program)

Now that you have your newly setup partiton on the 120giger, we need to make it's filesystem. I will assume you want to use ext3 below:

> sudo mke2fs -j /dev/hda1
Once this is complete you need to setup a mount point for the drive by doing, I call it storage, but you can call it anything you like as long as it's not already used in the /media folder:
> sudo mkdir /media/storage
sudo mount /media/storage /dev/hda1

To have the drive mount at each boot automatically, you need to now edit the file /etc/fstab

> gksudo gedit /etc/fstab

add this line (change it to suit the name of the directory you created above)
> /dev/hda1    /media/storage   ext3    defaults     0        2

Now you need to set permissions on the drive so that you can have total control over it... done by doing this, again change the relevant info to your username in place of shrumhead and name of the directory we made above:
> sudo chown -R shrumhead:shrumhead /media/storage

That should do it. Please pay the attendant on the way out... ;)

---

### Post by shrumhead on 2007-08-30
Thank you very much Southernman, that is exactly what I was looking for :)

---

### Post by southernman on 2007-08-30
Your quite welcome shrumhead. If you have any trouble, please post the errors you get and we'll sort it out for you.

If you don't get errors or have problems, please mark your post as solved.

---

### Post by shrumhead on 2007-08-30
I have a slight problem with 

> sudo mount /media/storage /dev/hda1

It says "mount: /media/storage is not a block device".

---

### Post by merlinus on 2007-08-30
Try:

```

sudo mount /dev/hda1 /media/storage

```

If that does not work, try this:

```

sudo mount -t ext 3 /dev/hda1 /media/storage

```

-merlin

---

### Post by shrumhead on 2007-08-30
lol dummy me.  Worked just fine.  Done and Done, ty for the help all.

---

