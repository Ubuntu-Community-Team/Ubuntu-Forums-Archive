---
title: "How to lock down Ubuntu so it's locally secure"
date: 2007-11-24
forum: General Help
---

### Post by CrazyGuy123 on 2007-11-24
I need a PC to put in a holiday house.  It must be able to browse the web and play games.  It must not be possible for any user of the system to break it.  I was considering Ubuntu.

I was going to give the user a single non-admin account and have it auto-login.

It is important that the computer is fully reset every week - so all bookmarks, settings, downloaded files, cookies, history etc. are cleared every friday.   I thought I could do that by deleting the user profile folder on a startup job?

Also, the system must be secure from people trying to mess with it by fiddling with the bootloader etc. to gain root access.  I can lock the BIOS by putting a passwod on it, and I can lock the case to prevent people resetting the CMOS.  How can I lock GRUB so it will not display a menu?  How can I ensure that Ubuntu will never drop to a root prompt if something like a fsck fails?  How can I ensure the user cannot fill their user profile folder on the hard disk so the system cannot boot?

Any suggestions how I should go about that?


If the above is too hard, I could consider a dual disk approach, where manually every friday the disk is wiped and replaced with the "known clean" disk contents.

---

### Post by CrazyGuy123 on 2007-11-24
Just to clarify, if you know solutions to any of those problems your help is appreciated,

---

### Post by gepatino on 2007-11-24
I would try setting the default, non-privileged, user home dir to /tmp or some subdir inside /tmp

By default, /tmp is cleaned after each reboot, so you only need to restart the machine and you have a clean default user.

If you decide to use a subdir inside /tmp, make shure to create it automatically before the user logs on, or you're going to have problems.

---

### Post by PmDematagoda on 2007-11-24
[Pessulus]("http://www.gnome.org/learn/admin-guide/latest/lockdown.html") could be useful for you. It can be install using:-

```
sudo apt-get install pessulus 
```

---

### Post by Martin Witte on 2007-11-24
to hide the grub menu, add to /boot/grub/menu.lst
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```
see [http://www.gnu.org/software/grub/manual/grub.html#Hidden-menu-interface](http://www.gnu.org/software/grub/manual/grub.html#Hidden-menu-interface)

---

### Post by Sef on 2007-11-24
System > Administration > Users and Groups and set up a new user.   By default they do not have admin privileges.  Also I would set the computer to boot into the new user without a password required.  System > Administration > Login Window.

---

### Post by CrazyGuy123 on 2007-11-24
> **Sef said:**
> System > Administration > Users and Groups and set up a new user.   By default they do not have admin privileges.  Also I would set the computer to boot into the new user without a password required.  System > Administration > Login Window.


Thanks everyone.

I found how to put a password on grub as well as hiding the menu - now they can't get in even if they hit escape to see the menu.

I'm not as worried about locking down gnome as long as none of the chnges persist through a friday.  I like the idea of using /tmp for a home dir, but I think it may upset the users their downloaded files etc. not persisting through a reboot - they only need to be deleted on fridays.

I solved the problem of users filling up the filesystem - have /home on a new partition, and then even if it fills up it doesn't matter.

Another question - is there a quick and easy way of logging web access?  say a transparent logging proxy on localhost?  I ask because the users could do anything with the net connection on this machine, and it would be nice to have evidence of who did it if something illegal happens on the connection.

---

