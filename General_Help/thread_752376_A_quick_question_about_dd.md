---
title: "A quick question about dd"
date: 2008-04-11
forum: General Help
---

### Post by Tsuki on 2008-04-11
As it's probably quicker to ask than to try it myself and wait...

I have a 1 TB partition with 20 GB of data on it, and I'd like to make an image of it.  If I do something along the lines of:

```
dd if=/dev/sda1 of=~/sda1.img
```

How big would sda1.img be - 20 GB or 1 TB?

(If, as I'm guessing, it's 1 TB, is there an equivalent that would produce a 20 GB image?  I know I could compress the 1 TB file down quite happily, but I don't have a spare terabyte to store the image in the mean time!)

---

### Post by bingoUV on 2008-04-11
What do you want to do with the image? I mean you could just archive the data instead of making the image. Is there some reason you need to make an image?

The answer would depend on how you are going to use the image.

---

### Post by Tsuki on 2008-04-11
It's an image of a Windows partition, so I wasn't sure if something would be lost if I just backed up the files.

The image (or archive, whatever I end up creating) is a backup of the original state of a system, so that a (non-techie) end user can restore it if necessary by as simple a means as possible.

---

### Post by bingoUV on 2008-04-11
OK, I see. In windows world, not everything is a file. Microsoft must be giivng some utility to backup, but seeing that you are now in linux world ....

If it is ntfs filesystem, ntfsclone from ntfsprogs package should do it. Use -s option to create about 20G image rather than 1TB. 
```

sudo apt-get install ntfsprogs

```

---

### Post by Tsuki on 2008-04-11
Will give that a go on Monday.  Thanks for your help!

---

