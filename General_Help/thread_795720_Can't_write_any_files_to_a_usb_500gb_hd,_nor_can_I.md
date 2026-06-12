---
title: "Can't write any files to a usb 500gb hd, nor can I share it on the network...."
date: 2008-05-15
forum: General Help
---

### Post by DJSchmidty on 2008-05-15
k, so I have a home file server, and i'm trying to get my 500gb usb device to be apart of the shared folder lists in xubuntu.  I can mount the volume on the desktop, I can even set it as a shared folder under 'shared folders'.  But, its not coming up at all when i'm connected from another computer (ubuntu64)

Also, I can view all the files, open them all just fine, but I noticed that I can't drag and drop files even on the xubuntu computer.  It just rejects the folder, and brings it back ot the original location....

Can someone please tell me how to add a usb HD to my shared folders so I can use it as extra storage?? thanx.

(Maybe something with permissions?? but they are all greyed out)

---

### Post by ibuclaw on 2008-05-15
Open up a terminal and go to the location of the mounted hard-drive.

then type in:
```
ls -l
```
And a list of permissions will be shown.

example output:
[PHP]drwxr-xr-x  2 root root    4096 2008-03-24 16:47 usbdrive[/PHP]

This tells us that root owns the partition, and other users will only have read or execute permissions on the drive (No writing allowed).

To change this, type in:
```

sudo chmod 775 usbdrive -R
sudo chgrp plugdev usbdrive -R

```
Change the word "usbdrive" with the one that is used by your usb hard-drive.

And the permissions of the drive will now look like this:
[PHP]drwxrwxr-x  2 root plugdev    4096 2008-03-24 16:47 usbdrive[/PHP]

And you should now have write permissions to the harddrive.

Regards
Iain

---

