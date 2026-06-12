---
title: "how does &quot;device is now safe to remove&quot; work"
date: 2008-03-01
forum: General Help
---

### Post by Peter76 on 2008-03-01
Hi, I am trying to setup a lightweight system for somebody who is not that computer literate. That person works a lot with a usb stick. What I want to know is how I can get the "device is safe to remove" message, or where that is sent and how I can set that up under another wm/de than gnome. Thanks in advance, Peter

---

### Post by Rocket2DMn on 2008-03-01
Rather than "safely removing" in linux, you unmount the drive in software before unplugging it.  If the drive gets automounted with an icon on the desktop, you can right click and choose "Unmount" or "Eject", after which you can unplug it (unless it gives you an error).
To do it from the terminal, you need to know the device or the mount point, and use the umount command.  I'm going to assume you know what this means, ask if you don't.
```
sudo umount /media/[mountpoint]
//or
sudo umount /dev/[device+number]
```
I have found that using the "-l" (lowercase L) option sometimes helps if the drive is refusing to unmount.

---

### Post by Peter76 on 2008-03-02
@Rocket2DMn, I know all this; the thing is that if you unmount an usb stick which you have just writtento, although it says it is unmounted, sometimes the write isn't finished. Under Gnome when I unmount a stick I sometimes get a message that data still has to be written to it, which changes then in the " it is now safe to remove" message

---

### Post by lemmy999 on 2008-03-02
I tend to use Places>Computer and then right click on the relevant drive (or USB stick), select "unmount volume" and thats it!

---

### Post by Rocket2DMn on 2008-03-02
It should never actually unmount before the data is finished writing, it just won't let you.  Even if it disappears from the desktop, if you check the mount point and there is still data there, then it isn't unmounted.  The Gnome stuff is imperfect I think, maybe a result of miscommunication with HAL and automounter.  Doing it from the terminal is always the safest best, and that's where the "-l" option can be useful.
If you believe otherwise, show me a print screen followed by a visual of the mount point and any output you can get so we can try and troubleshoot.

---

### Post by spupy on 2008-03-02
Use the command "sync" to force the OS the write all buffers to all filesystems - that is, write the changes to the disk (or usb). Then you can unmount the usb safely. From "man sync":
```
 sync - flush file system buffers
DESCRIPTION
       Force changed blocks to disk, update the super block.
```

---

