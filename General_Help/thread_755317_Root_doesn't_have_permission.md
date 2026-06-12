---
title: "Root doesn't have permission?"
date: 2008-04-14
forum: General Help
---

### Post by Helgiks on 2008-04-14
I have an external hard drive that I keep allot of my files, but than all of a sudden I get an error message saying 

Couldn't display "/media/drive/some-folder".
Access was denied.

user@computer:/media/disk$ ls -l
drwx------ 3 user root 32768 2008-04-14 17:59 some-folder

I have tried changing group of the folder, but I get an error message saying that I don't have permission to change that, even when logged in as root.

root@computer:/media/disk# chown user:user some-folder/
chown: changing ownership of `some-folder/': Operation not permitted
root@computer:/media/disk# chgrp user some-folder/
chgrp: changing group of `some-folder/': Operation not permitted

I have also tried to change the permission

# ls -l
drwx------ 3 user root 32768 2008-04-14 17:59 some-folder
# chmod 666 some-folder && ls -l
drw------- 3 user root 32768 2008-04-14 17:59 some-folder

What just happened and why shouldn't root have the permission to change the group? - I have no Idea what just happened to my drive but I'm getting annoyed since I need to get to those files, not feeling like working with them as root with sudo all the time.

---

### Post by cmnorton on 2008-04-14
What is the output of df?

Is this drive automatically mounted in /etc/fstab? If so, check the permissions there. 

If you are manually mounting the drive, have you changed how you mount the drive?

---

### Post by aysiu on 2008-04-14
If it's NTFS or FAT32, you can't change ownership or permissions, as those filesystems do not support Linux permissions. You have to mount them with certain options. For more details:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Helgiks on 2008-04-14
user@computer:~$ df | grep "Filesystem\|sdb1"
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            488264736 306708960 181555776  63% /media/disk

It's W95 FAT32 filesystem, and no, I didn't change the way I mount it.

Well that explains why I can't change the permission, but why did it suddenly tell me I could access it, well, guess I'll just keep try fixing this.

EDIT: I think that link can help, thanks.

---

