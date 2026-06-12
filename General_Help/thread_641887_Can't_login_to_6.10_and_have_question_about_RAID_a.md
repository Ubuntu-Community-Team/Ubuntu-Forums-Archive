---
title: "Can't login to 6.10 and have question about RAID array"
date: 2007-12-16
forum: General Help
---

### Post by tuproxy on 2007-12-16
I am thinking that my 6.10 install has gone bad after doing some HD swapping.  I had a 5 dist RAID 0 array setup with MDADM (I believe, it was a long time ago).  

If I need to re-install the OS, will I lose all the data on the RAID array since it was created with the OS?  

What should I do?  I would like to re-install and recreate the array.  Is there a way to save it?

The system hangs after logging in.  I have the drives mapped to my XP machine and can transfer the data. It seems strange that I have
access via the network but can't get to the GUI or CL.  

What are your thoughts?

---

### Post by obl1v1ous on 2007-12-16
Not to sure about your log in troubles, but as far as your raid array is concerned.  Are you sure that you have a 5 disk raid 0?  ( a raid 0 is where the stripe set is written across all 5 drives, no redundancy or parity as in a raid 1 mirror or raid 5, in simple terms if you loose 1 or more drives in a raid 0 the data is unrecoverable). As for the being able to see the drive over the network , that is strange, hand you SSH, or remote to the box, is it pingable?

and also on that note, if you can get to the drive over the network why cant you just copy off the data, then you can  blow your array away and recreate and reload, then restore from backup later.

---

### Post by tuproxy on 2007-12-16
> **obl1v1ous said:**
> Not to sure about your log in troubles, but as far as your raid array is concerned.  Are you sure that you have a 5 disk raid 0?  ( a raid 0 is where the stripe set is written across all 5 drives, no redundancy or parity as in a raid 1 mirror or raid 5, in simple terms if you loose 1 or more drives in a raid 0 the data is unrecoverable). As for the being able to see the drive over the network , that is strange, hand you SSH, or remote to the box, is it pingable?

and also on that note, if you can get to the drive over the network why cant you just copy off the data, then you can  blow your array away and recreate and reload, then restore from backup later.

It is pingable
It is a RAID0 array (the data wasn't that important, more of a backup of other drives that are still in working order)
I have no way to SSH into the box, as I am running XP and there is no SSH client
I am copying the over since I have the mapped and it working correctly.

Is there a way to diagnose the problem?  I made a backup of my system in a TAR file.  I now just need to figure out how to extract it and get my system back up and running

*** note, I just installed PUTTY and got it to work for the first time ever!  It is a great tool! :)

---

