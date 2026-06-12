---
title: "Merging 2 .avi's in one"
date: 2006-12-19
forum: General Help
---

### Post by juantovarm on 2006-12-19
I downloaded an anime that comes in two parts, and i would like to merge them into one big file, for the person who uploaded them had to split it in two making it impossible to open the second file. Any ideas?

---

### Post by _mrv on 2006-12-19
> **juantovarm said:**
> the person who uploaded them had to split it in two making it impossible to open the second file

So the second file is not a valid file, but just a part of AVI file? Then I think you could just:

```
cat file1.avi file2.avi > output.avi
```

 _mrv

---

### Post by juantovarm on 2006-12-19
thanks! worked like a charm and in less than 10 seconds :D

---

### Post by jazzgossen on 2006-12-19
For future reference, you can also use the program avidemux to mix movie clips.

---

### Post by dminister27 on 2007-11-21
Im trying to merge 2 avi files.  Im using  cat we1.avi we2.avi > we3.avi   When I enter this command im getting no such file or directory.  I know the files are there I just renamed and watched them.  Any ideas???

---

### Post by juantovarm on 2007-11-21
First of all, in the terminal you have to be in the directory where the files are, you can do that with the command: 
```
cd 
```

for example if the files are in the desktop then 
```
cd /home/juan/Desktop
```
("juan" is of course the name of my home folder, replace it with the name in yours)

Once you are in the folder where your files are, then you can merge them using cat.

Remember to always use your TAB key while using the terminal, it completes the names of folders/files, that is a good way to check you are entering the right path and name of a folder/file, AND you avoid mispellings

---

### Post by dminister27 on 2007-11-22
Thank you for the speedy response.  The files are merged, this is where i hit another bump.  When I open we3 in movie player it has only the video from we1.  we2 video is missing.  I checked the math.  we3 is the size of both files combined.  Any ideas?? 
Also I would like to say thank you to the ubuntu community.  I have pledged to never use windows again, and so far I'm loving ubuntu. :-D

---

### Post by hikaricore on 2007-11-22
Just so you know, "cat" is not a recommended or correct way of merging avi files.

AVI is a container for other formats such as vxid video and mp3 audio.
Each AVI container file has file headers and other information stored in it as to the type, size, ect of the formats contained in it.

Merging AVI files with cat physically joins the files together and does nothing with the header data, leaving the second header in the middle.
This may be all fine and well for other formats that are just pure video or audio such as video mpegs and audio wav files, but as you can see it causes issues in container formats.

The best way would be to use cli tools like avimerge (which i believe is included with the _transcode_ package but I may be mistaken) or gui based video editing tools like _avidemux2_ which should be in the Ubuntu universe repos.

Hope this helps and best of luck.

--Aaron

---

