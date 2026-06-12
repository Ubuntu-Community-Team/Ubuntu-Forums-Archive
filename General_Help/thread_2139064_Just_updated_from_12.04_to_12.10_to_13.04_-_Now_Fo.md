---
title: "Just updated from 12.04 to 12.10 to 13.04 - Now Folders in /media are moved"
date: 2013-04-25
forum: General Help
---

### Post by bmcgonag on 2013-04-25
I was using Plex media server on Ubuntu 12.04 and had my movies and shows on a USB drive.  Had Plex media server pointed to /media/USBDrive/Shows and all was great.

Upgraded yesterday and today first to 12.10, then to 13.04. 

Now those folders / USB drives still show in the same place, but no files show under the Shows folder.  Instead they are now in /media/<user>/USBDrive/Shows.

In Plex, tried to update the folder, but it only get's to /media/<user> and then shows nothing under that.

How do I get back to where it's just /media/USBDrive/Shows so I can see all of my files?  What happened?

Tried to move the files from one folder to another (really from the same spot to the same spot I imagine), but there's not enough room on the drive for the 'copy' is what it said, even though I was doing a move.

Anyway, just baffled at this point at what to do. 

I'm comfortable with the command line or UI..Either way, I greatly appreciate any help with this.

---

### Post by carl4926 on 2013-04-25
I think IIRC this [COLOR=#333333]is modern behavior of systemd + udisks2[/COLOR]

---

### Post by bmcgonag on 2013-04-26
I've tried removing udisks2, can't do that apparently.  I added user plex to my group, I've made the folders shared, but can't get to the folders through the Plex Media Server web interface. 

I just don't know what to do here...this is kind of a sucky update if it's going to screw with the file system like this.

still looking for help.

---

### Post by carl4926 on 2013-04-26
I'm not aware that this behaviour can be changed it's hard coded in to the system now

---

### Post by dcstar on 2013-04-26
> **bmcgonag said:**
> I was using Plex media server on Ubuntu 12.04 and had my movies and shows on a USB drive.  Had Plex media server pointed to /media/USBDrive/Shows and all was great.
...........

/media is a System Folder for exclusive use by the System to mount and unmount removable devices. It should **not** be used for anything that requires a fixed mount point.

If you want fixed locations, create a mount point in /mnt and edit your /etc/fstab files to use it.

---

