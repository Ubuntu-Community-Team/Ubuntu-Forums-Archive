---
title: "Gdm Could Not Write The Auth File"
date: 2007-02-12
forum: General Help
---

### Post by maprx on 2007-02-12
I have read all the post with regard the deleteing the xauthority, Iceauthority, etc.  I can only log as root.  PLEASE IN ENGLISH TELL ME HOW TO GET MY USER BACK.  The system also reports 100% disk usage. SO, something big is hogging my space.  I assure you I had plenty of space on the drive, where did that go:confused: :confused: :confused: :confused: :confused: :confused:

---

### Post by Ramses de Norre on 2007-02-12
If you don't have a separate home partition, try this:
```
sudo aptitude clean
```
If /home is on a separate partition you'll need to log in as root and use rm to delete or mv to move some files to create space.
I can't tell anything about the reason with this poor info, have you done anything particular before this issue appeared? (Something that could have created a lot of files?)

---

### Post by maprx on 2007-02-12
i ran a unpdate and then i get this error.  i can log in as root and i can move to my home directory? do i run the command there?

---

### Post by maprx on 2007-02-12
how can i tell what file is the hog

---

### Post by maprx on 2007-02-12
> **Ramses de Norre said:**
> If you don't have a separate home partition, try this:
```
sudo aptitude clean
```
If /home is on a separate partition you'll need to log in as root and use rm to delete or mv to move some files to create space.
I can't tell anything about the reason with this poor info, have you done anything particular before this issue appeared? (Something that could have created a lot of files?)

did nothing, if i can't tell what the file is I assume a tmp file, how can i rm move it?

---

