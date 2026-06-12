---
title: "Media Files Going Blank, 0KB On Samsung SSD"
date: 2017-03-29
forum: General Help
---

### Post by ThePowerpuffGirls on 2017-03-29
I bought a 500GB SSD to replace the 500GB HDD we have in our office for backup storage.

I did a check to see if all copied, and noticed that 5 picture folders, plus 3 video files has 'blank' icons and says 0KB of space they use.
3 pictures in one folder are OK, and 4 in another are OK.
The last time I viewed these photos was months ago and they were alright.
It's a total of 89 picture that went corrupted/blank, which is only about 5% of all the pictures that were copied over.

I noticed this happened before on another drive on another computer. Nothing was done with the files, they are just there for storage, backup. It is a 250GB SSD, that is usually unplugged from the computer and on a shelf. On the 250GB storage drive, there were some folders with random pictures that went corrupt or blank, opposed to the whole folder.
Both drives are Samsung 850 EVO drives, which is pretty much the kind all the computers have here.
It seems be mostly pictures it happens to.
I have some TB drives with downloaded movies/TV shows and never had that issue with them.
What could cause the files to go blank; what is special about this images/folders?

Whenever I copy data over, I always go into the search bar and search file formats and search by lowest storage first because of this experience.

[http://i66.tinypic.com/s4mavl.png](http://i66.tinypic.com/s4mavl.png)

---

### Post by TheFu on 2017-03-29
Disk corruption can be caused by anything in the chain. If you are seeing it on multiple disks, then it is probably something upstream - a cracked network card?  Perhaps?  I've seen this before.

I know of 2 solutions to fight file corruption for storage that isn't used all the time.
a) use ZFS. It is the only file system that validates what was asked to be written is actually written.
b) use parity files - **par2** can make them and provides a way to validate the file(s) haven't become corrupted with the ability to correct it, if not too large.

A small script to create 10% par2 files.
```

#!/bin/sh
for filename in &#8220;$@&#8221;; do
  # Create a 10% recovery data with blocksize of 300KB
  nice par2 create -s307200 -r10 &#8220;$filename&#8221;
done

```

In theory, storage checksums (which is part of optical storage) should prevent the corruption, but that hasn't been my experience. I've recovered corrupted files from optical media thanks to having par2 files ON THE SAME MEDIA.

I'd be interested in seeing what other people are doing too.

---

