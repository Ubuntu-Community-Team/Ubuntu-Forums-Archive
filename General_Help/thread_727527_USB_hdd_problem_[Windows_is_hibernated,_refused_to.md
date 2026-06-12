---
title: "USB hdd problem [Windows is hibernated, refused to mount. Failed to mount 'dev/sda2'"
date: 2008-03-17
forum: General Help
---

### Post by anebg on 2008-03-17
[IMG]http://img397.imageshack.us/img397/1853/screenshotiw9.png[/IMG]
that is the screenshot.. 
im really new to ubuntu.. this used to be a harddrive i used for XP but the computer crashed and now i just added the external case and it has worked fine for me.. there's not really a way that i can put it into a computer and open windows because i erased all those files..
 is there a way??

---

### Post by BluntBox on 2008-03-17
I don't have any experience with USB drives, but a Sata drive I cannibalized from a XP machine recently had a similar error. I was able to force the drive to mount with the following method.

Create a folder for it to be mounted eg: /media/anebg
```
sudo mkdir /media/anebg
```
Then to mount the device:
```
sudo mount -t ntfs-3g /dev/sda2 /media/anebg -o force
```

You then need to give your user permissions to use the folder (this didnt work correctly till I had rebooted):
```
sudo chown -R yourusername:yourusername /media/anebg
sudo chmod -R 755 /media/anebg
```

After it was mounted forcefully the first time it worked normally.

---

### Post by anebg on 2008-03-17
Tried it and this is what i got..
```
anebg@Andre:~$ sudo mount -t ntfs-3g /dev/sda2 /media/anebg -o force
Windows is hibernated, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, so mounting could be done safely.

```
I have no idea =(
Thanks for reading

---

### Post by BluntBox on 2008-03-18
Hmm after a bit of searching it seems that does not work on hibernated drives.

You could try and force it to be read only with:
```
sudo mount -t ntfs-3g /dev/sda2 /media/anebg -o ro,force
```

It worked for this guy at least. [http://ubuntuforums.org/showthread.php?t=509276](http://ubuntuforums.org/showthread.php?t=509276)

At least then if you have room, you could copy all the data off the drive and format it clean.

---

### Post by anebg on 2008-03-18
Thank You .. It worked for read only.. i wonder if you can change the ro to rw or something like that

---

