---
title: "Live USB where are the persistent files stored?"
date: 2012-10-29
forum: General Help
---

### Post by sdowney717 on 2012-10-29
I ran the Live USB and was not sure where the files go or how you save them on the thumb drive.

where is 
"stored in reserved extra space" located?
and
How do you store them there where?

---

### Post by bgalfond on 2012-10-29
When using the USB creator, it will give you the option to add persistence, which is what you see there.  The drive will be fat32 formatted and a casper-rw file will be made of up to 4gb (fat32 file size limit).  This is where changes will be stored.

If you want it to act exactly like a CD, choose the bottom option and no casper file will be created and no changes you make preserved between uses.

---

### Post by sdowney717 on 2012-11-23
Ok, so I think this will work to recover persistent files out from the usb booted drive.

from here [http://alexsleat.co.uk/2011/02/06/howto-mount-usb-persistent-casper-rw-file-in-linux/](http://alexsleat.co.uk/2011/02/06/howto-mount-usb-persistent-casper-rw-file-in-linux/)

```
mkdir ~/caspermnt

sudo mount -o loop /media/9E3E-2290/casper-rw /home/scott/caspermnt/

```
the uid number for the usb drive which I copied off the properties page from folder /media

although comes up with root permissions in my home folder.
I can open that folder using gksu nautilus to become root
first shows lock, second shows root view.

How could you mount so the user has permissions to view?

---

### Post by efflandt on 2012-11-23
Use sudo mkdir to create a directory in /media.  Then when you mount it there it should have proper permissions for you to read it.  But to open certain files on it that only have permission for root or someone else, you would need to use sudo.  You could always symlink the /media/whatever-loop-mounted-casper-rw to your home directory.

```
efflandt@XPS8100-1204:~$ **ls -l /media**
total 8
drwx------ 12 efflandt efflandt 4096 Dec 31  1969 SONY8GB
drwxr-xr-x  2 root     root     4096 Jul 14 23:29 vdisk

efflandt@XPS8100-1204:~$ **ln -s /media/vdisk ~/vdisk**

efflandt@XPS8100-1204:~$ **sudo mount -o loop /media/SONY8GB/casper-rw /media/vdisk**

efflandt@XPS8100-1204:~$ **ls -l /media**
total 8
drwx------ 12 efflandt efflandt 4096 Dec 31  1969 SONY8GB
drwxr-xr-x 15 efflandt efflandt 4096 Jul 21 13:22 vdisk

efflandt@XPS8100-1204:~$ **ls -l vdisk**
lrwxrwxrwx 1 efflandt efflandt 12 Nov 23 13:08 vdisk -> /media/vdisk

efflandt@XPS8100-1204:~$ **cd vdisk**
efflandt@XPS8100-1204:~/vdisk$ **ls -l**
total 64
drwxr-xr-x  3 root root  4096 Apr 23  2012 boot
drwxr-xr-x  2 root root  4096 Jul 21 07:45 cdrom
drwxr-xr-x 14 root root  4096 Jul 23 01:44 etc
drwxr-xr-x  3 root root  4096 Jul 21 07:45 home
drwxr-xr-x  3 root root  4096 Apr 23  2012 lib
drwx------  2 root root 16384 Jul 21 12:26 lost+found
drwxr-xr-x  2 root root  4096 Jul 21 07:45 media
drwxr-xr-x  3 root root  4096 Jul 21 13:25 mnt
drwxr-xr-x  2 root root  4096 Jul 21 07:45 rofs
drwxr-xr-x  2 root root  4096 Jul 21 13:22 target
drwxrwxrwt  8 root root  4096 Jul 22 20:26 tmp
drwxr-xr-x  5 root root  4096 Apr 23  2012 usr
drwxr-xr-x  7 root root  4096 Jul 23 01:44 var
```Note that you only need to make the directory for the loop mount point in /media and symlink to your home directory once.  But of course you need to loop mount the casper-rw whenever it is not mounted and you want to see it.  Don't forget to **sudo umount /media/vdisk** (or whatever mount point) when finished with it before unplugging USB.

---

