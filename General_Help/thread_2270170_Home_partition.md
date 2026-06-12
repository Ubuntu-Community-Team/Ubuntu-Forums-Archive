---
title: "Home partition"
date: 2015-03-20
forum: General Help
---

### Post by pfeiffep on 2015-03-20
I just installed Ubuntu 14.10 in a separate newly created partition, I used the swap and home partitions from 14.04.2.
I know much of the data in downloads and documents is still present when booting to 14.04. 
I also know that some of the data from /home is accessible since when launching Thunderbird and Firefox both were already configured and the min|max|exit buttons are on the right.
Gnome flashback is installed on both using metacity.

 I'm just curious about the difference with new method since I had done this before with Ubuntu 12 and Mint and all my documents were shared nicely. I'm simply testing 14.10 so it's really no big deal.

---

### Post by deadflowr on 2015-03-21
New method?

---

### Post by pfeiffep on 2015-03-21
I actually didn't know how to exactly describe the observed behavoir (method) succinctly
Previously observed behavoir
Install new OS / on a new partition, identify existing /home and /swap to be reused. This resulted on all my settings, documents, downloads to be available in new OS

Recently observed behavoir:
Install new OS / on a new partition, identify existing /home and /swap to be reused. This resulted on all my settings to be available in new OS, but no documents or downloads were present.

---

### Post by Bucky Ball on 2015-03-21
Is /home still mounting at boot? Do a quick check as who knows? Might be that simple:

```
sudo blkid
```

Have a look for the /home partition. Check the UUID number, then open another terminal window and:

```
nano /etc/fstab
```

Is the UUID for /home you found previously there and mounting where it should be?

I'm presuming when you installed you chose 'Something Else' and marked the /home partition to use, but not to format? Might seem obvious, but doesn't hurt to check. ;)

---

### Post by kjohri on 2015-03-25
It is difficult to say but one possibility is that you might have checked the format option for the home partition this time. Since the Documents and Downloads are directories under /home, these would have got erased. Regarding settings, maybe, your settings are the same as the global or default settings, so they seem to have been preserved. The trick is to have separate partitions for root and home and not to format the home partition while installing a new version.

---

### Post by pfeiffep on 2015-03-25
Will the UUID for /home be identical on both Ubuntu installs?

This is more a learning exercise for me since I'm only playing / testing 14.10!

---

### Post by pfeiffep on 2015-03-25
> **kjohri said:**
> It is difficult to say but one possibility is that you might have checked the format option for the home partition this time. Since the Documents and Downloads are directories under /home, these would have got erased. Regarding settings, maybe, your settings are the same as the global or default settings, so they seem to have been preserved. The trick is to have separate partitions for root and home and not to format the home partition while installing a new version.Thanks for your reply. I'm asking the question because I know the trick and have used it multiple times in the past - this time the file content is missing only from the 14.10 install - all the files are still present in my normally used 14.04 install.

---

### Post by decrepit on 2015-03-26
I did something similar, but forgot on the old version I called myself michael on the new version I use mike, so although home was on the same partition in both systems, there was two home folders in it, mike and michael. So the data in one wasn't viewable in the other, unless you browsed to the other home folder.
So have you used exactly the same name?

---

### Post by pfeiffep on 2015-03-28
> **decrepit said:**
> I did something similar, but forgot on the old version I called myself michael on the new version I use mike, so although home was on the same partition in both systems, there was two home folders in it, mike and michael. So the data in one wasn't viewable in the other, unless you browsed to the other home folder.
So have you used exactly the same name?You nailed it - I let the installer choose my userid based on my name - oh well nothing lost really!

---

