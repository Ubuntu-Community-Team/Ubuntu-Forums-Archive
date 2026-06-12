---
title: "ubuntu stops working out anytime a new OS is installed"
date: 2008-02-23
forum: General Help
---

### Post by JimmyHopkins on 2008-02-23
Plus, I have various other issues. If you can help with any, thanks.

1. Whenever I install another OS (fedora, mint linux, debian, etc.) on another partition, my ubuntu partition craps out. (ubuntu is on sda6, the other os is always on sda5). Ubuntu has it's own home partition (sda7), the other os's home is always on it's partition (sda5).  I recently put debian on sda5, and now ubuntu goes into the terminal, rather than gui. So then I type "startx" and it says to hit control+D and gui will start. Hitting ctrl+D does work, it's just annoying that ubuntu always does this. Also, I should probably say every time I install another os, I always let the new OS rewrite GRUB, rather then keep ubuntu's GRUB. This shouldn't be a problem, right?

2. I know this is a n00b question, but I can't find links to gutsy's repository (all of them, main, restricted, universe, multiverse). Could someone give me the links? I need to add ubuntu's repositories to debian, for nvidia drivers, and many other apps I don't want to go find a .deb for.

3. Another n00b question! Ubuntu's file manager window (whether it's gnome or nautilus's fault, I don't know)  adds helpful information, such as links to your desktop, home, ex cetera (look at the left of this screenshot [http://polishlinux.org/reviews/ipod_i_linux/ipod_in_nautilus.png](http://polishlinux.org/reviews/ipod_i_linux/ipod_in_nautilus.png))
In debian, all I get is a small, unhelpful white box (like this, but I'm using gnome, not konqueror: [http://www.marcelgagne.com/images/cwl2004/konqueror_smb.jpg](http://www.marcelgagne.com/images/cwl2004/konqueror_smb.jpg))
How can I change this?

4. Debian can't mount any other partition I have. Debian is on sda6, and I would like to access sda5 (ubuntu), sda7 (ubuntu's home), and sda3 (windows XP). Meanwhile, ubuntu can access everything fine.
Here's the message debian gives me:

libhal-storage.c 1401 : info: called libhal_free_dbus_error but dbuserror was not set.

process 4008: applications must not close shared connections - see dbus_connection_close() docs. this is a bug in the application.

error: device /dev/sda3 is not removable

error: could not execute pmount


and 

libhal-storage.c 1401 : info: called libhal_free_dbus_error but dbuserror was not set.

process 4047: applications must not close shared connections - see dbus_connection_close() docs. this is a bug in the application.

error: device /dev/sda6 is not removable

error: could not execute pmount

You get the point.


Thanks for all your help in advance. Sorry for all the debian-related questions, but I figure debian and ubuntu are pretty similar.

---

### Post by pointone on 2008-02-23
> **JimmyHopkins said:**
> Plus, I have various other issues. If you can help with any, thanks.

1. Whenever I install another OS (fedora, mint linux, debian, etc.) on another partition, my ubuntu partition craps out. (ubuntu is on sda6, the other os is always on sda5). Ubuntu has it's own home partition (sda7), the other os's home is always on it's partition (sda5).  I recently put debian on sda5, and now ubuntu goes into the terminal, rather than gui. So then I type "startx" and it says to hit control+D and gui will start. Hitting ctrl+D does work, it's just annoying that ubuntu always does this. Also, I should probably say every time I install another os, I always let the new OS rewrite GRUB, rather then keep ubuntu's GRUB. This shouldn't be a problem, right?

Ubuntu is most likely crapping out because partitions are being formatted and their UUIDs are being changed. Ubuntu determines which drives to mount at boot by reading /etc/fstab, which specifies the drives by UUID. When the UUID changes, Ubuntu can't find the drive, and throws an error. The simple solution would be to switch from the UUID scheme to the /dev/*d* naming scheme, as in /dev/sda1, /dev/hdb3, etc. If you edit /etc/fstab, it should have some lines like:

```
# /dev/sda2
UUID=########-####-####-####-############ <mount point> ext3 ...
```

You'll want to change it to:

```
# /dev/sda2
/dev/sda2 <mount point> ext3 ...
```

... of course, keeping the path the same as the commented path. You should be able to do this safely with every entry in fstab, although you might want to leave the root partition alone (the one with the "/" mount point) since this one won't be formatted and therefore, the UUID won't change. To be safe, backup your fstab first.

As for letting the other installer rewrite GRUB, most modern distributions' installers detect other Linux operating systems already installed without much issue. This isn't always the case, though. If the installer doesn't detect Ubuntu, you'll need to edit GRUB's menu.lst manually. On the other hand, if you don't let the installer overwrite, you'd need to edit GRUB manually anyway.

One more permanent solution would be to use openSUSE's method of loading other distributions' GRUB separately. I forget the exact way to do this, though. What happens is you can specify Ubuntu's GRUB to simply load the other distribution's GRUB, as long as you don't install the other distribution's boot loader in the MBR.

> **JimmyHopkins said:**
> 2. I know this is a n00b question, but I can't find links to gutsy's repository (all of them, main, restricted, universe, multiverse). Could someone give me the links? I need to add ubuntu's repositories to debian, for nvidia drivers, and many other apps I don't want to go find a .deb for.

```
cat /etc/apt/sources.list
```

However, although Ubuntu is based on Debian, not all Ubuntu packages are compatible with Debian. You can install NVIDIA's proprietary drivers manually, otherwise.

I can't imagine there are many other applications that aren't available in Debian. If you're using Debian Etch (stable), consider upgrading to Lenny (testing).

> **JimmyHopkins said:**
> 3. Another n00b question! Ubuntu's file manager window (whether it's gnome or nautilus's fault, I don't know)  adds helpful information, such as links to your desktop, home, ex cetera (look at the left of this screenshot [http://polishlinux.org/reviews/ipod_i_linux/ipod_in_nautilus.png](http://polishlinux.org/reviews/ipod_i_linux/ipod_in_nautilus.png))
In debian, all I get is a small, unhelpful white box (like this, but I'm using gnome, not konqueror: [http://www.marcelgagne.com/images/cwl2004/konqueror_smb.jpg](http://www.marcelgagne.com/images/cwl2004/konqueror_smb.jpg))
How can I change this?

Look around in the View menu and in the settings dialog. I'm sure there's an option to enable this.

> **JimmyHopkins said:**
> 4. Debian can't mount any other partition I have. Debian is on sda6, and I would like to access sda5 (ubuntu), sda7 (ubuntu's home), and sda3 (windows XP). Meanwhile, ubuntu can access everything fine.
Here's the message debian gives me:

libhal-storage.c 1401 : info: called libhal_free_dbus_error but dbuserror was not set.

process 4008: applications must not close shared connections - see dbus_connection_close() docs. this is a bug in the application.

error: device /dev/sda3 is not removable

error: could not execute pmount


and 

libhal-storage.c 1401 : info: called libhal_free_dbus_error but dbuserror was not set.

process 4047: applications must not close shared connections - see dbus_connection_close() docs. this is a bug in the application.

error: device /dev/sda6 is not removable

error: could not execute pmount

You get the point.


Thanks for all your help in advance. Sorry for all the debian-related questions, but I figure debian and ubuntu are pretty similar.

Try adding these partitions to Debian's /etc/fstab. Check Ubuntu's fstab as an example (you can pretty much copy and paste, but you'll need to check/change the mount points).

Good luck!

---

