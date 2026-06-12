---
title: "External HD mounts as 755"
date: 2007-10-29
forum: General Help
---

### Post by Julolidine on 2007-10-29
So, I created a folder /media/disk and made it 777 RWX privileges.  Then I plugged in my external, it didn't automagically mount, so I mounted it 

sudo mount /dev/sdb1 /media/disk/

Which when I check, it gives me;

drwxr-xr-x 13 root root 32768 1969-12-31 16:00 disk


So, I tried chmod -R 777 to the whole thing, but it still doesn't do anything.    I also tried to move a file to the harddrive from my own, and even as a superuser, it won't let me claiming ownership won't be preserved.  

:confused::confused::confused:

---

### Post by p_quarles on 2007-10-29
Is this external drive formatted in FAT or NTFS? If so, it won't change permissions to anything but 755. You should be able to get it to work by making yourself the owner, however:
```
sudo chown -R *username* /media/disk
```

---

### Post by Julolidine on 2007-11-05
Thanks for that reply, it really helped me out.  It is indeed a FAT partition.  

The next question I have if anyone is out there is why does my externals mount sometimes with absolutely no intervention from me, and other times I have to do it manually.  Does anyone know the processes/programs involved in the automagic mounting?

---

