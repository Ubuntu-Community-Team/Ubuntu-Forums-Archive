---
title: "Rooted CD/DVD never ejects"
date: 2006-10-10
forum: General Help
---

### Post by GuiGuy on 2006-10-10
All of a sudden, after working well for a couple of months, a user can not eject CDs/ DVDs from the drive. A dialog states only ROOT can.

I'm sure there's an explanation, so maybe someone can help?

Thanks

---

### Post by codejunkie on 2006-10-10
> **GuiGuy said:**
> All of a sudden, after working well for a couple of months, a user can not eject CDs/ DVDs from the drive. A dialog states only ROOT can.

I'm sure there's an explanation, so maybe someone can help?

Thanks
i have no idea if this will even work but it's work a try,
click on System/Administration/Users And Groups click on your user name then click Properties then user Privliges and make sure **Use CD-ROM Drives** is checked.

---

### Post by GuiGuy on 2006-10-11
> **codejunkie said:**
> i have no idea if this will even work but it's work a try,
click on System/Administration/Users And Groups click on your user name then click Properties then user Privliges and make sure **Use CD-ROM Drives** is checked.

Thanks for that, but I had already eliminated it. The user has full permissions ](*,)

---

### Post by GuiGuy on 2006-10-12
> **GuiGuy said:**
> All of a sudden, after working well for a couple of months, a user can not eject CDs/ DVDs from the drive. A dialog states only ROOT can.


<rant>
grrrrr... I find some things in Linux very frustrating. What some might regard as a feature I find just plain annoying. 
</rant>

Anway, the solution:

Open shell
sudo eject /dev/hdx 

NB: hdx should be the name of the CD/ DVD device

AFter that the "only root can eject the DVD" problems should disappear.


Regards

---

### Post by CatKiller on 2006-10-12
I think that what you'd done is mounted the device as root. Meaning that only root can unmount it. You could change the appropriate lines from /etc/fstab to **users** rather than **user** to allow anyone to unmount it, reagardless of who mounted it.

---

### Post by GuiGuy on 2006-10-12
> **CatKiller said:**
> I think that what you'd done is mounted the device as root. Meaning that only root can unmount it. You could change the appropriate lines from /etc/fstab to **users** rather than **user** to allow anyone to unmount it, reagardless of who mounted it.

Thanks, but I have already eliminated that:

/dev/hdc /media/cdrom0 auto user,atime,auto,rw,dev,exec,suid 0 0

I tried **users** also.

Ad the moment I am still stuck with **sudo eject** ](*,) 

regards

---

### Post by CatKiller on 2006-10-12
The order of the mount options is important - it's perfectly possible to have an option one way and then switch it the other way with a subsequent option. I also find it strange that you have so many options listed. Mine is the fairly simple > /dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by GuiGuy on 2006-10-13
> **CatKiller said:**
> The order of the mount options is important - it's perfectly possible to have an option one way and then switch it the other way with a subsequent option. I also find it strange that you have so many options listed. Mine is the fairly simple

Hi
My options were as set by the Ubuntu install. I only toyed with "user" and "users" after the problem emerged. As I said, the system had been behaving correctly.

Anyway, the good news- I tried "user", rebooted and found that didn't work. **Then I tried "users", rebooted and it seems to be OK once more.**


regards

---

### Post by PC_load_letter on 2008-07-07
> <rant>
grrrrr... I find some things in Linux very frustrating. What some might regard as a feature I find just plain annoying.
</rant>

Anway, the solution:

Open shell
sudo eject /dev/hdx

NB: hdx should be the name of the CD/ DVD device

AFter that the "only root can eject the DVD" problems should disappear.


Regards

I unmounted the CD-Rom drive by mistake in Feisty, when I mounted it back I couldn't eject the CD unless Iam 'root'. What GuiGuy suggested worked like a charm. Thanks.

---

