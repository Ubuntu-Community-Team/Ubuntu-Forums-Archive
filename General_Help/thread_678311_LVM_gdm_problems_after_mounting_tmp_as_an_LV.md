---
title: "LVM: gdm problems after mounting /tmp as an LV"
date: 2008-01-25
forum: General Help
---

### Post by 0mcg0 on 2008-01-25
I'm trying to set up lvm2 and have run into a problem when I try to mount /tmp as an lv.
I'm going through the same process that I was successful in getting /home and /var mounted with,

1 I create the lv /dev/lv-pool/newtmp, and mount it on /mnt
2 sudo su and init 1 to get to single user mode
3 cp -avx /tmp/* /mnt/tmp/
4 umount /dev/lv-pool/newtmp
5 mv /tmp /tmp.old
6 mkdir /tmp
7 mount /dev/lv-pool/newtmp /tmp
8 edit /etc/fstab so that the mounting will happen at boot

booting proceeds without problem to the gdm login screen
but when the user id and password are entered the login hangs
and gives the following in .xsession-errors

---------------------------------------
(process:6075): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:6079): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/flying-hogfish:/tmp/.ICE-unix/6072
Window manager warning: Failed to read saved session file /home/mark/.metacity/sessions/default0.ms: Failed to open file '/home/mark/.metacity/sessions/default0.ms': No such file or directory
** Message: Not starting remote desktop server
-------------------------------------------
If I reverse the process I went through things go back to normal.

Now I don't *really* have to have /tmp as a lv but I curious about what might be 
happening.

Any clues?
btw this is on a fairly fresh gutsy install

---

