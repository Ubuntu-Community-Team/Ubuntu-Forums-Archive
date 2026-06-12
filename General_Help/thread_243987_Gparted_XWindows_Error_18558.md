---
title: "Gparted XWindows Error 18558"
date: 2006-08-25
forum: General Help
---

### Post by UltraMathMan on 2006-08-25
I deleted the partitons on two usb flash drives I have but gparted crashes? when I try to apply new partitions (fat32). The following is outputted to the terminal```
~$ sudo gparted
mkdosfs: /dev/sdb1 contains a mounted file system.

(gparted:18558): Gdk-CRITICAL **: gdk_window_set_geometry_hints: assertion `GDK_IS_WINDOW (window)' failed

(gparted:18558): Gdk-CRITICAL **: gdk_window_resize: assertion `GDK_IS_WINDOW (window)' failed

(gparted:18558): Gdk-CRITICAL **: gdk_draw_segments: assertion `GDK_IS_DRAWABLE (drawable)' failed
The program 'gparted' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 63224 error_code 9 request_code 66 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

``` any help would be appreciated - thanks in advance!

---

### Post by UltraMathMan on 2006-08-26
I did a ```
sudo apt-get remove --purge
``` and reinstalled it with apt-get. Now it's telling me the drive is mounted, so I did ```
sudo umount /dev/sdb1
``` before running gparted. I then ran it again before applying changes and the terminal said it was already unmounted. Suggestions?

EDIT: I think fstab or something might be messed up and the device is either not unmounting or remounting :confused: I'll keep playing around with it

---

### Post by UltraMathMan on 2006-08-28
**bump**

---

