---
title: "Backup of PNG files problem"
date: 2014-08-28
forum: General Help
---

### Post by pancho5 on 2014-08-28
Hello!

In the process of using the Lubuntu "Screenshot" accessorie to save space of JPEG files, my intention was/is to back them up on a jump drive (Lexar 8GB).  When I back them up, I get error messages that say:

"Screenshot from xxxx-xx-xx ......PNG: Invalid filename"  (see attachment)

What do I have to change/do so that I can backup PNG files?

Thanks in advance.

---

### Post by sudodus on 2014-08-28
I suspect that there are problems because the file names contain special characters, for example space ' ' and  colon ':'.

If this is the problem, you can either use a program or script that can manage file names with special characters, or remove the special characters from the file names.

Removing the special characters can be done with a shellscript (that you make with some help), but check, that no other program is depending of those particular file names. In your case it seems to indicate the time the files were created. Unless you create a lot of screenshots automatically, I think it is a good idea to give those files descriptive file names instead of those numbers. And avoid special characters ;-)

---

### Post by pancho5 on 2014-08-28
> **sudodus said:**
> I suspect that there are problems because the file names contain special characters, for example space ' ' and  colon ':'.

If this is the problem, you can either use a program or script that can manage file names with special characters, or remove the special characters from the file names.

Removing the special characters can be done with a shellscript (that you make with some help), but check, that no other program is depending of those particular file names. In your case it seems to indicate the time the files were created. Unless you create a lot of screenshots automatically, I think it is a good idea to give those files descriptive file names instead of those numbers. And avoid special characters ;-)

Thank you for your assistance.  Not to familiar with scripting...its been a long, long, time since I took a Unix Systems & C hands on training course.  I did a test using descriptive file names and it did work and I was able to back it up to my jump drive.  The pictures from the "Screenshot" application were not that critical.  But, they would be if they were personal/family photos.  So, I will just use descriptive names for now on.  Thanks again!):P

---

### Post by sudodus on 2014-08-28
You are welcome :-)

---

