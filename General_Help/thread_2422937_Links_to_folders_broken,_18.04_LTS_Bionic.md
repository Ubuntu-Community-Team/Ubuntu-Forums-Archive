---
title: "Links to folders broken, 18.04 LTS Bionic"
date: 2019-07-15
forum: General Help
---

### Post by nought2 on 2019-07-15
I'm having trouble with shortcut links I've created to folders on an external USB 3.0 HDD. After creating them the links were saved to the Desktop. The links work as expected during the login session in which they were created, but if the system is rebooted or if I log-out/log-in the links become broken.

When I click on a broken link this message is displayed:
> This link "folder-name" is broken. Move it to the rubbish bin?
This link cannot be used because its target "/media/username/drive-name/xxx/yyy/zzz/folder-name" does not exist.
The target does exist. The USB 3.0 HDD was at no stage disconnected from the computer.

The links were created by using Files to navigate to the desired folder in the directory structure, right click desired folder, choose Create Link from context menu. After that I've tried dragging and dropping the link to the Desktop, and moving it to Desktop via the Files right click context menu options. Result after reboot or logout is the same.

Oddly, after a reboot or logout the links remain active when the Desktop directory is accessed via Files. However, the links are broken when accessed from the GUI Desktop.

Is there any way to stop these links from becoming broken?

---

### Post by Impavidus on 2019-07-15
When the system is shut down, the external drive is unmounted and the the links become invalid. After reboot, the desktop is drawn before the external drive is mounted. I'm not sure, maybe the external drive gets mounted automatically if it's already attached at boot time, but it will happen quite late during the login process. When you use the file manager (Nautilus, a.k.a. Files) to access the links, the external drive is mounted.

---

### Post by Dennis N on 2019-07-15
Try using bookmarks (in Files) to your USB device instead. As long as the USB device is mounted before using the bookmark, the bookmarks will work. (If not, all you get is an "Oops!" message, reminding you to mount the device).

---

### Post by Holger_Gehrke on 2019-07-15
Nothing gets mounted at boot unless it's in /etc/fstab. Removable storage devices get mounted at /media/$USER/"Label or UUID of device". Where should they get mounted if nobody is yet logged in ? This gets somewhat obscured by the behaviour of the file manager which silently mounts filesystems on access. You could write a script that starts after login which parses the output of lsblk and mounts devices that are connected but not mounted through udisksctl.

Holgerf

---

### Post by CatKiller on 2019-07-15
Having mounted volumes displayed on your desktop will not break in the way your launchers to unmounted volumes do. It's an option available in each desktop environment, although you may need to install an extension in Gnome to do it because of that project's habit of removing functionality on a whim.

---

### Post by nought2 on 2019-07-15
> **Impavidus said:**
> When the system is shut down, the external drive is unmounted and the the links become invalid. After reboot, the desktop is drawn before the external drive is mounted. I'm not sure, maybe the external drive gets mounted automatically if it's already attached at boot time, but it will happen quite late during the login process. When you use the file manager (Nautilus, a.k.a. Files) to access the links, the external drive is mounted.
I follow the reasoning of your explanation regarding mounting and it being a staged process related to the discover of devices, but what happens on my system still seems odd.

If the links can be re-established in Nautilus (in the 'Desktop' directory in this instance) when the USB HDD is mounted - which is why those links remain active - I do not understand why the links appearing in the Desktop GUI are broken. Both places are representations of the the same directory. 

> **Dennis N said:**
> Try using bookmarks (in Files) to your USB  device instead. As long as the USB device is mounted before using the  bookmark, the bookmarks will work.Yes, that is what I figured I'll have to do if the GUI links are not refreshed after login. The links in the Nautilus 'Desktop' directory are readily accessible.

> **Holger_Gehrke said:**
> Nothing gets mounted at boot unless it's  in /etc/fstab. Removable storage devices get mounted at  /media/$USER/"Label or UUID of device". Where should they get mounted if  nobody is yet logged in ? This gets somewhat obscured by the behaviour  of the file manager which silently mounts filesystems on access.
Again, I follow the reasoning. There is beauty to the logic of Linux. But coming to grips with it is likely to be an enduring learning experience.
> **Holger_Gehrke said:**
> You  could write a script that starts after login which parses the output of  lsblk and mounts devices that are connected but not mounted through  udisksctl.Perhaps, but only after I have leaned how to crawl and walk.

+++

Extending from the idea of shortcut links to an external drive, how are might shortcut links to directories stored in internal drives and partitions handled? Mounting them would not be delayed by the OS having to activate USB drivers, so they should be available to the system promptly at boot or login. How would such links likely behave?

---

### Post by nought2 on 2019-07-15
> **CatKiller said:**
> Having mounted volumes displayed on your desktop will not break in the way your launchers to unmounted volumes do. It's an option available in each desktop environment, although you may need to install an extension in Gnome to do it because of that project's habit of removing functionality on a whim.
Prescient! You answered my query about internal drives/partitions/volumes before it was asked.

Can you suggest an extension that might bring such functionality?

By the way everyone, I've been trying out lots of things with my new 18.04 installation that I thought that the shortcut links might be broken because a conflict had been created somewhere in the system. It seems that what I have seen is not an iatrogenic bug, it's a feature.

---

### Post by CatKiller on 2019-07-15
> **nought2 said:**
> Can you suggest an extension that might bring such functionality?

Nope. The Gnome project's habit of taking out useful functions is one of the reasons I no longer use Gnome, which means I have no experience of any of them and couldn't test if they work before recommending one. You might additionally need to use Nemo, again because features got taken out of Nautilus.

As an aside, KDE is very nice ;)

---

### Post by nought2 on 2019-07-15
> **CatKiller said:**
> As an aside, KDE is very nice ;)
About two weeks in now and I'm more than impressed with Ubuntu. Regarding Linux generally, it seems too many distros are never enough.

---

