---
title: "[SOLVED] Odd USB mounting behavior"
date: 2008-03-13
forum: General Help
---

### Post by agaudio on 2008-03-13
I have a setup in which I have an external Lacie 40 GB harddrive plugged into the computer and I use this as the destination for my backups the Simple Backup program available for download in the Ubuntu Repository. However, I have noticed some odd behavior that I was hoping someone could shed some light one.

First of all, I have noticed that when I log in, everything is normal and the USB drive BACKUP shows up as one of my mounts. No problem. But then I log out and my wife logs in. Then there are two BACKUP mounts listed, though both point to the same USB drive. If my wife logs out and I log back in, then either both mounts are still there, or there are no mounts for BACKUP at all (a little random there).

Then this morning I noticed that my USB drive was mounted to BACKUP_ since apparently the folder BACKUP already existed. And of course the daily backup was saved to BACKUP which was nothing more than a folder in the root filesystem under /media/. 

Does anyone understand what is going on here? Is it  necessary to auto unmount a USB drive when logging out? If so, how does one do this? Is there something else happening? Why did the folder BACKUP remain under /media/, causing the USB drive to mount to BACKUP_? Very odd.

Thanks for any help you can provide!

---

### Post by ibuclaw on 2008-03-13
Yeah, I sometimes get that with my one with my CLASSIC SL, both claim to be mounted until you umount and remove it, while the other stays there and still claims to be mounted.

What I ended up doing was removing the ability to show Mounted Volumes on my Desktop (Check out [Ubuntu Tweak]("http://getdeb.net/release.php?id=2279")) and added the Disk Mounter Applet to my bottom bar. And I generally just unmount the filesystem with a "Click/Click" action before I logoff.

[EDIT]
You can also use the Disk Mounter Applet to open Nautilus to them too, by the way. So those desktop icons won't be missed afterall!
[EDIT]

Iain

---

### Post by agaudio on 2008-03-13
Thanks. I tried your suggestion, but nothing happens when I try to add the disk mounter applet. ALl the other applets seem to work though. 

By the way, do you think the whole BACKUP_ vs BACKUP thing is related to this as well.

---

### Post by ibuclaw on 2008-03-13
hmm... Strange. I couldn't honestly say why the applet wouldn't show.

Have you tried logging in/out, rebooting, etc...
Does it happen for both bottom and top?

And no, I doubt it, but I suppose anything is possible. :)

For the time being, unmount the BACKUP drive, leave it unplugged, and reboot your system.
Then try opening up the Disk Mounter Applet, if you still get nothing, something strange is wrong with it. And perhaps reinstalling it is required. (?)
If it does start and appears functional. All is good!
Next, open up your "/media" folder and check that the only folders there are the currently mounted devices on your system. (ie: remove the BACKUP and BACKUP_ folders iif they exist).
Now, plug in your external hard drive and turn it on, let it automount, and nautilus should open a new window into it.

Hope all goes well.

Regards
Iain

---

### Post by agaudio on 2008-03-13
Great. Thanks for the tip. Your suggestions work.Once I unmounted the USB drive, the applet showed up and now it works fine with the USB. 

Do you suppose there is any way to unmount the USB drive in a logout script?

---

### Post by ibuclaw on 2008-03-13
Yes, there is! thankfully enough.

I'm just going off memory here (you WILL have to look it up.)

in your .bash_logout file (located in your home folder, hit Ctrl+H to see all your hidden files).

Enter in something like this:

```

if [ -d /media/BACKUP ]; then
   sudo umount /media/BACKUP
fi

```

Though this can be done more efficiently using the /dev/sdc location, as that is pointing straight to your device. (I'm assuming that it is the only external drive that you use.)
Also not sure how sudo would work... as unmounting requires root privileges and sudo requires a password.

Again, I'm only going off memory here, this is something you can look up.

Iain

---

