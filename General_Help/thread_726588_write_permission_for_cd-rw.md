---
title: "write permission for cd-rw"
date: 2008-03-16
forum: General Help
---

### Post by kwboom on 2008-03-16
Hi there I just installed Ubuntu to a friends PC and  I am trying to burn a music CD but it keeps telling me that I don't have wirte permission to burn to the cd-rw...... What am I missing????????

---

### Post by pointone on 2008-03-16
Try adding the user to the cdrom group if they're not already a member.

---

### Post by kwboom on 2008-03-16
I am a total newb with linux so you migt have to explain a bit more for me......How do you add to other group????

---

### Post by kwboom on 2008-03-16
I keep getting this error pop up in another window......

Cache directory location unavailable

Please check if the cache location exists 
and has writable permissions.

Cache location:  bruce


Also I must add...... I just burned a cd with MP3's directly as data with it just by putting the files in the CD-RW drive and not through the Serpentine program and it burnt them as data but it will not burn as music files that regular cd players will play them.

---

### Post by kwboom on 2008-03-16
bump for some help......

---

### Post by gam3r4eva on 2008-03-16
You don't need to bump after less than forty minutes.  Give people a chance to answer before you bump.

To add a user to the cdrom group go to:

System>>Administration>>Users and Groups

Now click on your user, then click the properties button on the right.

Click the "User Privileges" tab and make sure the "Use CD-ROM drives button is checked.

That will make sure your user is in the CD-ROM group.

---

### Post by kwboom on 2008-03-17
Sorry for the fast bump but I will wait longer next time.......

I did check under user groups and it is listed there under his name....  Could it be anything else......

---

### Post by BenjaminGTF on 2008-03-18
I had the same problem, and same output.

Serpentine needs to temporarily put wav files in your home directory, so make sure you have at least 700 MB free in your home directory.

---

