---
title: "how to see drives?"
date: 2019-06-07
forum: General Help
---

### Post by josephfg on 2019-06-07
I am running ubuntu studio on an HP laptop.  I'm using the xfce option.  I transferred some files to a USB drive, and then I clicked the little arrow icon in order to safely remove the drive.  So far so good, the drive unmounts, and I can safely remove it.

I tried, however, before removing it, to remount it and check it for the files, and I could not for the life of me figure out how to do that.  When I first plug the USB in, an icon appears on the desktop for the unmounted drive, I can mount it and see it.  When I click the unmount icon, it unmounts and the desktop icon disappears.  The drive is still physically connected to the computer, but how can I see it again?

I used to be a Windows user, and Windows has a "My Computer" icon you can place on the desktop, which shows you all the drives.  I can't find anything like that in Ubuntu.  Is there something like that, and if so, where is it?

Also, a general question about USB drives: what happens if you just yank it out without unmounting it?  Is there a risk of data corruption?  That seems to be the logic of unmounting, or "safely remove drive," but I want to know for sure, if anybody knows.

---

### Post by TheFu on 2019-06-07
Never yank any storage device from any Unix computer without unmounting (umount is the command) first.  There is no guarantee that all the data for any file has been written to the storage.  Unix uses buffers for all storage and network access.  Yes, data corruption is possible, even likely.

The other question is extremely specific to the file manager program being used.  I don't know which xfce or ubuntu studio uses by default. Sorry.  I know Ubuntu-Mate uses caja and I think LXDE uses Thunar.

I think all GVFS/GIO mounts are triggered by the udev subsystem.  That is the physical insertion of the device, in this case, into a USB port.  You should know that GVFS is known for extremely poor performance.  They've been working on it, but until they just use the **mount** command, which is what **fstab** and **autofs** use, it will have bad performance and no real way for us to provide any mount options to improve.

If you use mount (which will read the fstab file) or autofs, then the umount command is mandatory.
I use autofs for all portable storage access, but it requires manual configuration, in advance, for each different partition to be mounted.  Once configured, you just plug in the specific storage device and access it.  It will be dynamically mounted, with the mount options you specified earlier, until it isn't "in-use" any longer. Then autofs will automatically umount the storage. The automatic umount takes between a minute and 5 minutes.  I don't actually know how long.  I use this daily for external USB storage.

The way to see mounted storage on any Unix system is with the **df** command.  Unfortunately, gvfs storage doesn't show up, which is why I don't consider it a *real mount*.  Real mounts show up in the mtab and are shown by the df command.  Period.

The file system used matters too, BTW. Different file systems support different mount options, and have very different performance, beyond just what the device can handle.

Some more reading.
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)
[https://wiki.gnome.org/Projects/gvfs](https://wiki.gnome.org/Projects/gvfs)

---

### Post by ajgreeny on 2019-06-07
If you click on the small arrow next to a USB drive in thunar, the xfce4 file manager it ejects the USB, one step further than simply unmounting it. This removes it from the system completely; it's as if it were no longer plugged in so it can be most simply remounted by unplugging and replugging it.

Rather than clicking that arrow you can right click on the disk and choose Unmount if you prefer, in which case the disk is not ejected, the icon will remain in the left hand thunar pane and it can be clicked again to mount the disk once more.

---

### Post by The Cog on 2019-06-07
Just to add to ajgreeny's explanation: Ejecting a drive (rather than just umounting it)  also removes power from it. Then, you have to physically unplug and replug the drive to get it seen as a new insertion and get it powered on again.

---

### Post by Dennis N on 2019-06-07
> Also, a general question about USB drives: what happens if you just yank it out without unmounting it? Is there a risk of data corruption? That seems to be the logic of unmounting, or "safely remove drive," but I want to know for sure, if anybody knows. 

Yanking it out before it's unmounted is a bad idea, as stated in the posts above. But, if you should leave a USB inserted while powering off your computer, systemd unmounts all mounted file systems before shutting down. That includes any USB drive you left plugged in and mounted.  

Evidence of this can be found in the systemd journal: A USB is left mounted, and computer shut down. Later checking the journal shows it was unmounted before shutdown.

```
Jun 07 13:28:04 Tyana-vm systemd[1]: Unmounting /media/dmn/MyData...
Jun 07 13:28:04 Tyana-vm systemd[1]: Unmounted /media/dmn/MyData

```
After shutdown with USB inserted, you have to physically remove and reinsert it to mount again.

---

### Post by josephfg on 2019-06-08
Thank you everyone for your help, which is most helpful!

---

