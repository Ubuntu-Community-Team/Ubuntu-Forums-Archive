---
title: "Can't Rename Files to UPPER-CASE"
date: 2007-12-18
forum: General Help
---

### Post by xluryan on 2007-12-18
This is a REALLY odd problem, and I have no idea what's going on...

I run this command:
```

mv video_ts.bup VIDEO_TS.BUP

```

And get this output:
```

mv: `video_ts.bup' and `VIDEO_TS.BUP' are the same file

```

I'm pretty sure linux still holds upper and lower case filenames different from each other. Any ideas?

---

### Post by taurus on 2007-12-18
What filesystem are you trying to change the name on?

---

### Post by HermanAB on 2007-12-18
Windoze NTFS and VFAT are case insensitive.

Cheers,

Herman

---

### Post by xluryan on 2007-12-19
That was probably it. It was a FAT32. I moved the files over to an EXT3 and case started to matter again.

:P

---

### Post by geirha on 2007-12-19
On fat and ntfs you'll have to rename it to a different name first, so something like this should work
```
mv video_ts.bup video_ts.bup.tmp &&
mv video_ts.bup.tmp VIDEO_TS.BUP
```

---

### Post by xluryan on 2007-12-19
Didn't. They all just go to lower-case no matter what I mv them as. Not a big deal though; you can't make a DVD on a FAT system anyway, because they don't support files over 4GB...

---

### Post by nick_h on 2007-12-19
For FAT, use the mount option shortname=mixed in your /etc/fstab to get the upper case.

---

