---
title: "Ubuntu 14.04 and Virtual Box shared folder automount issue"
date: 2015-03-29
forum: General Help
---

### Post by MarcusL on 2015-03-29
Hi all, I just today started playing with VirtualBox and Ubuntu 14.04 but I am stuck at a point and need some help.

I have installed the Guest Additions and created a shared folder in Windows for the ubuntu session to use, all seems to be working ok as the folder auto mounts at > /media/sf_istandards. 

The folder name in the share name from Virtual Box side is > istandards but I notice it adds the > sf_ when it mounts to > /media/ to end up as > /media/sf_istandards/.

I have been battling with getting the folder to mount to > /var/www.  I have edited the /etc/fstab with various versions of this command, and all stop during the boot process and call out an error that I can hit "s" to skip.

What is wrong with the command?

```
sf_istandards /var/www vboxsf  defaults  0   0

```
I have also tried this with the same result:

```
istandards /var/www vboxsf  defaults  0   0

```

---

### Post by TheFu on 2015-03-29
Does /var/www exist?
Did you umount the /media/sf_istandards/ first?

Besides that, seems like you've done very well. My notes about this: [http://blog.jdpfu.com/2008/10/26/virtualbox-host-drive-access](http://blog.jdpfu.com/2008/10/26/virtualbox-host-drive-access) 

BTW, the names used by the media automatic mounting tool is based on the disk label.
BTW, if that mount isn't a linux file system, there will be permissions problems.  That might be fine for static files to be shared, but not for dynamic programs. For those, file and directory permissions are absolutely critical to the web server AND for system security.

---

### Post by bardo2 on 2015-03-29
Off the top of my head: did you add yourself to the vboxsf group in the guest (sudo adduser <your username here> vboxsf) and reboot the guest?

And while we're at it: turned off automounting for this shared folder (to avoid generation of sf_...)

OMG, while verifying, i ran into the same problem. (LOL)
...until i found: [http://ubuntuforums.org/showthread.php?t=2074022]("http://ubuntuforums.org/showthread.php?t=2074022")

What i did in my VM's is to unmount the shared folder and create a symlink from /media/sf_<name> to the place, where i want the mount to appear, chown that one to root:vboxsf and reboot with automount set to ON. Works fine thereafter.

---

