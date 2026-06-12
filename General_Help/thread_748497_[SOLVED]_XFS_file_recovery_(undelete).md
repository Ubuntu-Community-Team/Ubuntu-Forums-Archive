---
title: "[SOLVED] XFS file recovery (undelete)?"
date: 2008-04-07
forum: General Help
---

### Post by njparton on 2008-04-07
I've just done a very stupid thing and deleted a load of files on my ubuntu NAS server on a partition that was formatted with the XFS filesystem.

Does anyone know of a command line tool that I can use to recover them?

They were deleted from windows, the partition is shared over my home network via samba (and hence no delete confirmation dialogue box).

Please help me!!

---

### Post by cdenley on 2008-04-07
You can recover some deleted files from an xfs filesystem with photorec. It won't recover the file names or paths, though, and will only recognize certain types of files.

```

sudo apt-get install testdisk
sudo photorec /path/to/disk

```

---

### Post by njparton on 2008-04-07
Thanks for that.  It appears that program will only let me recover files to a different physical disk, not in-situ.  The files I deleted are far too big for me to recover to the OS disk which is only 40GB (- the space already used).

Does anyone know of anything that will work in-situ?

---

### Post by bodhi.zazen on 2008-04-07
[http://linuxwebdev.blogspot.com/2005/06/xfs-undelete-howto-how-to-undelete.html](http://linuxwebdev.blogspot.com/2005/06/xfs-undelete-howto-how-to-undelete.html)

---

### Post by njparton on 2008-04-08
Thanks for your reply, that looks very interesting.  However, the files I want to recover are mainly videos so I can't search for text in them as that link suggests.
 
I'm at work at the moment so I'll give this another read when I get home tonight to see if I've got it wrong (?) or if it can be adapted.

---

### Post by njparton on 2008-04-11
For anyone else coming across this thread I've not been able to solve this (and hence my data is lost). 
 
However, I've found some links that show you how to set up a recycle bin for samba so in the future I should at least be able to retrieve my files from there.
 
Check out:
 
[http://ubuntuforums.org/showthread.php?t=748519](http://ubuntuforums.org/showthread.php?t=748519)

---

### Post by Littleweseth on 2008-04-11
The tool you want is 'foremost'. It recovers files based on distinctive characteristics of file type headers and so forth, so you get your files back, but with no names etc. (I believe foremost is like photorec, but for a wider range of files.)

Of course, the usual caveats apply - foremost does not work 'in situ', so you need another big hard disk to dump everything to.

-lws

---

