---
title: "How to copy pictures from desktop to USB drive in  13.04?"
date: 2014-02-21
forum: General Help
---

### Post by hodad on 2014-02-21
I have a folder with pictures on my desktop.  I want to copy them to my thumb drive for transfer to my windows 7 pc.  The thumb drive is formatted for FAT32.

The problem is:  when I copy the pix to the thumb drive, the pix are "read only" and I can't do anything with them.  THe Windows PC only recognizes one of the pix.

I can right click on properties, and change to "read and write", but when I exit properties, and go back into the same picture, it says "read only".  I assume that this is because I'm not the "owner" (even though I took the pictures and copied them onto the desktop!).

Does anyone know a SIMPLE procedure for allowing me to copy pictures from the desktop onto a thumb drive without having to go into the terminal and changing the permissions on each file?  (which, by the way, I've tried with sudo CHOWN and CHMOD all morning long to no avail).

Sorry if I sound disgusted at this point, but how can such a simple and common process turn into such a nightmare!

---

### Post by sudodus on 2014-02-21
Are you automounting the USB pendrive with the file browser?

In that case I think it is mounted on

```
/media/your-user-name/usb-pendrive-label
```

whatever 'your-user-name' and 'usb-pendrive-label' are.

It might help if you change the permissions of ```
/media/your-user-name
``` once, to make this work in the future. Try this command (where you insert your actual user name instead of the string  'your-user-name')

```
sudo chmod ugo+rwx /media/your-user-name
```

---

### Post by bab1 on 2014-02-21
> **sudodus said:**
> Are you automounting the USB pendrive with the file browser?

In that case I think it is mounted on

```
/media/your-user-name/usb-pendrive-label
```

whatever 'your-user-name' and 'usb-pendrive-label' are.

It might help if you change the permissions of ```
/media/your-user-name
``` once, to make this work in the future. Try this command (where you insert your actual user name instead of the string  'your-user-name')

```
sudo chmod ugo+rwx /media/your-user-name
```
I believe this is all handled by udev.  If you manually create a mount point udev will not use it.  It will create another one with a different name (e.g username2).

---

### Post by sudodus on 2014-02-21
Yes, you are right about the mount points. But I am talking about changing the permissions of

```
/media/your-user-name
```

while the mount points are
```

/media/your-user-name/usb-pendrive-label
```

I have done it myself to get around the same (or a similar) problem.

---

### Post by Impavidus on 2014-02-21
Fat32 itself doesn't support permissions and, if automounted, the permissions for the usb drive should be OK.

Maybe the thumbdrive is just broken. It will be remounted read-only and this is consistent with Windows having difficulty reading it.

---

