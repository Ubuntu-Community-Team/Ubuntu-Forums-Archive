---
title: "I was using dd to restore a partition and..."
date: 2007-04-10
forum: General Help
---

### Post by billdotson on 2007-04-10
I have a partition /dev/sda1 that is 100GB and an external partition I use for backup that is 113GB (I made it bigger just in case).  I ran the command 

```
 
sudo dd if=/dev/sdb5 of=/dev/sda1 bs=8192 conv=notrunc,noerror

```

and this was the result that was shown at the end

```

dd: writing `/dev/sda1': No space left on device
13184341+0 records in
13184340+0 records out
108006119424 bytes (108 GB) copied, 3593.64 seconds, 30.1 MB/s

``` 

Does that mean that it copied successfully but could not copy the extra 13GB that didn't have any data on it?  Or since the partition sizes weren't exactly the same it did not restore the partition correctly?

Thanks alot.

---

### Post by billdotson on 2007-04-10
all I am asking is that since it said it did not have enough space did it copy all it could (the 100GB that would go on the windows partition) and then couldn't finish the 13G that couldn't fit on the Windows partition.. as that 13GB was not part of the Windows partition to begin with?  The 13GB can only be empty blocks from the partition on the external drive.. that is unless some files got moved there when it copied which it shouldn't have.  

I am in Windows right now so obviously it booted and it seems to be working fine as of now.

---

