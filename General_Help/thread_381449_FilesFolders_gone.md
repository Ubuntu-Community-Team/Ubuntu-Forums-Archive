---
title: "Files/Folders gone"
date: 2007-03-10
forum: General Help
---

### Post by z987k on 2007-03-10
Recently I did a chmod 766 to a folder and all of it's sub-folders and contents as some had permissions that didn't allow non-root access.  It was a hard drive from a different machine formated ext3.  I went to the folder with nautilus and while all the immediate sub folders were there, every one of them and their contents are either completely gone, or they are a 0byte file that retains the original file/folder name.  I have no idea how this happened, my first reaction was wtf?  Is there a way to recover my data?  There was a lot... 50gigs or so.  Everything else on the drive is fine.

Thanks for your help,
Zach

---

### Post by Famicommie on 2007-03-10
What was the precise command that you entered?

Navigate to the folder in question from the terminal, and input the command

```
ls -al
```

What is the output?

---

### Post by z987k on 2007-03-10
They are all:

```
drw-r--r--   3 zach            500  4096 1969-12-31 18:00
```

of course with the 3 differing depending on number of messed up files/folders in them.

---

### Post by Famicommie on 2007-03-10
Okay Zack, how were you accessing this drive? Did you physically install it into the computer that you are working on?

Also, I am very disturbed that the dates are all from 1969

---

### Post by z987k on 2007-03-10
Removed it from the old machine and put it in the new one, then did the ```
sudo chmod -R 766 * 
``` in the pwd.

---

### Post by Famicommie on 2007-03-11
Bizarre. If it was a lot of stuff, I think that my first course of action would be to drop the HD back in the old machine and see if there is anything left on it.

---

### Post by z987k on 2007-03-11
Well everything is fine except the single folded.  There's like 7 main folders then each has sub-directories.  The one folder and all it's sub's did this.

---

### Post by z987k on 2007-03-12
Ok, well I figured it out.  I chmoded all of the folders 777 and chowned all of them 500, which brought everything back.  I thought I had done that, but I noticed I could see everything while browsing as root.

---

