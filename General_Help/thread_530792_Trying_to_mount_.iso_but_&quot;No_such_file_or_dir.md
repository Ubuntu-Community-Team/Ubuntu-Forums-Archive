---
title: "Trying to mount .iso but &quot;No such file or directory&quot; error"
date: 2007-08-20
forum: General Help
---

### Post by Waelwulf on 2007-08-20
I've been trying to mount the gparted-livecd.iso file, which is on my desktop but when I try to mount it with this: > sudo mount -o loop gparted-livecd.iso /mnt/try/ it just gives me the error "File or directory not found." What am I doing wrong?

---

### Post by jakev383 on 2007-08-20
> **Waelwulf said:**
> I've been trying to mount the gparted-livecd.iso file, which is on my desktop but when I try to mount it with this:  it just gives me the error "File or directory not found." What am I doing wrong?

Try using the full path for the ISO. I'm assuming you made a dir called /mn/try as well....

---

### Post by Waelwulf on 2007-08-20
I'm just not certain how to create those new directories and all that and target it from the desktop. This guide: [http://gparted-forum.surf4.info/viewtopic.php?pid=1725#p1725](http://gparted-forum.surf4.info/viewtopic.php?pid=1725#p1725) tells me to create a temporary directory and all that but I don't know why I can't just mount it regularly?

---

### Post by Waelwulf on 2007-08-20
I just tried this > sudo mount -o loop gparted-livecd.iso desktop but it couldn't find it there either, which is where it currently is. Forgive my confusion but I'm just generally pretty newbish to Ubuntu.

---

### Post by wirelessmonkey on 2007-08-20
If your gparted iso is on your desktop:
sudo mkdir /mnt/try
sudo mount -o loop ~/Desktop/gparted-livecd.iso /mnt/try

---

### Post by DirtDawg on 2007-08-20
My notes concerning iso mounting are slightly different than the method you are using.
First, you must create the /media/isoimage directory:
```
 sudo mkdir /media/isoimage 
```
Then mount the iso and direct it to the new directory. Note this command is different than the one you are using now. Of course, replace "path/to/iso" with the path of the iso you're trying to mount. "/home/Waelwulf/gparted-livecd.iso", for example.
```
  sudo mount path/to/iso /media/isoimage/ -t iso9660 -o loop 
```
Then you can access the iso through /media/isoimage. It will probably also show up on your desktop. To unmount, use:
```
 sudo umount /media/isoimage 
```
Note that's "umount", not "unmount".

This method works for me without fail. I hope it works for you.

---

### Post by jakev383 on 2007-08-22
> **DirtDawg said:**
> 
```
  sudo mount path/to/iso /media/isoimage/ -t iso9660 -o loop 
```


Your command should work.  I can't see how they couldn't.
As a side note, I believe the -t iso9660 used to be required, but now it should autodetect the format.  You should only need to use it when it doesn't correctly detect the format of the disk.  It works for me both ways, and I only just recently dropped using the -t flag to save time (I mount ISOs on a server all the time).

---

### Post by DirtDawg on 2007-08-22
> **jakev383 said:**
> Your command should work.  I can't see how they couldn't.
As a side note, I believe the -t iso9660 used to be required, but now it should autodetect the format.  You should only need to use it when it doesn't correctly detect the format of the disk.  It works for me both ways, and I only just recently dropped using the -t flag to save time (I mount ISOs on a server all the time).

Good to know

---

