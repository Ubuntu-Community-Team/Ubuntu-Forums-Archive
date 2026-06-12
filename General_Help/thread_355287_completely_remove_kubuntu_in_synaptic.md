---
title: "completely remove kubuntu in synaptic"
date: 2007-02-07
forum: General Help
---

### Post by carverj on 2007-02-07
Hi all,
        Recently installed Kubuntu and now I want to tar backup and want to revert back to just gnome for the process (basically so I can burn to DVD with Gnome K3b).
I noticed that Synaptic only gives me the option to "Completely remove" Kubuntu-desktop.
Is this going to affect me or is it just going to remove all the K desktop config. and packages safely?
Thanks guys and gals

---

### Post by r4ik on 2007-02-07
Try,

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Good luck !

---

### Post by carverj on 2007-02-07
Thank you for that. Managed to free up 7oo MB or so.
There still seems to be loads of unaccounted for space on the drive.
I used the command below to backup and then deleted as it was to big to burn to K3b (>4GB)
```
tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys --exclude=/media --exclude=/home /

```

This file was named backup.tgz or similar, and when I tried to delete it with the delete key, it seemed to rename it and stash it elsewhere!
So I located it and moved it to the trash bin with Konqueror (as root) to try to get rid that way.

Tried to search for files bigger than 2G which have been altered in the last 24 hours to no avail
Does this mean my calculations are incorrect? Is there another method for me to track huge unwanted erroneous data?
Thanks again

---

### Post by r4ik on 2007-02-07
You could try places -search for files - select more options and from the dropdown menu select "size at least"
Not sure but worth a try.

---

### Post by carverj on 2007-02-07
No, can't find any offending files!
So if I have a 9-10G worth of data on my Ubuntu drive, can this be compressed down to back up to DVD?

---

### Post by chavo on 2007-02-07
Try removing your apt cache. 
```

apt-get clean

```
That will remove all of the deb files that are cached by apt-get.

---

### Post by carverj on 2007-02-07
That takes care of another half gig or so :) 
Is it possible to split the tar command so that it can fit on 2 DVD's?

---

