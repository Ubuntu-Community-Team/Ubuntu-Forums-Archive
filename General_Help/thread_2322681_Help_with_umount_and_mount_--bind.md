---
title: "Help with umount and mount --bind"
date: 2016-04-29
forum: General Help
---

### Post by lsutiger on 2016-04-29
I have a separate hard drive for my media(music and video). I linked my /home/<user>/Music folder to a folder on the drive with mount --bind like so:
```
mount --bind /mnt/media/Music /home/<user>/Music
```
I ran df on the Music folder and it returned:
```
/dev/sdc1      480589520 327435472 128718388  72% /mnt/media/Music
```
Now I want to remove that link. I have attempted to run umount like so:
```
umount /mnt/media/Music
```
To test I opened two terminals. I cd in ~/Music on one and /mnt/media/Music in the other
I create a folder named temp in the ~/Music folder. I ls the /mnt/media/Music and the temp folder is there. I cd into the temp folder, run touch tmp. I them go to the other terminal, which is in the ~/Music folder, cd to the temp folder and the tmp file is there. When I go to the file manager(Nemo) and go to the properties of the Music folder, it has Link target: /mnt/media/Music
How can I unlink this?

---

### Post by QDR06VV9 on 2016-04-29
I refer to this.... others may have a better solution.
From here [http://www.thegeekstuff.com/2013/01/mount-umount-examples/](http://www.thegeekstuff.com/2013/01/mount-umount-examples/)
> Lazy unmount of a filesystem
This is a special option in umount, in case you want to unmount a partition after disk operations are done. You can issue command umount -l with that partition and the unmount will be done after the disk operations gets finished.
For instance, consider a scenario that a task (i.e: script or any other command) is doing a copy operation on a disk and at the same time you are allowed to issue a unmount with -l, so that unmount would be done once the copy is over (i.e: the disk operation).
```
# umount /mydata -l
```
Forcefully unmount a filesystem
umount provides the option to forcefully unmount a filesystem with option -f when the device is busy as shown below:
```
# umount -f /mnt

```


I hope this is useful

---

### Post by lsutiger on 2016-04-29
Thanks. The forceful umount worked.

---

### Post by QDR06VV9 on 2016-04-29
Nice! Glad it worked out.
Kind Regards

---

