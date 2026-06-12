---
title: "Hardy USB eject"
date: 2008-06-02
forum: General Help
---

### Post by anv on 2008-06-02
Hi before there were logic mount umount system in xubuntu, while right mouse clicking over the precise partition on usb drive icon there were option to unmount, mount and open the partition, now it automounts those all partitions on the disk, and opens them double so I have 3 partitions and it opens automatically 6 windows in thunar. and only option to turn off the media is choose eject from the menu, and while doing this to one partition it shuts down them all, and starts them again with 6 windows. so it leads to  only disk shut down option as shutting down the disk from the power button and that I know is not the best option.

I want to set the system in same way as it followed earlier the mounting unmounting, how this is achieved.

---

### Post by anv on 2008-06-03
...bump...

I really need to get this repaired...


1.) how to set the automount option off... 

2.) how to gain the previous system back I really hate this new one it breaks the usb disk after couple of weeks.

---

### Post by anv on 2008-06-03
answering to my own post...


1.)founded an area in xfce-manager for portable media, removed tick away from the auto-mount and auto-browse.

2.)added device plugin for xfce to panel where it is possible to mount or unmount devices

(...in case if it bugs someone else.)

---

### Post by trash on 2008-08-01
I just started using the 'mount devices' aplet available in the panel... I like my devices mounting when plugged so your fix doesn't work for me.

Is it a bug that my usbdrive desktop icon would have eject as an option instead of unmount?

---

### Post by jimmy the saint on 2008-08-02
If you disable Thunar's volume management it will eliminate a lot of these double mount issues.  It aslo eliminates the problem that sometimes volumes get remounted after being unmounted.  Everything is still automounted just fine.

---

### Post by trash on 2008-08-02
> **jimmy the saint said:**
> If you disable Thunar's volume management it will eliminate a lot of these double mount issues.  It aslo eliminates the problem that sometimes volumes get remounted after being unmounted.  Everything is still automounted just fine.

nope didn't make any difference and on top of that i disabled all of the options in removable drives and media... if i use the desktop icon to 'eject' the external hd it unmounts and then mounts itself again.
There was an achived thread about this issue that people were trying to figure out a script for but it got archived before anybody found a solution and i found no other info about it besides this thread.

---

### Post by randcoop on 2008-08-05
Adding the mount/umount to the panel worked for me.  I did not disable thunar-volume management.  Now, when I plug in the USB key, it mounts automatically, opens a thunar window to show me what's there (my preference...this can obviously be set not to happen), and leaves an icon on the desktop.  When I want to unmount, I click on the mount icon in the panel, click once on the drive to be unmounted, and it's done. The icon for the drive remains on the desktop until I remove the drive.  If I want to mount it again, I simply click on the desktop icon and it mounts.

---

### Post by tw1ggy.ramir3z on 2008-08-06
> **randcoop said:**
> Adding the mount/umount to the panel worked for me.  I did not disable thunar-volume management.  Now, when I plug in the USB key, it mounts automatically, opens a thunar window to show me what's there (my preference...this can obviously be set not to happen), and leaves an icon on the desktop.  When I want to unmount, I click on the mount icon in the panel, click once on the drive to be unmounted, and it's done. The icon for the drive remains on the desktop until I remove the drive.  If I want to mount it again, I simply click on the desktop icon and it mounts.

It didn't work for me. I've just added the mount/umount icon on the panel but I continue to get two windows when I plug a usb drive.

---

### Post by randcoop on 2008-08-06
One other thing that may have an impact: my USB plug in drives are not in my fstab or mtab and I don't have a directory for it in /media.  That's the part that Thunar volume management handles.  If you have it's possible that you do have something in mtab or fstab and so you're automatically mounting AND using Thunar volume management.

---

