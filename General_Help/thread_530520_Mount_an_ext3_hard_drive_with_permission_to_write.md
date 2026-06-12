---
title: "Mount an ext3 hard drive with permission to write"
date: 2007-08-20
forum: General Help
---

### Post by Dave54 on 2007-08-20
I know many questions close to this have been asked. I've read many of them.

I'm running feisty and I have a hard drive formatted as a single ext3 partition with information on it. I would like to have the ability to easily mount and read/write to it, but _not_ have it mount automatically when I log on.

First, I created a mount point:```
sudo mkdir /media/slave
```
Next, I gave myself to read/write to it:```
sudo chown -R dave:dave /media/slave
```
So far so good. Finally, I want ubuntu to mount to that mount point. So I go to "Places > Computer", right-click on the volume and click "Properties", go to the "Volume" tab, and under "Mount Point:" I enter "slave"

Done! Now to mount it, I double-click the volume (in "Computer"), and it automatically mounts it, but it mounts to "/media/slave_" instead of "/media/slave".

It seems that I did everything right, but ubuntu wants to avoid mounting to my folder. What's up?

---

### Post by Ek0nomik on 2007-08-20
I have never mounted a device graphically to be honest...

Try this:

Accessories/Terminal:

```
fdisk -l
```

Look for your device.  It should say that it's formatted as EXT3 and it should also display the size of the device.  It will post something like /dev/hda1.

```
sudo mount /dev/hd**xy** /media/slave
```

If you get confused with the fdisk -l output, just paste it in a reply and I will help you.

---

### Post by randcoop on 2007-08-20
As an alternative, you might just try using pmount instead of mount.

I use the command:```
pmount /dev/sd* /media/[name of mount point]
```

where you would obviously replace the * with your actual device (mine is sda2, for example).  

Note that you don't need to use sudo; pmount allows you to mount as an ordinary user.

---

### Post by bodhi.zazen on 2007-08-20
To mount you need to use the mount command.

If you have no entry for the partition in /etc/fstab you will need to use sudo (which is likely why you can not do it yet with your gui).

So make an entry in fstab

Ownership will change when you mount the partition so you will need to set permissions again once the partition is mounted (if they need to be adjusted).

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by Dave54 on 2007-08-20
> **Ek0nomik said:**
> Try this:

Accessories/Terminal:
```
fdisk -l
```
I think that command needs sudo to work. My device is /dev/hdb1
> **Ek0nomik said:**
> ```
sudo mount /dev/hd**xy** /media/slave
```
This worked, but there are some folders I can't access due to permissions. I could not unmount the hard drive by right-clicking the icon on the desktop, I got the following error:> Cannot unmount volume: The volume was probably mounted manually on the command line.
I unmounted it with the following command:
```
sudo umount /media/slave
```
Which seemed to work well enough.

> **randcoop said:**
> As an alternative, you might just try using pmount instead of mount.

I use the command:```
pmount /dev/sd* /media/[name of mount point]
```
After installing pmount, I tried it, but it didn't work:
```
dave@dave-comp:~$ pmount /dev/hdb1 /media/slave
Error: device /dev/hdb1 is not removable
```

> **bodhi.zazen said:**
> To mount you need to use the mount command.

If you have no entry for the partition in /etc/fstab you will need to use sudo (which is likely why you can not do it yet with your gui).

So make an entry in fstab

Ownership will change when you mount the partition so you will need to set permissions again once the partition is mounted (if they need to be adjusted).

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

Between your post and link, it worked out very well with full ability to read/write in all folders. The only complaint is that it mounts at boot (something I didn't want).

Here's what I did, start to finish:

```
sudo mkdir /media/slave
sudo chown -R dave:dave /media/slave
sudo fdisk -l
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```
In the window that pops up, I added: "/dev/hdb1	/media/slave	ext3	defaults	0	0". Save, close.
```
sudo mount -a
sudo chown -R dave:dave /media/slave/
sudo chmod -R 755 /media/slave/
```

Now that I think about it, I guess mounting at boot is not so bad, but does anyone know how to get rid of the icon on the desktop for the disk? (I do _not_ want to have that there 24/7)

Thanks for all the help guys!

---

### Post by Irony on 2007-08-20
Something like this (I've tried gui - but couldn't figure it out);

[PHP]sudo fdisk -l

sudo mkfs.ext3 /dev/hdb1

sudo mkdir /media/slave

sudo mount /dev/hdb1 /media/slave

sudo chown username -R /media/slave

sudo chmod -R 700 /media/slave

sudo umount /media/slave[/PHP]

Note that permissions is done after mounting.

---

### Post by bodhi.zazen on 2007-08-20
To get rid of the icon, either mount it in /mnt rather then /media

Or : [http://ubuntuforums.org/showpost.php?&p=2513012&postcount=3](http://ubuntuforums.org/showpost.php?&p=2513012&postcount=3)


=====


To have the disk NOT mount at boot, change "defaults" in fstab to 

"noauto,users"

you can then mount as a user. Check out the fstab link I gave you ;)

Also, after entering the partition in fstab I presume the gui will work to mount the drive

---

### Post by Dave54 on 2007-08-20
Wow. Thanks again bodhi.zazen.

Given my options, I think I'll mount it in /mnt. It won't appear in "Places", but it'll still be in "Computer".

I didn't like the option of making mounted volumes not appear on the desktop because it also affects flash drives, etc.

Oh, and thanks for clearing up how to make it not automatic. I've forgotten now why I wanted it not to mount on startup, but if I remember, now I have a fall-back plan :)

---

### Post by Dave54 on 2007-08-20
Uh-oh.

I made /mnt/slave, changed the fstab, and then I ran "sudo mount -a". The mount worked, but the icon appeared on my desktop! (this time it was named "/mnt/slave" instead of "slave".) I tried mounting it in /home/dave/slave, but the icon appeared once again.

It would seem the icon appears no matter where you mount it. I'm working with a clean install of feisty here.

Anyone know anything about this?

---

### Post by bodhi.zazen on 2007-08-20
Seems this is a recent change with feisty ...

---

### Post by Dave54 on 2007-08-21
Oh well.

I decided to disable mounted icons, works well enough. If anyone comes up with a work-around, feel free to share.

By the way, bodhi.zazen, you were right: once the "users" modifier was in the fstab, the gui had no problem using a custom folder as the mount point.

---

