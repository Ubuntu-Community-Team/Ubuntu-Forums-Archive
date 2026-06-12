---
title: "Truecrypt Problem"
date: 2007-05-07
forum: General Help
---

### Post by bobbob1016 on 2007-05-07
I made a few hidden volumes in Truecrypt, and I don't know how to delete them.  According to what I've looked up, I'd have to format the drive.  What I've found is that it looks like random data on the drive, is there any way I could either delete the hidden files, or format the empty space only?  I have my home directory on a different partition, so I could reformat the whole thing, but I don't have a partition I can move all my files to, to backup my home directory to, and I don't want to risk my data, unless I'm certain it's not too risky.  The other problem is that there are some hidden volumes on my second drive too, which is too big to backup locally.  I have a network drive to backup too, but 100gig doesn't go over my 100mbps network that fast.  Can anyone suggest anything?

I would post on the truecrypt.org forums, and still plan to, but their forums are down.

---

### Post by scooper on 2007-05-08
To be honest, I can't really understand the precise issues you have.  Are these truecrypt volumes a drive partition or a file?

If they're partitions that you want to delete you need to do nothing.  Truecrypt doesn't create hidden files, it simply reads and writes the disk directly.  The data is not readable without truecrypt and your passphrase.  All you have to do is unmount it from truecrypt and follow normal procedures to set the partition up for other uses.  If it's not loaded by truecrypt it should be fully accessible to other disk management tools.  I think the command "truecrypt -d ..." handles unmounting.

Why do you need to move your home directory if it's not on a truecrypt volume?  I thought your goal is simply to delete the truecrypt volumes?

Sorry if I missed the point, but perhaps I could be more helpful if you can simplify/clarify the problem.

Cheers,
Steve

---

### Post by bobbob1016 on 2007-05-08
The files are hidden.  Truecrypt hides them in random data, so that only truecrypt can read them.  There aren't any files there, just the hidden files among the random data.  [http://www.truecrypt.org/hiddenvolume.php](http://www.truecrypt.org/hiddenvolume.php)  What I need to do is remove the hidden files, and the way I've found through google-ing is to format the drive.

---

