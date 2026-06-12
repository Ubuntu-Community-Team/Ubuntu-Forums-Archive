---
title: "Save pics and vids not diplayed in windows"
date: 2007-10-30
forum: General Help
---

### Post by Roen hayden on 2007-10-30
OK i have saved some pics and vids from the internet on a external hard drive they show up fine in ubuntu. and the thumbnail is displayed but when i connect the external Harddrive to my windows computer it reads some of those pics and vids as just a "." or a ".file" and no thumbnail displayed any idea what could cause this?

---

### Post by Roen hayden on 2007-11-01
any idea?

---

### Post by minus198 on 2007-11-01
What filesystem does the drive have? NTFS, EXT3?

---

### Post by timcredible on 2007-11-01
linux will look at the file and find out what type of file it is regardless of it's name - ie. you can save a picture file as test.doc and it will understand it's a picture and show you a thumbnail of it.  windows only looks at the filename extension to determine the file type, so unless you named the files with a well-known extension like .jpg or .png, it won't try to display a thumbnail.

---

