---
title: "Dynamically Link drectories with fstab?"
date: 2013-03-03
forum: General Help
---

### Post by twinturbotom on 2013-03-03
I have a shared NTFS primary parition where I store my Documents, Pictures, & Downloads.  I don't want to mount it as my /home as there are other files in a home direcotry that shouldn't exist in my shared directory. The files should exist on the shared partition not physically in the /home partion.

The way I accomplished this was by mounting shared parition directories to the corresponding /home/DIR in the /etc/fstab.  IS this the proper way to do this?

```

/media/USER/shared/Pictures /home/USER/Pictures    none    bind    0     0
/media/USER/shared/Documents /home/USER/Documents    none    bind    0     0
/media/USER/shared/Downloads /home/USER/Downloads    none    bind    0     0
```

The shared primary partion is automaticallly mounted in /media/USER (not sure how with no fstab entry) and shows up in nautilus "Devices" but doesn't work there?  Yet I can go into the shared drive or /home/USER/Documents and read/write just fine.  I've changed user groups of the /media/USER to my user / group.

As you can see I'm just dangerous enough in linux to make it work but would love thoughs on the best way to impliment this / fix the Device from showing up and/or not working?

---

### Post by oldfred on 2013-03-03
You cannot use same name for both the default Pictures in /home and the Pictures folder from your shared data partition. I do not use bind, do cannot really help. Some suggest bind as it may work with Samba better, but I just use links. 
Nautilus will automount partitions in /media if you click on them and they are not already mounted. 

With my links I have to delete the default Pictures folder in /home and link the Pictures folder from my shared NTFS data partition. If you want both in /home you need to rename your shared Pictures to Pictures2 or Pictures_Shared or something different as the mount point in /home.

       Splitting home directory discussion and details See posts by Morbius1 as he prefers bind:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by twinturbotom on 2013-03-03
Thanks for sharing your wealth of knowledge; it is much appreciated!  I'll dig throught the links and update my final implimentation.

---

### Post by Morbius1 on 2013-03-03
> The shared primary partion is automaticallly mounted in /media/USER (not sure how with no fstab entry)
You are using Ubuntu 12.10 right? Um ... I don't think it is automatically mounted. At least not automatically mounted at boot. It may appear that way because it's listed in Nautilus and when you click it it just brings you to the contents of that partition but what it's doing in the background is mounting it for you when clicked.

The reason I think that is because no human would ever mount anything under /media/$USER ( look at the permissions of /media/$USER and you will see why ). If you decide to use symlinks or bind I would have the partition mount automatically in fstab and I would mount it somewhere else like /media/shared or even /mnt/shared. For example:

Create a mount point in /mnt:
```
sudo mkdir /mnt/shared
```
Add a line to fstab ( note this line should appear above the bind lines in fstab if you are using bind):
```
UUID=DA9056C19056A3B3 /mnt/shared ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```
[COLOR=#0000cd] *To find the correct UUID number for your partition run this command:*[/COLOR]
```
sudo blkid -c /dev/null
```
Unmount the already mounted partition:
```
 sudo umount /media/USER/shared
```
Then run this command which will test for syntax errors and mount the partition:
```
sudo mount -a
```

[COLOR=#0000ff]If you use bind you will need to change the path to point to the new mountpoint: /mnt/shared/Picutes for example.[/COLOR]

---

### Post by twinturbotom on 2013-03-03
Thank you for the help and options, I appreciate the education and direction.

Morbius, I originally changed the group and user permissions for my /media/$USER direcotry thinking that my user account can then use that as a mounting location for anything specific to the account.... is that a bad idea?  As you can tell I'm dangerous enough in linux to impliment bad solutions!  I want the share drive to only be accessible for this account.

I ended up mounting the shared drive in fstab (/media/$USER/shared).

```
UUID="###" /media/$USER/shared ext2 defaults 0     0
```

I am pretty sure I originally formated the drive as NTFS but GParted is saying it's ext2?

  Then I deleted my ~/DIRs and created soft symbolic links to the corresponding DIRs in my shared drive.

```
ln -s /media/$USER/shared/Pictures ~/Pictures
```

Thanks again, let me know if I should change what I have.

---

### Post by Morbius1 on 2013-03-03
/media/$USER is a system directory in Ubuntu 12.14. It's controlled by Access Contol Lists and one is created automatically for each local user such that no one can access anything within it except that user ( and root ) . Any non-fstab specified internal or external partition like a usb device for example will automatically mount to to /media/$USER/LABEL. Not sure what will happen if you override the permissions set by the system so we will use your setup to see what happens. 
> I am pretty sure I originally formated the drive as NTFS but GParted is saying it's ext2?
That's kind of weird isn't it. If it's mounting without error it must be ext2 then. Not a filesystem I would have chosen but it it all works for you then don't mess with it.

---

