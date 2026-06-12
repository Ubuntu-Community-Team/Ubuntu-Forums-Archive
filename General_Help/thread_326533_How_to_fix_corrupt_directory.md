---
title: "How to fix corrupt directory"
date: 2006-12-27
forum: General Help
---

### Post by dcroxton on 2006-12-27
I have a directory at /back that I use to mount a Samba share.  It is not allowing the mount all of a sudden.  When I do ls -l on the root directory, /back shows as:

[INDENT]?---------   ? ?        ?          ?                ? /back[/INDENT]

I tried running fsck /back and got the following output:
[INDENT]
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
fsck.ext2: Is a directory while trying to open /back

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
[/INDENT]

The thing is that the Samba share is not currently mounted.  I don't know what's supposed to be in a directory that's used as a mount point when it isn't mounted, so I don't know what to substitute for <device>.  I tried using /dev/hda1, which is the device for the root directory, but I got a warning that it could cause severe damage.  Perhaps I need to boot up with a live cd and run this command?

BTW, I created a new directory and mounted the Samba share there, and it works fine, so that's not an issue.

Thanks,
Derek

---

### Post by kidders on 2006-12-27
Hi there,

What an odd issue!

> **dcroxton said:**
> I tried running fsck /back and got the following outputThat's the output you would expect when trying to fsck something that isn't a block device, so that's nothing to worry about. :-)

Try **fsck /dev/hda1** perhaps.

> **dcroxton said:**
> I don't know what's supposed to be in a directory that's used as a mount point when it isn't mountedUsually nothing, since it will be difficult to access whatever's there, when there's a filesystem mounted on top of it. Having said that, I sometimes put icons in my mount points, to help make it more obvious when whatever's usually there has _not_ been mounted.

> **dcroxton said:**
> I tried using /dev/hda1, which is the device for the root directory, but I got a warning that it could cause severe damage.Yeah, you really shouldn't fsck something that's in use. Like you suggested, booting off a LiveCD (any Linux CD will do) is the thing to do.

> **dcroxton said:**
> BTW, I created a new directory and mounted the Samba share there, and it works fine, so that's not an issue.

Yep :-) All I would do in your shoes is delete the weird directory and make a new mount point for myself. That said, the reason for the odd-looking corruption happening in the first place would bug me ... and I'd boot from a CD and check the filesystem.

---

### Post by dcroxton on 2006-12-28
Thanks for the response.  I forgot to mention that I did try deleting /back, but I got an error (I'm not at that computer right now, so I can't show what it was).

I will try fsck'ing /dev/hda1 tonight and see if that solves the problem.

Sincerely,
Derek

---

### Post by dcroxton on 2006-12-30
Hmm, fsck turned up no errors on /dev/hda1.  However, I was able to delete the directory while booted from a live cd, and after that, I seem to be having no more problems.  I am, as you say, still a little worried about the cause of the problem -- especially since I just had another partition (on a totally different disk) also go bad -- but I'm not sure what else to do about it.

Sincerely,
Derek

---

### Post by kidders on 2006-12-31
Me neither :-( At times like this, errors are kinda reassuring! Please post back if anything like this happens again.

---

### Post by rivalarrival on 2007-08-20
I'm having the same problem after a reboot.

I've got a share on a win server that I'm able to mount with an fstab entry to /mnt/windows.  Everything works fine, sometimes I can reboot but not often. Fstab entry:

//192.168.1.1/d /mnt/windows smbfs credentials=<file path> 0 0

After a reboot, cd /mnt/windows causes the terminal window to hang for a minute, then give the typical rival@computer: /mnt/windows$ prompt.  "ls" gives "ls:  .: Input/output error"

mount -a hangs for a minute, then "Could not resolve mount point /mnt/windows"
umount says its not mounted according to mtab
Cannot delete the mount point

Mounting to a different point (/mnt/win) by modifying the fstab entry and mount -a works fine. After a reboot,  /mnt/windows is uncorrupted and the /mnt/win is broken as above. I can then rmdir /mnt/windows.

---

