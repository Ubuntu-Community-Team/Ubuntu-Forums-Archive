---
title: "Total noob mounting question"
date: 2008-07-07
forum: General Help
---

### Post by alright on 2008-07-07
When I installed Hardy, I created a FAT32 partition for Vista and Ubuntu to share.  I mounted it as /share.  

Is the location of this then File System/share?

also

Is there any difference in having it mounted as /share then the way many threads had suggested as /media/share??

Thanks a lot.

---

### Post by Titan8990 on 2008-07-07
Really, there is nothing wrong with /share but it is typically somewhat of a "standard" to mount your devices in the /media directory.

Also, why in the world did you make it FAT32 and not NTFS?

---

### Post by sdennie on 2008-07-07
There are some differences.  If you mount it as, for example, "/mnt/share", then gvfs won't take control of it and show it on your desktop or in nautilus.  If you mount in in "/media/share", then it will.

Regardless, I don't recommend mounting it as just "/share" but instead one of the two places I mentioned above depending on the behavior you want.

To answer your first question, "File System" refers to "/" so, in the scenario you've described, it would indeed be "File System/share".

---

### Post by alright on 2008-07-07
> **Titan8990 said:**
> Really, there is nothing wrong with /share but it is typically somewhat of a "standard" to mount your devices in the /media directory.

Also, why in the world did you make it FAT32 and not NTFS?

Well, from all the threads/guides to installing Ubuntu I researched they all suggested FAT32, that Ubuntu had issues with NTFS?  Maybe I misread??  

I was pretty confused when I could easily see everything on my Vista [NTFS] drive.

---

### Post by alright on 2008-07-07
> **vor said:**
> There are some differences.  If you mount it as, for example, "/mnt/share", then gvfs won't take control of it and show it on your desktop or in nautilus.  If you mount in in "/media/share", then it will.

Regardless, I don't recommend mounting it as just "/share" but instead one of the two places I mentioned above depending on the behavior you want.

To answer your first question, "File System" refers to "/" so, in the scenario you've described, it would indeed be "File System/share".

Okay thanks.  I guess I'll remount it in /media/.

---

### Post by bodhi.zazen on 2008-07-07
> **alright said:**
> Well, from all the threads/guides to installing Ubuntu I researched they all suggested FAT32, that Ubuntu had issues with NTFS?  Maybe I misread??  

I was pretty confused when I could easily see everything on my Vista [NTFS] drive.

FAT32 is fine.

You can also use NTFS with the ntfs3g driver.

---

### Post by alright on 2008-07-07
Would it be difficult now to reformat that shared partition as NTFS (if I would choose to)?

Also, could someone point me in the right direction of moving the /share to /media/share

I found 

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

but I'm not sure if this is the same procedure I should take.

Sorry, I literally am just starting ubuntu. 

Thanks again.

---

### Post by bodhi.zazen on 2008-07-07
> **alright said:**
> Would it be difficult now to reformat that shared partition as NTFS (if I would choose to)?

No, but if you re-format you will lose any data on the partition. Also you will need to update the uuid in fstab.

List partitions by uuid with :

```
sudo blkid
```

> Also, could someone point me in the right direction of moving the /share to /media/share

I found 

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

but I'm not sure if this is the same procedure I should take.

Sorry, I literally am just starting ubuntu. 

Thanks again.

```
sudo umount /share

sudo rm -rf /share
sudo mkdir /media/share

gksu gedit /etc/fstab
```

In fstab, change "/share" to "/media/share"
save and quit gedit

```
sudo mount /meida/share
```

---

### Post by alright on 2008-07-07
Thanks so much, that worked great, and I just saw it in the ubuntuguide.  I guess I didn't look as well as I thought I did.  

In regards to changing from FAT32 to NTSF, in fstab I just would change type  from "vfat" to "ntsf" correct?

---

### Post by bodhi.zazen on 2008-07-07
> **alright said:**
> Thanks so much, that worked great, and I just saw it in the ubuntuguide.  I guess I didn't look as well as I thought I did.  

In regards to changing from FAT32 to NTSF, in fstab I just would change type  from "vfat" to "ntsf" correct?

ntfs-3g

(the ntfs driver = ro ; ntfs-3g = rw)

---

