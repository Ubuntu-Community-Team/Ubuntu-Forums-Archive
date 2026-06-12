---
title: "All connected USB drives have root permissions and are read-only for regular users"
date: 2017-01-07
forum: General Help
---

### Post by janjaromirhorak on 2017-01-07
About a month ago I have run some regular updates on my Kubuntu 16.10 machine (unfortunately I can't remember the names of the packages). Now, a month later, I tried to write some data on my USB stick and it suddenly doesn't work.

The USB disk is recognized and I am able to connect it simply using the GUI, for example by clicking the "connect drive" icon in Dolphin or Konqueror. I am able to read data from the USB stick, but when I try to copy a file to the stick, i get following errors (*waran* is my username, *A874-2FAD* is the name of the USB stick):

Konqueror:

```
Access denied. Could not write to '/media/waran/A874-2FAD'
```

Copying using command line (*cp testfile.jpg /media/waran/A874-2FAD/*):

```
cp: cannot create regular file '/media/waran/A874-2FAD/testfile.jpg': Permission denied
```

I am able to write / delete / change files as root, as a regular user I have only read permittions.

I tried to unmount the pendrive and remount int with umask=000:
```

sudo mkdir -p /mnt/sd1
sudo umount /dev/sdx1
sudo mount -o rw,users,umask=000 /dev/sdx1 /mnt/sd1
```

But the only thing that changed was the mountpoint.

I have tried it (unsuccessfully) with 4 different USB sticks, 2 SD cards (directly through the card reader on my notebook or using an external card reader) and a CF card (using an external card reader). I have dual boot on this computer, writing to sticks from Windows 10 worked just fine. If it helps narrowing the problem, I am able to print from Kubuntu using an USB cable.

Also I noticed, that I have some new folders in the */media* directory. Previously */media/* contained one folder called *waran/*, in this folder were only the currently connected USBs.

Now it looks like this (*ls -aRl*):

```
.:
total 44
drwxr-xr-x  11 root  root  4096 Oct 22 20:36 .
drwxr-xr-x  25 root  root  4096 Dec 20 21:47 ..
lrwxrwxrwx   1 root  root    45 Oct 15 13:46 .directory -> /etc/kubuntu-default-settings/directory-media
lrwxrwxrwx   1 root  root    42 Oct 15 13:46 .hidden -> /etc/kubuntu-default-settings/hidden-media
lrwxrwxrwx   1 root  root     4 Oct 22 20:36 usb -> usb0
drwxr-xr-x   2 root  root  4096 Oct 22 20:36 usb0
drwxr-xr-x   2 root  root  4096 Oct 22 20:36 usb1
drwxr-xr-x   2 root  root  4096 Oct 22 20:36 usb2
drwxr-xr-x   2 root  root  4096 Oct 22 20:36 usb3
drwxr-xr-x   2 root  root  4096 Oct 22 20:36 usb4
drwxr-xr-x   2 root  root  4096 Oct 22 20:36 usb5
drwxr-xr-x   2 root  root  4096 Oct 22 20:36 usb6
drwxr-xr-x   2 root  root  4096 Oct 22 20:36 usb7
drwxr-x---+  4 waran waran 4096 Jan  5 21:27 waran
    
./usb0:
total 8
drwxr-xr-x  2 root root 4096 Oct 22 20:36 .
drwxr-xr-x 11 root root 4096 Oct 22 20:36 ..
    
(...)
    
./usb7:
total 8
drwxr-xr-x  2 root root 4096 Oct 22 20:36 .
drwxr-xr-x 11 root root 4096 Oct 22 20:36 ..

./waran:
total 20
drwxr-x---+  4 waran waran 4096 Jan  5 21:27 .
drwxr-xr-x  11 root  root  4096 Oct 22 20:36 ..
drwxr-xr-x   2 root  root  8192 Jan  1  1970 A874-2FAD
drwxr-xr-x   2 waran waran 4096 Oct 22 22:19 System\x20Reserved

./waran/A874-2FAD:
total 12
drwxr-xr-x  2 root  root  8192 Jan  1  1970 .
drwxr-x---+ 4 waran waran 4096 Jan  5 21:27 ..

./waran/System\x20Reserved:
total 8
drwxr-xr-x  2 waran waran 4096 Oct 22 22:19 .
drwxr-x---+ 4 waran waran 4096 Jan  5 21:27 ..
```

Any advice? Why did the structure suddenly change? How can I write to my USB sticks directly from Kubuntu?

---

### Post by coffeecat on 2017-01-07
Did you install the package usbmount and, if so, did this problem crop up after installing it?

The presence of mountpoints /media/usb0, /media/usb1, etc suggests you may have done so.

---

### Post by janjaromirhorak on 2017-01-07
Thank you, uninstalling *usbmount* worked for me, now I am able to write to the pendrives again.

---

### Post by coffeecat on 2017-01-07
@janjaromirhorak, I'm glad you managed to resolve your problem. Sadly, this is a perennial problem. I can't really say more than I said in another thread a couple of years ago:

[https://ubuntuforums.org/showthread.php?t=2255751&p=13182999&viewfull=1#post13182999](https://ubuntuforums.org/showthread.php?t=2255751&p=13182999&viewfull=1#post13182999)

---

