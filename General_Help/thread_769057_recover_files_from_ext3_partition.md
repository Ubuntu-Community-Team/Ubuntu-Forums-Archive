---
title: "recover files from ext3 partition"
date: 2008-04-26
forum: General Help
---

### Post by brynk on 2008-04-26
I just reinstalled a pc of mine with Hardy. Afterwards I discovered that I forgot to backup an important database. I've been trying to recover it using various tools such as foremost, photorec and autopsy, but so far no luck...
I managed to pull a lot of images and other files off the drive and even came across some snippets of db information using search tools, but I couldn't figure out how to recover the complete MySQL files stored in /var/lib/mysql.
Can anyone help me out?

---

### Post by tamoneya on 2008-04-26
if those tools didnt do a full recover of your files you are either going to need to pay a professional data recovery service to do it or give up.  PhotoRec and AutoPsy are both pretty nice and if they cant find your database you are more or less out of luck.

---

### Post by brynk on 2008-04-26
Ok, but that's assuming I got the most I could out of these tools and since I've never used them before I'm not sure I did.
Since I managed to pull so much other deleted files off the drive I can't help but feel there must be something left of my databases.

---

### Post by brynk on 2008-05-03
I'm still trying to recover the lost db and managed to get a hole bunch of .frm and .MYI files using photorec. There weren't any .MYD files returned.
Can anyone tell me how I can see the contents of the .MYI files without the .MYD?

---

### Post by brynk on 2008-05-07
:'(

---

### Post by TechZilla on 2011-03-05
sorry for re-open, but im having same issue.

FYI photorec is awesome for most file but lacks support for MYD files. recovered MYI and frm, bit not the actual database data.  

so....

i've been trying ext3grep, but i keep getting segfaults.  i 'm going to try sluethkit next

---

