---
title: "Drive Permissions"
date: 2007-06-14
forum: General Help
---

### Post by strange_cathect on 2007-06-14
Hello,

I have added a second hard drive which I used Gparted to format to ext3.  But now only Root has RW permissions to the drive.

Can someone help me with the correct edit to fstab?  Here is my drive info:

> root@alan-desktop:/home/alan# mount
**/dev/sda2 on / type ext3 (rw,errors=remount-ro)**
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdd1 on /media/External type ext3 (rw,noexec,nosuid,nodev)
/dev/sde2 on /media/ALAN TAYLOR type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
root@alan-desktop:/home/alan# 


---

### Post by NeoLithium on 2007-06-14
Assuming that it's your /media/External mount, you can always just chown it to yourself with the following command:

```
sudo chown YOURUSERNAME /media/External
```

---

### Post by strange_cathect on 2007-06-14
Thanks, but this isn't working.

**sudo chown -R alan:alan /media/disk-1**

I've determined that the above command should work, but when I enter this at the prompt I'm told that I don't have permissions to write to this drive. 

Any ideas?

---

### Post by DagMan on 2007-06-14
Is the drive sde partition sde2...
mounting at the folder /media/ALAN TAYLOR
Try sudo chown -R alan:alan "/media/AlAN TAYLOR"
or unmount it and rename it to something without spaces.

If the folder is the /media/disk-1 that you've posted above,  try chown first with the drive unmounted and then mount it and use the -R option.

If it is the bolded entry in your first post, /dev/sda2 on / type ext3 (rw,errors=remount-ro)
then the / filesystem wouldn't be getting changed and you'de just want to do the folder /home/alan or "/home/ALAN TAYLOR" or whatever the home folder is.

Can you be a little more specific like which drive and partition it is, which folder it's mounting at, aso if you can post the output of 'cat fstab' here it would help.
Also does the folder where the disk mounts already exist or is it created for example when you plug in an external drive and it's created.

---

### Post by strange_cathect on 2007-06-14
sudo chown -R alan:alan /media/disk-1

Ok, I forgot to mount before I did this command.  Now I can write to the drive; however, I am unable to delete a test file I saved to it.  In fact, the "delete" option is grayed out and is not selectable in the right click menu.  

Ideas?

---

### Post by strange_cathect on 2007-06-14
Reboot cures all.  Thanks, guys!

---

