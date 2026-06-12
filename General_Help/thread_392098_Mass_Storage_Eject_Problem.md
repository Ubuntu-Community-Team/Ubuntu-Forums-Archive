---
title: "Mass Storage Eject Problem"
date: 2007-03-24
forum: General Help
---

### Post by MonkeyBoy on 2007-03-24
I have a usb mass storage device which mounts just fine but when I go to eject, it fails.  This happens when I try to eject with windows too but with windows it writes to the device as I move files over but with ubuntu it waits 'til I eject to write the files and fails.

Is there a method of getting ubuntu to write to the device as I move files over rather than when I try to eject?

Any help would be very welcome.

---

### Post by jakev383 on 2007-03-24
Might not be much of a help, but look at the sync/nosync options. I dimly remember something about this with mount points and NFS....

---

### Post by 3rdalbum on 2007-03-24
Just so you know, Linux starts copying files across when you drag them over. But you're correct, there is a difference between the ways Linux and Ubuntu copy files.

Windows reads an amount of data from the source disk and puts it on the destination, then repeats. When all the data has landed on the destination, the copying operation "returns" and the progress window disappears.

Linux reads as much data as possible from the source disk into a memory buffer, and also starts putting the contents of the memory buffer onto the destination disk. When the last piece of data has arrived in the memory buffer, the copying operation "returns" and the progress window disappears, but Linux is still writing data to the destination in the background.

So if you drag a gigabyte of MP3s onto an MP3 player then immediately try to eject it, it won't work as Linux is still copying in the background.

You can mount a flash drive as "sync", so copying works the same as in Windows, but this will actually be slower than the default behaviour. My advice is that when the copying operation returns, do something else for a little while. Or eject the disk and do something else while Linux finishes the copying.

---

### Post by evilc on 2007-04-21
Try this worked for me now get unmount drive, in terminal: 
sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak

---

