---
title: "Mountall Order"
date: 2013-12-26
forum: General Help
---

### Post by henriqueferreira2009 on 2013-12-26
Is there a way, on which one can force mountall all to follow a specific order of boot?


  For exemple, i need to automatically mount /dev/sda1 and /dev/sda5,  being /dev/sda1 a directory of the /home folder(later changes :p) and  /dev/sda5 the /home directory. So i keep getting errors because it seems  that mountall trys to mount /dev/sda1 befor /dev/sda5.


  In my fstab the fs's are pointed to UUID values, what makes me think  that this is the cause, but i have not tested with the /dev/sdax  pattern, and as i'm lazy, i'm just(:p) asking here if this does some  sort of difference...

---

### Post by vanadium on 2013-12-26
Doesn't mountall respect the order as listed in /etc/fstab? Otherwise, you could handle this with a symbolic link in your /home folder to /dev/sda1. Alternatively, a "mount bind" issued later during the startup, may also be used to have the contents of your /dev/sda1 on a directory under your /home.

---

### Post by henriqueferreira2009 on 2013-12-26
> **vanadium said:**
> Doesn't mountall respect the order as listed in /etc/fstab? Otherwise, you could handle this with a symbolic link in your /home folder to /dev/sda1. Alternatively, a "mount bind" issued later during the startup, may also be used to have the contents of your /dev/sda1 on a directory under your /home.

If i create a symbolic link of the folder to /dev/sda1, when the /dev/sda6(i mistook for /dev/sda5 but it is sda6, but still...) is mounted, that folder is automaticallly mounted?

Maybe i should post my /etc/fstab here, for better comprehension:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=d44d4066-496d-4a83-bd40-d65c82c482e1 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=12c25951-b1d2-439f-b480-076017340c0e /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=c0b4fe1e-f351-45f4-9b9b-35eac27aebd9 none            swap    sw              0       0
#Videos(/dev/sda1)
UUID=6aa0ecde-0a73-4915-bcab-e2b416d8775d /Vídeos/Seriados ext4 defaults 0 2


What happens is that in the boot it appears that /dev/sda1 could not be mounted on /Vídeos/Seriados...

---

### Post by deadflowr on 2013-12-26
Do you have a folder called /Videos?
Shouldn't it be /home/username/Videos?
How you have it would be in outside the home folder.
Like /bin, or /usr.

---

### Post by henriqueferreira2009 on 2013-12-26
> **vanadium said:**
> Doesn't mountall respect the order as listed in /etc/fstab? Otherwise, you could handle this with a symbolic link in your /home folder to /dev/sda1. Alternatively, a "mount bind" issued later during the startup, may also be used to have the contents of your /dev/sda1 on a directory under your /home.

Oh, nevermind... replying i just figured out what's the problem... I wrote the path to the mount point of /dev/sda1 wrong... Well, i will fix and reboot and confirm if there's some problem... If the problem disappear i will mark this solved... LOL

---

### Post by henriqueferreira2009 on 2013-12-26
Yeah, noob problem solved...

---

