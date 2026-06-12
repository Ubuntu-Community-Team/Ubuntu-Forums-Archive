---
title: "update-initramfs - boot from cd"
date: 2017-07-16
forum: General Help
---

### Post by jgw on 2017-07-16
I got an error (update-initramfs is disabled since running on read-only media)   I booted from the cd.  I got the error because the cd is read-only media.  As far as I can tell that is the way it is.  What I have to do is to move to the hard drive that has the problem and run the update-initramfs script from that drive.  My problem is that I don't know how to move to the drive and run the program from that drive.

Here is what I tried.  I went to disks, found the original drive, changed the file system name to "main" (to stop dealing with the 20 some number name).  
Then I CD'd to /media/ubuntu/main/usr/sbin.
Then I did: update-initramfs -c -k 4.8.0.36-generic

Then I got: "update-initramfs is disabled since running on read-only media".  Apparently EVERYTHING is read-only.

I then ran the same command but, this time, added "sudo".  It made no difference.  Its obvious that I am doing something wrong.  Because I booted off the cd perhaps I can't get to root?  (have no clue)   Hopefully somebody will be able to help me.

Thank you.................


I am going to surrender on this one and mark it solved.  This happened on a laptop and there is really nothing real important on it so I am just going to re-install and be done with it.

---

