---
title: "Device Icons"
date: 2008-01-05
forum: General Help
---

### Post by glennzo on 2008-01-05
Hey folks. I would like to hide the device icons that are automatically placed on my desktop. Using the configuration editor won't do it because that will also hide the icons for any inserted devices or CD/DVD's. I want that functionality but I don't need icons for other partitions. Any thoughts?

---

### Post by CatKiller on 2008-01-05
Look at how to modify your /etc/fstab. If you change the mount points of those partitions so that they are not mounted in /media (/mnt instead, say) then the icons will not appear on your desktop.

---

### Post by glennzo on 2008-01-05
Nah. That won't do it. It doesn't matter where they're mounted. That has nothing to do with whether they display on the desktop or not.

---

### Post by CatKiller on 2008-01-05
That's not true. Volumes mounted in /media are displayed on the Desktop. Volumes mounted elsewhere are not.

At least, in Gnome. You don't say what you're using.

---

### Post by p_quarles on 2008-01-05
> **CatKiller said:**
> That's not true. Volumes mounted in /media are displayed on the Desktop. Volumes mounted elsewhere are not.

At least, in Gnome. You don't say what you're using.
That's kind of using a powerdrill on a thumbtack, though.

To make the volume icons disappear:
```
gconf-editor
```Select Apps >> Nautilus >> Desktop
Uncheck the box next to "volumes_visible"

---

### Post by glennzo on 2008-01-05
> **CatKiller said:**
> That's not true. Volumes mounted in /media are displayed on the Desktop. Volumes mounted elsewhere are not.

At least, in Gnome. You don't say what you're using.I'm using Gnome / Ubuntu Gutsy. I made the change to one of the mounts before I posted a reply. Didn't change a thing. When I re-mounted the partition as /mnt/xp it showed up on the desktop.

---

### Post by glennzo on 2008-01-05
> **p_quarles said:**
> That's kind of using a powerdrill on a thumbtack, though.

To make the volume icons disappear:
```
gconf-editor
```Select Apps >> Nautilus >> Desktop
Uncheck the box next to "volumes_visible"That method will also keep inserted devices from showing up on the desktop. Insert a thumb drive. It's not going to show up.

---

### Post by aidanr on 2008-01-05
CatKiller's advice is correct
[http://ubuntuforums.org/showthread.php?t=415702](http://ubuntuforums.org/showthread.php?t=415702)
[http://www.joshgerdes.com/blog/2007/10/30/move-mounted-partition-icons-from-the-desktop-in-ubuntu-710/](http://www.joshgerdes.com/blog/2007/10/30/move-mounted-partition-icons-from-the-desktop-in-ubuntu-710/)

---

### Post by glennzo on 2008-01-05
Pointing to a few other threads proves nothing. As I said, I made the changes and things were still the same. I followed the advice given. I will admit that I didn't reboot to see what the result was but I don't think that it would have made a difference. Linux being Linux the same thing is true for Fedora. In order to keep partition  icons from showing on the desktop you need to create a file, populate it with data and after you log out and back in the icons are not there, but if you plug in your thumb drive an icon shows up. That's my goal here. In faireness to the help that I've received is there something that I missed?

Edit: I'll try the gconf-editor method later. Got to take down Christmas decorations now. The boss is calling for help.

---

### Post by CatKiller on 2008-01-05
> **glennzo said:**
> Pointing to a few other threads proves nothing. As I said, I made the changes and things were still the same. I followed the advice given. I will admit that I didn't reboot to see what the result was but I don't think that it would have made a difference.

Did you unmount the already-mounted partitions? If not, then they're still mounted at /media, and so will still show on the desktop. You can unmount the volumes with ```
sudo umount /media/whatever
``` After you've edited /etc/fstab, and created the new mount points, you can use ```
sudo mount -a
``` to mount all of the filesystems that have an entry in /etc/fstab. Or you could just reboot, which would unmount the existing filesystems, and then mount the ones in /etc/fstab on reboot.

Most of this information was in the thread that you didn't want to read.

Good luck with the Christmas decorations.

---

### Post by p_quarles on 2008-01-05
Did you at least restart X after changing the mount points? Rebooting won't do anything, but logging out would. If you did, disregard.

As for gconf, I'd point out that those pluggable devices will still show up in Nautilus browser windows, so the loss in functionality wouldn't be terrible. There most likely is a way to manually configure the file in question:
```
~/.gconf/apps/nautilus/desktop/%gconf.xml
```
so that it displays certain devices while excluding others. If you happen to have access to the Fedora machine that was configured this way, it should be simple to get the necessary tweaks from there. Linux is Linux, but different distros do tend to add features here and there.

Fwiw, KDE has a simple GUI interface for accomplishing exactly what you're looking for. It allows you to configure different kinds of devices to display on the desktop, as well as setting them to display while mounted, unmounted, both, or neither.

---

### Post by glennzo on 2008-01-05
Yes, What I did was
umount /media/xp
mkdir /mnt/xp
gedit /etc/fstab
Changed
/dev/sda3 /media/xp ntfs-3g defaults 0 0
to
/dev/sda3 /mnt/xp ntfs-3g defaults 0 0
I saved the file and then
mount -a
At that point /mnt/xp mounted without error and immediately appeared on the desktop. Appreciate the help and glad that no one thinks that some Fedora user joined in here to raise h e double hockey sticks.

---

### Post by glennzo on 2008-01-05
> **p_quarles said:**
> Did you at least restart X after changing the mount points? Rebooting won't do anything, but logging out would. If you did, disregard.

As for gconf, I'd point out that those pluggable devices will still show up in Nautilus browser windows, so the loss in functionality wouldn't be terrible. There most likely is a way to manually configure the file in question:
```
~/.gconf/apps/nautilus/desktop/%gconf.xml
```
so that it displays certain devices while excluding others. If you happen to have access to the Fedora machine that was configured this way, it should be simple to get the necessary tweaks from there. Linux is Linux, but different distros do tend to add features here and there.

Fwiw, KDE has a simple GUI interface for accomplishing exactly what you're looking for. It allows you to configure different kinds of devices to display on the desktop, as well as setting them to display while mounted, unmounted, both, or neither.
Guilty as charged! I didn't log out and back in after I made the changes. Here's a link to my wiki page about handling this in Fedora 8 if you're interested.
[http://www.johnson.homelinux.net/mywiki/DeviceIcons]("http://www.johnson.homelinux.net/mywiki/DeviceIcons") I'm in Windows right now. I'll reboot to Ubuntu and see what I can do along the lines of everyone's advice here. In other words, I'll give it another shot.

---

### Post by p_quarles on 2008-01-05
> **glennzo said:**
> Guilty as charged! I didn't log out and back in after I made the changes. Here's a link to my wiki page about handling this in Fedora 8 if you're interested.
[http://www.johnson.homelinux.net/mywiki/DeviceIcons]("http://www.johnson.homelinux.net/mywiki/DeviceIcons") I'm in Windows right now. I'll reboot to Ubuntu and see what I can do along the lines of everyone's advice here. In other words, I'll give it another shot.
Interesting. A little looking, and it appears that it should be easy to get the same thing to happen in Ubuntu:
```
sudo cp /usr/share/hal/fdi/policy/10osvendor/debian-storage-policy-ignore-fixed-crypto-drives.fdi /usr/share/hal/fdi/policy/10osvendor/debian-storage-policy-ignore-fixed-drives.fdi
```
Then:
```
gksudo gedit /usr/share/hal/fdi/policy/10osvendor/debian-storage-policy-ignore-fixed-drives.fdi
```
Then, remove the first "match key" line (which specifies encrypted volumes), and you should have the same setup.

---

### Post by CatKiller on 2008-01-05
> **glennzo said:**
> At that point /media/xp mounted without error and immediately appeared on the desktop. 

Now that's very peculiar. If there's no entry for /media/xp in /etc/fstab then I can't see why this would happen. Possibly there's some "user-friendly" shenanigans going on that we don't know about. As far as I can tell, this isn't working the way it should. Perhaps a bug report is in order? See if the reboot helps next time you boot into Ubuntu.

Sorry I couldn't be more help.

---

### Post by glennzo on 2008-01-05
> **CatKiller said:**
> Now that's very peculiar. If there's no entry for /media/xp in /etc/fstab then I can't see why this would happen. Possibly there's some "user-friendly" shenanigans going on that we don't know about. As far as I can tell, this isn't working the way it should. Perhaps a bug report is in order? See if the reboot helps next time you boot into Ubuntu.

Sorry I couldn't be more help.No apologies. We're usually more help than we realize. I appreciate the help and hope that I didn't come off as arrogant, but if it ain't a workin' it ain't a workin'. :)

---

### Post by glennzo on 2008-01-05
> **p_quarles said:**
> Interesting. A little looking, and it appears that it should be easy to get the same thing to happen in Ubuntu:
```
sudo cp /usr/share/hal/fdi/policy/10osvendor/debian-storage-policy-ignore-fixed-crypto-drives.fdi /usr/share/hal/fdi/policy/10osvendor/debian-storage-policy-ignore-fixed-drives.fdi
```
Then:
```
gksudo gedit /usr/share/hal/fdi/policy/10osvendor/debian-storage-policy-ignore-fixed-drives.fdi
```
Then, remove the first "match key" line (which specifies encrypted volumes), and you should have the same setup.Now see. If I had looked I may have found the same thing myself. OK, I booted Ubuntu and used gconf-editor. It did exactly what I said it would. No icons at all, so I set it back. Then I changed the mountpoint again to /mnt/xp, logged out and back in. No dice. Icon still there. Another issue has arisen in Ubuntu, this one with my wireless. It stopped working so I need to tend to that first then tackle the anal desktop icon thing. I'll use the above method and see what we get.

Edit: Wireless is fixed and I made the changes as suggested above and rebooted. The icons are still there.

---

### Post by glennzo on 2008-01-05
> **CatKiller said:**
> Now that's very peculiar. If there's no entry for /media/xp in /etc/fstab then I can't see why this would happen. Possibly there's some "user-friendly" shenanigans going on that we don't know about. As far as I can tell, this isn't working the way it should. Perhaps a bug report is in order? See if the reboot helps next time you boot into Ubuntu.

Sorry I couldn't be more help.Hi CatKiller. That was a typo on my part that I have since fixed. It should have read **/mnt/xp** and not **/media/xp**.

---

