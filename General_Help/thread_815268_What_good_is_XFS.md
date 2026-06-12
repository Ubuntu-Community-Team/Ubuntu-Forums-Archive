---
title: "What good is XFS?"
date: 2008-06-01
forum: General Help
---

### Post by Quantumstate on 2008-06-01
After much research I decided on XFS for a filesystem, as the most technically superior and stable.

But I now find that this journalling seems to be a myth.  Recently after trying a number of (busted/braindead/schlock/dreg) styles on kdelook my KDE started locking up on login.  Power down was the only option, as I couldn't even crash X.

Well now there are files and directories in /tmp which I can not delete as root.  Some have ??? ???? ??? for size, location, etc.  I know the ondisk file structure needs repair, and apparently this is not done at boot, inexplicably.

So I boot to the CD's filesystem, mount /dev/sda1 and copy xfs_repair to the ramdisk, umount sda1, and run xfs_repair on it.  It finds and fixes problems by taking problem sectors and simply putting them in lost&found!

What kind of fix is this?!  This is so basic I would have expected this method 15 years ago.  What happened to the journal?  Why diesn't it actually -FIX- the filesystem, rather than just stupidly setting aside unlinked sectors?


And now that I have the other partition set to NTFS I can't even boot to CD with /dev/sda1 unmounted anymore.  I tell it to use the NTFS part as root so it won't mount sda1 and it flunks, I guess because it doesn't have that module.  And yet when I set the ramdisk filesystem to be root and sda1 to be /target, it won't allow me to umount /target!  How am I supposed to repair it?

Can anyone advise?

---

### Post by Quantumstate on 2008-06-02
Alright, I have lost all confidence in XFS.  In installing ~eight busted styles from kdelook, my KDE locked up twice during testing and I was forced to power down.

And now my system is falling to pieces.  Many functions no longer work (including wifi), and my KDE sessions are no longer being saved or restored.

This is intolerable, after only three power-downs.  WTF happened to journalling?!

I am now looking for a new filesystem, as I must completely start over and reinstall.  I hear ext3 is slow.  I've used Reiser for years, but now that the chief developer is in jail it looks like no more development there.

Any suggestions?

---

### Post by ibuclaw on 2008-06-02
Personally, I don't think that ext3 is at all slow.

And if you think otherwise, there are various ways that you can [speed it up]("http://ubuntuforums.org/showthread.php?t=107856").

There is a reason why it is the default for Ubuntu and most other distributions, you know.

Regards
Iain

---

### Post by bingoUV on 2008-06-02
XFS : It has very bad defaults. You have to evaluate all the create filesytem options, and mount options according to your needs. It has a reputation of being good for large files and fast deletes. But you must have compared benchmarks.

ext3 : I agree with tinivole that it is fast enough for casual use. I tried this speeding up trick, and lost data. I don't even have a very demanding setup, but as I was playing with unstable graphics drivers which locked the system, this was really unsafe. Do it only if you are using all stable kernel modules and have battery backup.

ext4 : I hear very good reports. Seems to be linux's answer to ZFS (without the pool/inbuilt raid etc.). [http://tastic.brillig.org/~jwb/zfs-xfs-ext4.html](http://tastic.brillig.org/~jwb/zfs-xfs-ext4.html) was a good comparison, but seems to be down today. ext4 beat all compared filesystems, including ZFS in some fields. As you are an adventurer, please try it out and let us all know of its current stability.

---

