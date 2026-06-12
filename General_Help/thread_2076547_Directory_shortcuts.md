---
title: "Directory shortcuts"
date: 2012-10-26
forum: General Help
---

### Post by Dai777 on 2012-10-26
Before I updated this morning I had set up some directory short cuts such as:

ln -s /media/'My Book'/Linux/dai1/Documents /home/dai/Documents/

Now these shortcuts have been renewed but, they throw up a dialog box instead of connecting to the directory on my external hard drive.

How do I get them to work as before by just clkicking on an icon in one directory and going into the directory on my external hard drive.

Thanks in advance 
Dai



















:

---

### Post by drmrgd on 2012-10-26
What does the dialog box say?  

This command also seems to be backward.  It should be TARGET first then LINK_NAME.  By the looks of it, you have the LINK-NAME first and then the target.

```
ln -s /media/'My Book'/Linux/dai1/Documents /home/dai/Documents/
```

Also, if you run ls -l in the terminal where that link it, do you see it pointing to the correct place?  Usually a broken symbolic link will be colored red and will not be pointing where you want it to.

---

### Post by Dai777 on 2012-10-26
> **drmrgd said:**
> What does the dialog box say?  

This command also seems to be backward.  It should be TARGET first then LINK_NAME.  By the looks of it, you have the LINK-NAME first and then the target.

```
ln -s /media/'My Book'/Linux/dai1/Documents /home/dai/Documents/
```

Also, if you run ls -l in the terminal where that link it, do you see it pointing to the correct place?  Usually a broken symbolic link will be colored red and will not be pointing where you want it to.

The directory structure was changed in the upgrade

this works fine:
ln -s /media/dai/'My Book'/Linux/dai1/Downloads /home/dai/Downloads/

---

