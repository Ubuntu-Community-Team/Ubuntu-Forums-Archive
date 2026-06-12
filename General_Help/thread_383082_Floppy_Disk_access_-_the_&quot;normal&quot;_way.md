---
title: "Floppy Disk access - the &quot;normal&quot; way?"
date: 2007-03-12
forum: General Help
---

### Post by redadept on 2007-03-12
Hello --

By way of a little background, I work in a small public library, and we are considering putting out an older computer running Ubuntu as a "public use" workstation.  We will provide Internet access, an office suite, and a graphics / scanner combination for user images.  So far we have installed Ubuntu 6 without a hitch, along with Firefox, OpenOffice, Xsane and GIMP.  The "deal breaker" however, is the way that Linux provides access to a user's floppy disk.  Perhaps I can be clearer by a simple comparison:

What We Want:
User inserts floppy disk, clicks on desktop icon, gets a file manager window with disk contents.  User runs OpenOffice, and from there can save to and load from the floppy disk, visable immediately from the "Save / Load" menu.  Upon finishing, user closes OO, ejects his disk, and walks away with zero possibility of data loss. In other words, exactly like things have happened in Windows ever since the days of Win95.

What We Get:
1) user must mount the floppy disk before an icon appears on the desktop
2) user must "hunt" through the "Save / Load" file manager box in OO in order to find the floppy that they just mounted
3) user must carefully "unmount" the disk before ejecting in order to prevent data loss.

I say "deal breaker", because we cannot train each and every walk-in off the street on how to do things "right" in Linux. Unless I can guarantee a simpler and foolproof way of saving/loading guest floppy files, my library management will not approve an Ubuntu Public PC, no matter what the cost savings or security benefits.

Sooo.... does anyone know if a script or kernel hack is available that will provide floppy access in a manner identical to WinXP?  Thanks in advance.

-- Darrell

---

### Post by kokiri on 2007-03-12
I'll just add a bit of a disclaimer here..... I don't have a floppy drive to test this on. That being said, I've used these howto's with other problems before with great success. Ok.. continuing with the info.

Here's the link to the autofs how to:
[http://gentoo-wiki.com/HOWTO_Auto_mount_filesystems_(AUTOFS)]("http://gentoo-wiki.com/HOWTO_Auto_mount_filesystems_(AUTOFS)")

You'll need to:
```
sudo apt-get install autofs
```
for it to work, then you should be able to hack the config file to get the floppy to automount for you
There's a timeout option for the automounter to unmount the media as a good failsafe, you could experiment with values there.

It's an idea to try, as far as the hunting in OO, I'm not super versed in OO's config setups, but I'm sure there would be a way to restrict the scope of the file manager, just don't know how myself.

Hope this was somewhat helpful.

---

### Post by mbeierl on 2007-03-13
You should also add the sync mount options to the mount point for in /etc/fstab.  From the man pages:

sync:   All I/O to the file system should be done synchronously.
dirsync: All directory updates within the file system should be done synchronously.  This affects the following system calls: creat, link, unlink, symlink, mkdir, rmdir, mknod and rename.

So, something like:

```

/dev/fd0   /home/user/a_drive   vfat  user,sync,dirsync   0 0

```
ought to help with the delayed writes...

---

### Post by mbeierl on 2007-03-13
Oh, and you can also create a symbolic link from the Desktop directory to /media/floppy instead of mounting it under /home/user/a_drive...

That way there will be an icon on the Desktop!

---

### Post by redadept on 2007-03-14
Thanks to all for the information -- I'll explore the options with AUTOFS and see if I can get the floppy to automount properly.

Cheers,
-- Darrell

---

