---
title: "Question about comparing file sizes"
date: 2006-12-15
forum: General Help
---

### Post by M-Theory on 2006-12-15
Hey everyone,

I've copied a lot of files (mainly large ones) from one hard drive to another, but during the process my computer freezed a couple of times and therefore I had to reboot. It is likely that some of the files I copied aren't complete. 
My question is if there's a script or program that can compare the data on the two harddrives and tell me whether the file sizes are the same. I hope someone can help.

Thanks.

---

### Post by yabbadabbadont on 2006-12-15
Are the files all in the same directory?  (i.e. they came from one directory on the source drive and you copied them to one directory on the new drive)

---

### Post by M-Theory on 2006-12-15
I just copied the contents of the partition on the one drive to a partition on the other drive, so the directory structure is identical.

But they aren't all in one directory.

---

### Post by yabbadabbadont on 2006-12-15
Hmmm.  If you want an exact copy of the whole filesystem from one partition to another, then you will probably want to read up on rsync.  It was made for situations like that.  (even if the source and destinations are on different machines)

I keep a backup of my home directory up to date using:

sudo rsync -av /home/bubba /media/backup

It preserves all permissions, owners, and groups, and only copies the files/directories that are different between the source (/home/bubba) and the destination (/media/backup/bubba).  There are a lot of options you can use, so spend some time reading up on it.  (man pages, etc)

---

### Post by M-Theory on 2006-12-15
I used CP to copy the files. the option -a also preserves everything like file permissions and structure and such. The -u option also only updates files that aren't already on the destination drive, however, I don't think it looks at file sizes, only file names and dates.

I don't need to copy the whole partition again, I just want to find the few files (I think max 6) that don't have the same file size as their original and thus haven't been copied in whole.

---

### Post by pandu.rs on 2006-12-15
u can quickly generate a md5 sum of all the files under a directory using

In cp's src dir
find -type f | xargs md5sum | sort > /tmp/file1.txt

In cp's dst dir
find -type f | xargs md5sum | sort > /tmp/file2.txt

then u can see the diff between them using comm
comm -1 -3 file1.txt file2.txt

That shld give u the files having different md5sum in dst directory and hence not copied properly.

---

### Post by yabbadabbadont on 2006-12-15
> **M-Theory said:**
> I used CP to copy the files. the option -a also preserves everything like file permissions and structure and such. The -u option also only updates files that aren't already on the destination drive, however, I don't think it looks at file sizes, only file names and dates.

I don't need to copy the whole partition again, I just want to find the few files (I think max 6) that don't have the same file size as their original and thus haven't been copied in whole.

rsync will do that.  It will only copy the files from the source that are either missing from, or different on, the destination.  It is used to mirror software repositories all over the world.  It also happens to work well for mirroring from one directory tree to another.

---

