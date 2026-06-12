---
title: "Sharing NTFS on start-up"
date: 2012-10-19
forum: General Help
---

### Post by LutraMan on 2012-10-19
After much digging around I've found a way to share my NTFS drives, but I don't know how to do it so it will still remain active after I restart the computer.

This is the method I currently use:
first, I unmount the drive (in case it is mounted at start-up)
then I open the terminal and use the following command: ```
 sudo /sbin/mount.ntfs /dev/sdc1 /media/Expansion -o rw,auto,user,fmask=0111,dmask=0000
```
Then I manually share what I want and tick the box 'guest access'

This method works for me, but I have to do it every time after I restart the computer.

I think the only problem is that the mount on start-up does not set NTFS permissions to grant access from the network, and the command I use does (I don't understand the command, I copy pasted it from a forum post and edited it to my needs, and I'm guessing 'fmask=0111' gives the permissions)

I'm thinking of adding a shell script with this command to /etc/init.d but I fear that might not be a very 'neat' way to do it. Also, I will need to find a way to deactivate whatever mounts the drive currently on-startup.

Any help or better ideas?

---

### Post by Scott Goodgame on 2012-10-20
Assuming you are running a GUI, go to software center and install samba, or apt-get install system-config-samba. That is the easiest way to create persistent shares.

---

### Post by yaniraD on 2012-10-20
Good to know. Thanks for the info.  :)

---

### Post by LutraMan on 2012-10-20
The share is not my problem. I can make the share persistent as long as I'll mount on the same directory.

The problem is the mount. I need to mount with spacial permissions for ntfs drives and what's done automatically by ubuntu at the moment does not do it.

---

### Post by papibe on 2012-10-20
Hi LutraMan.

Don't use init/rc.local for that. Instead, set a mounting rule on /etc/fstab (read more [here]("https://help.ubuntu.com/community/Fstab")).

Let us know how it goes.
Regards.

---

