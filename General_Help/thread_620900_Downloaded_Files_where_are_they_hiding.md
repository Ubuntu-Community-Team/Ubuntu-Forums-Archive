---
title: "Downloaded Files where are they hiding?"
date: 2007-11-23
forum: General Help
---

### Post by tezzaa on 2007-11-23
This is a real basic question, but I am a newbie.

When I dowload files I can see them in the Download Manager, but have not worked out where they are in the File System :(

Where do I need to look?

tezzaa

---

### Post by namanbagga on 2007-11-23
Search your home folder

---

### Post by Rahmat on 2007-11-23
HI

I would also like to add that it may be in your var/temp folder.  But you shuold still check your home folder or your desktop.  AM sure you can navigate to your home folder! 

:lolflag:

---

### Post by the yawner on 2007-11-23
Erm... If you're using Firefox the downloads usually go to your desktop. It's in your home folder.

---

### Post by Cannaregio on 2007-11-23
Find them wherever they are

First
```
sudo updatedb
```

Then
```
locate target_file
```
where "target_file" is the file you'r looking for

---

### Post by tezzaa on 2007-11-23
Thank you all very much for your replies

Tezzaa

---

### Post by louieb on 2007-11-23
Using Firefox?
Edit>Preferences>Main 
Download location is set there.:mad:

---

