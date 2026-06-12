---
title: "How to remove a &quot;directory link&quot; to /dev"
date: 2017-03-24
forum: General Help
---

### Post by Hans_van_Leeuwen on 2017-03-24
Some time ago I was experimenting with "chroot".
As result I have now a directory "/home/john/dev" that seems to be "link" to "/dev".
$ ls -ld /home/john/dev
drwxr-xr-x 18 root root 3480 Mar 24 16:30 /home/john/dev

The directory /home/john/dev/contains de same devices as /dev
$ ls -l /home/john/dev
crw-r--r-- 1 root root 10,  10 Jan 13 11L11 adbmouse
<end so on>

$ rm /home/john/dev
rm: cannot remove '/home/john/dev': is a directory
$ rmdir /home/john/dev
rmdir: failed to remove '/home/john/dev': Device or resource busy

When I remove a device in /home/john/dev the device is also removed from /dev.

How can I remove that directory /home/john/dev without removing the contents of /dev?

---

### Post by deadflowr on 2017-03-24
use unlink
like
```
unlink /home/john/dev
```

---

### Post by Dennis N on 2017-03-24
/home/john/dev doesn't look like a link. listing starts with 'd' so a directory. Prove or disprove this with:

**file /home/john/dev**

Could /dev be mounted here? - one of those 'bind' mounts where part of the file system is duplicated. Check with **mount** command.

reference:
[http://unix.stackexchange.com/questions/198590/what-is-a-bind-mount](http://unix.stackexchange.com/questions/198590/what-is-a-bind-mount)

unmounting/removing:
[http://askubuntu.com/questions/156667/how-to-unmount-after-using-mount-bind-option](http://askubuntu.com/questions/156667/how-to-unmount-after-using-mount-bind-option)

---

### Post by Hans_van_Leeuwen on 2017-03-27
$ unlink /home/john/dev
unlink: cannot unlink '/home/john/dev': Is a directory

I dared not to reboot the system because some devices in /dev where remove by my try to delete /home/john/dev,
On Saturday I had to reboot the system because an external disk was unreachable any more.
The reboot succeed.
After the reboot the directory /home/john/dev was empty.
So I could remove the directory /home/john/dev now.
Therefore I cannot check the mount command any more.

Thanks for your response.

---

