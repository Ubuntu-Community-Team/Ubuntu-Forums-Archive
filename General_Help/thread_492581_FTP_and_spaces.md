---
title: "FTP and spaces"
date: 2007-07-04
forum: General Help
---

### Post by Rebel Dragon on 2007-07-04
Hello all!

I've got a ton of pictures of my kids that I want to upload to my website via FTP. I'm using gftp, and it works great but now I've hit a wall. My lovely wife (who took most of the pics with the digicam) uploaded all of the pics to the computer with spaces in the filenames.  ](*,)

Her intentions were good, because she named them by date, but now it's a nightmare to try and upload them because the server doesn't support spaces in the file name. Is there an easy way to strip the spaces from the file names, without manually renaming each picture?

:confused:

---

### Post by croto on 2007-07-04
Hi! Open a terminal, go the folder where you have the pictures and type:

```

rename 's/ /_/g' *.jpg

```

It will replace all spaces by underscores in all files matching *jpg . I hope it helps.

EDIT: I know there are two *very different* versions of this command "rename". The code above works with the version shipped with Ubuntu. Other distributions may have the other version.

---

### Post by Rebel Dragon on 2007-07-05
Cool - thanks!

---

### Post by stylishpants on 2007-07-05
For future reference, there are also ways to automatically rename the pics based on the date in the photo's EXIF tags, so your lovely wife doesn't need to do that by hand. 

[http://ubuntuforums.org/showthread.php?t=481010](http://ubuntuforums.org/showthread.php?t=481010)

---

### Post by Rebel Dragon on 2007-07-05
Thanks Stylish - I'll have to check that out when I get home!

---

