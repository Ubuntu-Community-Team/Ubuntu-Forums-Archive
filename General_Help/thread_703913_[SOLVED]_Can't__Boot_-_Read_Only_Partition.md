---
title: "[SOLVED] Can't  Boot - Read Only Partition"
date: 2008-02-21
forum: General Help
---

### Post by DocHoliday52090 on 2008-02-21
I dual boot Windows and 7.10, and have had the two play well with each other for quite some time. Recently, however, I got an fsck check that claimed the ubuntu partition was locked in read-only, and that I needed to manually run fsck as root. I did so, and allowed fsck to clean the errors as they were recommended. This had happened to me before, but doing this fixed everything. 

However, this time it didn't - I restarted and X won't start. I looked through the text that results and I think it's the same thing - the partition is still in read only. 

The only thing I think is related is the fact that I use an ext2/3 extension driver in Windows so it can mount and use the Linux partition natively and seamlessly. I shut down Windows rather hastily by using the power button (it's a heavily stripped version, meaning it boots and shuts down within seconds) for lack of care. Perhaps these extension drivers did something to Ubuntu?

I want my Ubuntu back - I feel oddly confined in Windows...

---

### Post by DocHoliday52090 on 2008-02-21
Fixed. 

Actually all that was needed was for me to boot back into Windows and shutdown properly. The extension driver in Windows for ext2/3 that I use mounts the partition and sets it to read-only during shutdown for unknown reasons, and then lets it go right before shutdown. By improperly shutting Windows down, I did not get this last step, keeping Ubuntu's partition in read-only.

---

