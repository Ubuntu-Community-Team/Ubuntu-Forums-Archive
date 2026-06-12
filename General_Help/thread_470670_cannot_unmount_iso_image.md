---
title: "cannot unmount iso image"
date: 2007-06-11
forum: General Help
---

### Post by joriad on 2007-06-11
I discovered a mounted iso image icon buried beneath another desktop icon. When I attempt to unmount the iso I get this error:

Unable to unmount the selected volume 
umount: /dev/loop0: not mounted, 
Error: umount failed

The iso image I originally mounted the volume from had been deleted several days ago, so it no longer exists. I think that is what is causing the problem, but my question is, How do I solve the problem and unmount the volume?

---

### Post by tszanon on 2007-06-11
> **joriad said:**
> I discovered a mounted iso image icon buried beneath another desktop icon. When I attempt to unmount the iso I get this error:

Unable to unmount the selected volume 
umount: /dev/loop0: not mounted, 
Error: umount failed

The iso image I originally mounted the volume from had been deleted several days ago, so it no longer exists. I think that is what is causing the problem, but my question is, How do I solve the problem and unmount the volume?
Hmm...have you tried using another ISO image instead? Like, rename an ISO image to match the deleted one's filename or create one with that filename. Then, see if you can mount/unmount it.

---

### Post by joriad on 2007-06-11
Ok, I tried to create a new iso using the same name and unmount it that way, but it was unsuccessful. I also tried to mount and unmount another iso, it mounted fine but the new iso failed to unmount also. It does seem the only way I can unmount them is by rebooting. Now I have no iso files mounted. However after I mount any iso I have to reboot to unmount it. This is how it was mounted ```
sudo mount -t iso9660 -o loop '/home/john/Desktop/file.iso' /media/iso
``` 
I have in the past been able to unmount all iso files.

---

### Post by joriad on 2007-06-11
This is the error I get every time
Unable to unmount the selected volume
umount: /dev/loop0: not mounted,
Error: umount failed

---

### Post by drs305 on 2007-06-11
With the command you are using to mount it, have you tried unmounting with:

```
sudo umount /media/iso
```

---

### Post by joriad on 2007-06-11
I had tried that earlier wih no success, but now after another reboot it is working. Thats weird. Looks like everything is now working fine.

Thanks for your help.

---

