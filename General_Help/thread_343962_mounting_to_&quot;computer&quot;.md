---
title: "mounting to &quot;computer&quot;"
date: 2007-01-22
forum: General Help
---

### Post by lotacus on 2007-01-22
As of now, I have two ntfs mount points mounted to /mnt/windows and /mnt/windows2
I bound /mnt/windows2 to /media thinking that I would get an icon under "Computer" where it lists all the mounts such as filesystem, cdrom, usb disk, smart media etc etc, however this did not give the expected results.

Now I have mounts in /mnt/windows2 AND in /media/windows2

first, I would like to unbind /media/windows2 since the bind command doesn't produce expected results. Next I would like to unmount /mnt/windows /mnt/windows2. 

I tried to unmount those directories, using sudo of course (since I used sudo to mount them), and it would unmount them incorrectly. The folders /mnt/windows and /mnt/windows2 are still there but the contents are invisible. The properties of both folders give the filesize of the ntfs volumes, but the contents are inaccessible. I deleted the corresponding entries in FSTAB but that didn't work either. I then rebooted the kernel, only to find that Ubuntu remounted the filesystems. :S

So first, I would like help to successfully unbind and unmount these filesystems and to make sure they don't get re-mounted upon restart.

Second, I would like to mount the filesystems and have them appear in "Computer" where all the automatic mounts for the other hardware filesystems are located. I viewed the properties of those icons in "computer" and the are actually "desktop configuration files". So lastly, after mounting, I would like to know where these desktop configuration files are located so that I can add my  mount points to them.


thanks in advance.

---

### Post by scrooge_74 on 2007-01-22
So the other disks are in a MS computer? did you configure SAMBA for this? Is there an entry in SAMBA for them?

---

### Post by lotacus on 2007-01-24
oh sorry for not being clear... I have a dual boot system. A couple NTFS partitions on the same drive as my linux partitions. I read that if volumes are mounted in the /mnt directory, that Ubuntu would automatically list them in the "computer" section in nautilous and list it under "Places" in the menu bar.

---

### Post by bodhi.zazen on 2007-01-24
By "bind" I presume you mean link.

to unlink:

sudo unlink /media/windows2

HTH

---

### Post by lotacus on 2007-01-29
Well I used the bind command. As of now, the drives are unmounted. Dunno how that happened. Anways, thanks for letting me know how to unlink them. 

Now, any ideas to have them appear in the "places" panel or in the "computer" window?

---

