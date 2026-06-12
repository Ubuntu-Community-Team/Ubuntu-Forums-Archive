---
title: "hal-storage-removable-mount-all-options refused uid 1000"
date: 2007-10-31
forum: General Help
---

### Post by fdv1 on 2007-10-31
To date there are five existing threads on this. Not one has an answer, and some purport to have solutions, though none of the solutions have actually worked for me.

[COLOR="Red"]The error is:[/COLOR]
hal-storage-removable-mount-all-options refused uid 1000

This is a very widely reported bug in anything *ubuntu based.

Two examples of bugs filed: [Link 1]("https://bugs.launchpad.net/ubuntu/+source/kdelibs/+bug/98751"), [Link 2]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/115768")

[COLOR="Red"]The actual reason the error happens:[/COLOR]
PolicyKit wasn't ported to Debian and as I understand things, the next major rev of Ubuntu (and therefore it's HAL) shipped anyway.

Solution #1 that does not work (for me, anyway)
sudo mkdir /media/hdb5, then chmod it, then sudo mount /dev/hdb5 /media/hdb5
Reason this does not work:
Because on reboot, it all goes away!

Solution #1a that also does not work (for me, anyway)
Doing the above and also editing fstab to do this for you, as in adding
/dev/hdb5 /media/DISK0 ntfs-3g defaults,locale=en_US.UTF-8 0 0
Reason this does not work:
Because on reboot, not only does it not work, but your devices have moved one letter down the alphabet -- and hdb5 doesn't show anywhere!

Solution #2 that does not work (for me, anyway)
[this link]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")
Reason this does not work:
Has good info, but no solution is listed for this infamous error.

Solution #3 that does not work (for me, anyway)
Use some sort of graphical file manager to check some sort of box. I use Kubuntu, and someone suggested checking a "user" box on a tab in Dolphin.
Reason this does not work:
The tab doesn't appear for devices that generate this error.

There is ONE ACTUAL solution and TWO workarounds to this problem.

[COLOR="Red"]Actual solution #1:[/COLOR]
[PolicyKit]("http://www.google.com/search?hl=en&safe=off&q=refused+uid+1000+policykit+ubuntu&btnG=Search") must be added to all *ubuntu distributions.

[COLOR="Red"]Workaround #1[/COLOR]
/dev/YOURDRIVE /media/NAMEYOUWANTTOUSE ntfs-3g users,defaults,locale=en_US.UTF-8 0 0
By adding "users" you allow anyone with any permission level to read/write to all drives.

[COLOR="Red"]Workaround #2[/COLOR]
REMOVE this:
+ if (!invoked_by_uid || strcmp(invoked_by_uid, "0"))
+ if (!privilege || strcmp (privilege, "hal-storage-removable-mount"))
+ permission_denied_privilege (privilege, invoked_by_uid);

Which file? No idea. I haven't found anyone who could tell me. If I knew, I'd recompile whatever file it was and submit it to someone in authority or offer it for download on my own website.

I hope Workaround #1 helps you folks who have this problem!




See also:

---

### Post by Jpr80 on 2007-10-31
> **fdv1 said:**
> 
Solution #3 that does not work (for me, anyway)
Use some sort of graphical file manager to check some sort of box. I use Kubuntu, and someone suggested checking a "user" box on a tab in Dolphin.
Reason this does not work:
The tab doesn't appear for devices that generate this error.



I actually got it to work this way in KDE. In Dolphin, right-click the media, go to properties -> mounting and uncheck the "mount as user"-checkbox.

---

### Post by fdv1 on 2007-11-01
> **Jpr80 said:**
> I actually got it to work this way in KDE. In Dolphin, right-click the media, go to properties -> mounting and uncheck the "mount as user"-checkbox.

No... no. *The options are greyed out.*

---

### Post by tlu on 2007-11-02
> **Jpr80 said:**
> I actually got it to work this way in KDE. In Dolphin, right-click the media, go to properties -> mounting and uncheck the "mount as user"-checkbox.

Thanks for this hint - this works for me :)

---

### Post by Sikarian on 2007-11-03
> **Jpr80 said:**
> I actually got it to work this way in KDE. In Dolphin, right-click the media, go to properties -> mounting and uncheck the "mount as user"-checkbox.

This worked for me as well.  Thumbs up!

---

### Post by amarra on 2007-11-07
> **Jpr80 said:**
> I actually got it to work this way in KDE. In Dolphin, right-click the media, go to properties -> mounting and uncheck the "mount as user"-checkbox.

This works for me also, using Konqueror as file manager, from the system:/media folder

---

### Post by nuclearlee on 2007-11-08
> **Jpr80 said:**
> I actually got it to work this way in KDE. In Dolphin, right-click the media, go to properties -> mounting and uncheck the "mount as user"-checkbox.

AWESOME!!!  This worked for me too (for my ntfs external USB hd). Thanks...

---

### Post by dirtyscurty on 2007-11-12
I had some issues with an external USB hard drive. I guess I didn't "Safely Remove" it from a windows system. I ran the following in the terminal:

mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

<of course change the /dev/sbd1 and /media/sdb1 drive info to how your system detects your drive. Usually you can tell what its calling it by trying to open the drive in dolphin. The name will be in the title of the window.>

it reset the $LogFile

and I was able to mount the drive and see my files.

damn windows. 

:guitar:

---

### Post by reets on 2007-11-24
unchecking "Mount as user" worked for me also (it was the only thing i tried too).

---

