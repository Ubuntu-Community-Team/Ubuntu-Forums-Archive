---
title: "Mounting network harddrive at boot"
date: 2007-05-09
forum: General Help
---

### Post by darrenc on 2007-05-09
I have an external network harddrive that Ubuntu will not mount automatically at bootup.  It's in my fstab and can be mounted manually, but the boot sequence is causing it to be skipped when booting.  When I watch the boot, everything in fstab mounts before networking is enabled, so there is no route to the harddrive at the time it tries to mount it.

As it is now, every time I reboot I have to manually give a mount -a command -- when I remember, which is not usually until something fails because it needs to access the external drive.

So, can anyone offer any advice on how I can either automate this process of running the mount command by a script or something like that after everything is up and running or how I can instruct the system to start networking before loading the fstab entries?

Thanks.

---

### Post by IgnorantGuru on 2007-05-09
Not sure how to bring up networking before fstab, or if that's even possible.  As for a script...

First add 'user' to the options in fstab for the device (this allows all users to mount/umount it - you don't need root).

Then save a script like

```

#!/bin/bash
mount [whatever device and mount point]

```

Make the script executable and save it to your user's autostart.  I use KDE so it's the ~/.kde/Autostart folder.  Not sure what it is in gnome.

---

### Post by darrenc on 2007-05-10
> **IgnorantGuru said:**
> First add 'user' to the options in fstab for the device (this allows all users to mount/umount it - you don't need root).

Thanks for the info.  Maybe I was a bit too vague - sorry.  It's a samba mount, which won't allow me to mount it as anything but root (among many other problems it always gives me).

My normal fstab entry for that mount is 
```
//linkstation1/link	/mnt/link	smbfs	dmask=777,passwd=	0	0
```

Note that I have to give it the dmask and null password to allow user level write access.  If I specify either "user" or "users=myself", it still doesn't allow writing.

But, back to the current issue.  If I modify fstab to read
```
//linkstation1/link	/mnt/link	smbfs	user,dmask=777,passwd=	     0	     0
```

and create the script, executing the script as myself returns the following:

> smbmnt must be installed suid root for direct user mounts (1000,1000)
smbmnt failed: 1

A Debian/Ubuntu tips forum I found says this error is because some distros don't configure smbfs properly and gives instructions on how to (supposedly) fix it - by issuing the command "chmod u+s /usr/bin/smbmount /usr/bin/smbumount" to set uid root.  However, like most other people on that forum, it doesn't fix the problem for me.  After setting uid root, I get the following when trying to mount it as a user:

> libsmb based programs must *NOT* be setuid root.
7762: Connection to linkstation1 failed
SMB connection failed

Now, granted a lot of this is total gibberish to me, but isn't it first telling me I can't mount it as a user unless I first set uid root, and then when I do that it's coming right back and telling me I'm not allowed to mount it because it now is set uid root -- exactly the way it previously told me it had to be set???

ARGH  ](*,)

---

