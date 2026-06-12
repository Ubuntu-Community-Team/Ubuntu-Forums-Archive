---
title: "Is it possible to mount /home somewhere else without re-installing?"
date: 2006-12-13
forum: General Help
---

### Post by jclmusic on 2006-12-13
i got a new hard drive that i'd like to use as my /home partition, so i can have more space, and free up the older hard drive to dual boot a number of different linux distros :) 

how could i move where /home is mounted?

---

### Post by taurus on 2006-12-13
Mount your new harddrive somewhere like /mnt/temp and copy /home to that.  Then, edit your /etc/fstab to include an entry for that new harddrive except have it mount to /home.  Reboot and see what happens...

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
(Look at the part about [COLOR="Red"]**Using the new partition**[/COLOR]...)

---

### Post by musicinmybrain on 2006-12-13
This should work:

1. Create a partition and filesystem on the new drive.
2. Mount the new partition and copy all files (including hidden files) from /home to the new partition. (Use Ctrl+H to show hidden files in Nautilus).
3. "gksudo gedit /etc/fstab"
4. Look for "UUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX /home"
5. Open another terminal and type "sudo blkid"
6. Find your new partition in the output and replace the old UUID with the UUID returned by blkid for your new /home partition. Go ahead and edit the comment above it, too, just for consistency.
7. Now reboot and Ubuntu should use the new partition as your /home.

Edit: beaten to an answer. that looks good too :-P

---

### Post by jclmusic on 2006-12-13
thank u so much!!

---

