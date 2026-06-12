---
title: "[SOLVED] Mounting a 2nd physical HDD"
date: 2008-02-18
forum: General Help
---

### Post by meazz1 on 2008-02-18
I have successfully mounted a 2nd 160 gig IDE drive and created a mount point.
Before I created the mount point in fstab, I could see the drive in "Computer" in the Places menu.
Once I added this link in fstab, I no longer see it in Computer.
Is there way to do it, so the physical drive shows up in Computer menu there?
I still want to keep the Desktop folder.

I added this to my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dd87a640-cae4-4139-9df9-a0949e71f7b0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d29d7ca0-c19a-4cb7-8512-bb985b3dc422 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hdb1 	/home/mehdi/Desktop/2nd ext3 defaults 0 0
```

---

### Post by bodhi.zazen on 2008-02-18
For it to show in "Computer" you need to mount it in /media (rather then home).

You can use a link (after mounting) if you like :

```
ln -s /media/2nd /home/mehdi/Desktop/2nd
```

---

### Post by meazz1 on 2008-02-18
> **bodhi.zazen said:**
> For it to show in "Computer" you need to mount it in /media (rather then home).

You can use a link (after mounting) if you like :

```
ln -s /media/2nd /home/mehdi/Desktop/2nd
```

Can you explain a little more on the steps?

thanks

---

### Post by bodhi.zazen on 2008-02-18
> **meazz1 said:**
> Can you explain a little more on the steps?

thanks

Sorry, since you stated you edited fstab I figured you knew what you were doing.

1. Unmount the hard drive.

```
sudo umount /home/mehdi/Desktop/2nd
```


2. Delete the old mount point (take care, if the drive is not unmounted you will delete your data).

```
rm -rf /home/mehdi/Desktop/2nd
```


3. Make a new mount point in /media (I will use 2nd, you can use what name you will)

```
sudo mkdir /media/2nd
```


4. Edit fstab

```
gksu gedit /etc/fstab
```

Change the line for your HD to :

> /dev/hdb1  /media/2nd  ext3  defaults  0  2

The 2 = check file system at boot, good idea, you can leave it at 0 if you like ....


5. Mount the HD

```
sudo mount /media/2nd
```

It should now appear in "Computer"


6. Set permissions (if needed)

```
sudo chown -R mehdi.mehdi /media/2nd
chmod 770 /media/2nd
```


7. Make a link (or short cut)

```
ln -s /media/2nd /home/mehdi/Desktop/2nd
```

A link will put a folder in your home directory, in this example called 2nd. This is a direct link, or shortcut, to your HD and will behave the same as your old mount point. 

Your HD will now appear in both "Computer" as 2nd and in your home directory as 2nd.


If there is a step you do not understand, please ask ;)

---

### Post by meazz1 on 2008-02-19
> **bodhi.zazen said:**
> Sorry, since you stated you edited fstab I figured you knew what you were doing.

1. Unmount the hard drive.

```
sudo umount /home/mehdi/Desktop/2nd
```


2. Delete the old mount point (take care, if the drive is not unmounted you will delete your data).

```
rm -rf /home/mehdi/Desktop/2nd
```


3. Make a new mount point in /media (I will use 2nd, you can use what name you will)

```
sudo mkdir /media/2nd
```


4. Edit fstab

```
gksu gedit /etc/fstab
```

Change the line for your HD to :



The 2 = check file system at boot, good idea, you can leave it at 0 if you like ....


5. Mount the HD

```
sudo mount /media/2nd
```

It should now appear in "Computer"


6. Set permissions (if needed)

```
sudo chown -R mehdi.mehdi /media/2nd
chmod 770 /media/2nd
```


7. Make a link (or short cut)

```
ln -s /media/2nd /home/mehdi/Desktop/2nd
```

A link will put a folder in your home directory, in this example called 2nd. This is a direct link, or shortcut, to your HD and will behave the same as your old mount point. 

Your HD will now appear in both "Computer" as 2nd and in your home directory as 2nd.


If there is a step you do not understand, please ask ;)



Thank you, you are a my star.

---

