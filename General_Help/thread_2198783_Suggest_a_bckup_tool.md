---
title: "Suggest a bckup tool"
date: 2014-01-10
forum: General Help
---

### Post by linuxyogi on 2014-01-10
Hi,

I am using Xubuntu 12.04. I need to back up a particular folder in my Home to a usb drive incrementally. The folder has many files and sub folders in it.

I tried 

**Grsync **is giving me some errors

 **Deja Dup's** style of backup is not what I want want. I don't want to create an archive of  the files. I just want the backup utility to copy the new files and folders  to the target ignoring the existing ones.

**Ukopp **too failed with some errors.

I searched for pybackup but didnt find it in the repos.

What do you recommend ?

---

### Post by ajgreeny on 2014-01-10
What sort of errors are you seeing using grsync?

I use that always for my backups to an external hard drive, but in my case that external is formatted to an ext4 filesystem.  If I used a fat32 or ntfs filesystem I did get a few errors related to permissions, but generally, if those are what you are seeing, you can largely ignore them.  You may also get errors if you have the same named files using a different case (upper vs lower) for the name, as in Linux they are seen as different files, in Windows filesystems they will be the same file, hence some error messages.

---

### Post by linuxyogi on 2014-01-10
I am getting this error 

```
rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: write failed on "/media/Linux Mint 15 Cinnamon 64-bit/new best /sangam(with audio).avi": No space left on device (28)
rsync error: error in file IO (code 11) at receiver.c(322) [receiver=3.0.9]
   174653440  29%    4.27MB/s    0:01:34  rsync: connection unexpectedly closed (450 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(605) [sender=3.0.9]
Rsync process exit status: 12
```

The usb drive's capacity is 7.5 GB

The source folder presently holds 5.1GB of data but strangely after running grsync I found that the data size o the usb drice has increased and now its 6.6 GB.

Also Grsync is kind of checking every file and moving to the next. This is taking a lot of unnecessary time. What I want rsync to do is check if there are any new files or folders in the source and copy them to the backup destination.

---

### Post by Buntu Bunny on 2014-01-11
> **linuxyogi said:**
> 
I searched for pybackup but didnt find it in the repos.

Did you mean pybackpack? It's in Synaptic.

---

### Post by vanadium on 2014-01-11
> **linuxyogi said:**
> Also Grsync is kind of checking every file and moving to the next. This is taking a lot of unnecessary time. What I want rsync to do is check if there are any new files or folders in the source and copy them to the backup destination.
That is exactly what rsync does with the -a ("archive") option. However, this option will only work correctly when the destination is also a drive that supports linux permissions: indeed the "-a" option attempts to make an exact "mirror" copy of the source files. This involves that also ownership and permissions are copied. To make incremental mirror copies on drives that do not support linux permissions, other options would need to be used. 

Error messages suggest 1) that the destination drive is full 2) that there might be errors in the connection/transmission ...

First of all check that 1) the file system of the USB system is "healthy", 2) there is space left on the USB device.

---

