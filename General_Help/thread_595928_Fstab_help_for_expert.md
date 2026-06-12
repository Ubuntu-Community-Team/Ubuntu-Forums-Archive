---
title: "Fstab help for expert"
date: 2007-10-29
forum: General Help
---

### Post by Geronimo on 2007-10-29
My system has 2 partition, in one there is Ubuntu 32bit (/dev/sda1) and in the other Ubuntu 64bit (/dev/sda2).
In Ubuntu 32bit there are 2 users (x and y).
At the boot of Ubuntu 32bit I woul like to mount the /dev/sda2 only for me (user x) and not for the other (user y).
In the NTFS volume the solution is putting "uid=1000" (the uid of user x) in the option field but ext3 doesen't support this flag.
I tryed to use "noauto, users" thinking to create a script to mount the partition at the boot of the user x, but the script doesen't work because of only root can use mount. 
Can anyone help me?

---

### Post by p_quarles on 2007-10-29
You could just mount it normally in fstab, and then change the permissions on the mount folder:
```
sudo chmod 744 /media/foo
```
This will make the directories executable only by your user (provided that you are the owner) and root. Directories need to be "executed" to open in Linux, so this will prevent the other user from going to this directory. 

*Don't* change the permissions recursively, though. That will just mess up your entire filesystem. :)

---

### Post by Geronimo on 2007-10-30
Yes, this is a solution, but I have to manually do "sudo chmod 744 /media/foo" each time I boot. I can't make a script that ran at boot becouse of I'm not root.
I would like to do that with a boot script.
There are other solutions?
Thanks

---

### Post by p_quarles on 2007-10-30
It doesn't keep the permissions after you logout? That's really surprising. What exactly are the permissions set to when you log back in?

---

### Post by Geronimo on 2007-10-30
Hops, yes it works,
I thought, it reset the permission at any boot.
Sorry and thanks

---

