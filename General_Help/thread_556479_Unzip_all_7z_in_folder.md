---
title: "Unzip all 7z in folder"
date: 2007-09-21
forum: General Help
---

### Post by Githlar on 2007-09-21
I'm trying to unzip all 7z archives in a folder, but I just can't seem to get it to work.

I tried:

ls *.7z > filelist
7z x @filelist

And it gives me an error saying something like unknown archive.

I thought about trying to use a shell script to do it, but I can't think of how I might go through that file list line by line and extract them.

Also, when these are extracted, I want to zip all the files into individual zip archives with a shell script. I think i'll have the same problem doing this, too.

---

### Post by FuturePilot on 2007-09-21
Try
```
cd /folder
```
```
p7zip -d *.7z
```

---

### Post by Githlar on 2007-09-21
What's the difference between 7z and p7zip?

I got it to work with:
p7zip -d \*.7z

---

### Post by FuturePilot on 2007-09-21
p7zip is the name of the archive program.  7z is the file extension.

---

### Post by Githlar on 2007-09-21
7z is a program too. And it says it can 7z/un7z and everything...

---

### Post by FuturePilot on 2007-09-21
Oh, I see. I always use p7zip though.

---

### Post by Githlar on 2007-09-21
Do you know I could recurse files in a directory and zip them all?

---

### Post by FuturePilot on 2007-09-21
Do you want them all in one archive? You could just highlight them all, right click>Create archive. Title it something and select the .7z archive type, or whatever type you want.

---

### Post by Githlar on 2007-09-21
No, I'd like them all in individual archives.

---

