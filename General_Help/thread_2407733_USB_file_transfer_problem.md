---
title: "USB file transfer problem"
date: 2018-12-08
forum: General Help
---

### Post by ra7411 on 2018-12-08
I've got 2 desktop computers, both with up to date Ub 18.04 o/s'.

On one, I have a 1.2g mp4 file that plays fine on it, and when I copy it to a usb drive, it will again play the file that is on the usb drive.

When I take the usb drive and plug it in on the second computer, that same mp4 file  errs out when I try to play it off the usb. When I try to copy it from the usb to this second computer, the copied file errs out also.

I've tried 2 different usb drives - same problems. I've tried 2 different vid players - same problems.

Smplayer err is: mplayer/mpv has finished unexpecedly. Exit code: 2

I've done similar file transfers with these machines when they were Ub 16.04 without any problems.

Any ideas how to fix this?

---

### Post by HermanAB on 2018-12-08
Well, don't yank the thing out before it finished copying.

The 'Safely Remove' feature should prevent that.  You can also run 'sync' from a terminal before umount.

---

### Post by ra7411 on 2018-12-08
> **HermanAB said:**
> Well, don't yank the thing out before it finished copying.

The 'Safely Remove' feature should prevent that.  You can also run 'sync' from a terminal before umount.

Well, I didn't remove it before it was finished copying - that's plain in my original post - the mp4 ran fine from the usb, in the first computer.

---

### Post by HermanAB on 2018-12-09
"1.2g mp4" - What is the file system on the USB drive?

You need FAT32, NTFS or any other Linux file system on the thing to use large files.

If the widget is formatted with FAT16, then the file will be truncated.

---

### Post by The Cog on 2018-12-09
> **ra7411 said:**
> Well, I didn't remove it before it was finished copying - that's plain in my original post - the mp4 ran fine from the usb, in the first computer.
That is not a valid test. If you have just written the file to the USB stick then the contents will be in memory in disk cache, and you will be playing from cache not from the stick itself. You could try removing the stick and reinserting it, then trying to play the file.

---

### Post by ra7411 on 2018-12-09
> **The Cog said:**
> That is not a valid test. If you have just written the file to the USB stick then the contents will be in memory in disk cache, and you will be playing from cache not from the stick itself. You could try removing the stick and reinserting it, then trying to play the file.

That's good to know, but I did a lot of things, including waiting  ample time past when Files said it was done copying (which I always do with large files), pulling the drive out and putting it in a different input slot for copying, playing, etc, various combinations, to see if anything made a difference.

The usb drive is formatted fat 32.

Finally, I couldn't figure anything else to do, so I re-booted both machines then repeated the copy, transfer to other machine, see if it plays, and it worked.

---

### Post by HermanAB on 2018-12-09
BTW, you can easily copy files between machines with SSH or netcat.  Sneakernet is so 20th century...
;)

---

### Post by sudodus on 2018-12-09
I have seen problems to read/write big files via USB (I think mainly in 32-bit linux systems), so you may have a real problem, and it is a good idea to check, that the copy is correct.

You can use md5sum to check if the file was copied correctly.

1. Calculate the md5sum of the original file

```

cd /path-to-original-file  # change directory to where you have the original file
md5sum filename.mp4 > filename.mp4.md5

```

2. Copy to the USB drive

```

rsync --info=progress2 filename.mp4* /path-to-the-mounted-directory-on-usb/  # copy the mp4 file and the md5-sum file
sync  # flush the buffers and wait for it to finish so that the shell returns to prompt

```

3. Unmount the partition(s) on the USB drive

```

sudo umount /path-to-the-mounted-directory-on-usb/

```

4. Unplug the USB drive and plug it into the same computer

I guess it will automount, which is fine.

5. Check the md5sum of the copied file

```

cd /path-to-the-mounted-directory-on-usb/  #change directory to where you have the copied files
md5sum -c filename.mp4.md5

```

6. Unmount the partition(s) on the USB drive

```

cd  # change directory from the USB drive (as suggested here to your home directory)
sudo umount /path-to-the-mounted-directory-on-usb/

```

7.a. If the md5sum of the copy is OK, you can move the USB drive to the other computer and try to play the file.

7.b. Otherwise try to make the copy process succeed, maybe via sftp or rsync and a local area network.

---

### Post by HermanAB on 2018-12-09
Hmm, rsync is a better kind of copy.  It calculates checksums and only completes once the copy is exactly the same as the original.

However, it won't necessarily help with USB widgets, since the disk I/O is buffered/cached, so what it reads back is not necessarily on the the widget - it may still only be in RAM and you can still yank the widget before it is done writing.

The bottom line is that with removable disks, you need to be patient.  Copying data over ethernet with scp or netcat is better for the impatient.

---

