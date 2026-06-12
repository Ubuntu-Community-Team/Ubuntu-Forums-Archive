---
title: "[SOLVED] File permissions in DigiKam"
date: 2008-03-11
forum: General Help
---

### Post by agaudio on 2008-03-11
I'm not sure if this is the right forum, but I will give it a go anyway.

I have been trying out DigiKam for the last few days and I like it a lot. I am running it on my Gnome Desktop but this has not caused any trouble. However, I am facing one somewhat annoying problem.  I am sharing one large album (subdivided into folders by year and month) among both users on my desktop computer. The problem is that if one user imports some new pictures from our digital camera, the new pictures get the file permissions:

```
-rw-r--r--
```

This of course means that the other user on the computer cannot make modifications in the file without first opening a terminal and chmoding the right permissions. Is there any way to automate this so that all new files in a folder with permissions 

```
drwxrw-r--
```

will automatically take on the permissions of the folder? Or is there some other solution that I am not thinking of?

Thanks!

---

### Post by justleen on 2008-03-11
that depens on Digikam i'd say...

is there no option in Digikam to change default ownership?

---

### Post by agaudio on 2008-03-11
I looked for something like that but alas to no avail. I saw on some forum a discussion of UMASK - having to do with a different problem, but still, could that be something?

---

### Post by justleen on 2008-03-11
UMASK is the User Mask you apply - which means, the rights for a user

by the looks of it (google) this is just of digicam works.. you'll have to change the permissions afterwards by hand...

---

