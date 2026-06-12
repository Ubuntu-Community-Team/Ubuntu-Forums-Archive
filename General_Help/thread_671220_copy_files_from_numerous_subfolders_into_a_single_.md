---
title: "copy files from numerous subfolders into a single folder"
date: 2008-01-18
forum: General Help
---

### Post by gorlop on 2008-01-18
I have thousands of jpgs in numerous subfolders within a folder called pictures. I would like to copy all of the files into a single folder. Is there an easy way to do this? Obviously, I could go into each subfolder, copy the contents, and paste it into the new folder, but this would take forever given the number of folders that I'm working with. 

I basically want to resize all of the pictures with gthumb without having to do each subfolder separately.

---

### Post by gvartser on 2008-01-18
Lets say that your root folder where you store your pictures in is called:
-> Pictures

and you want to copy those to:
-> All_Pictures

then this a way to do it.

#) [COLOR="DarkGreen"]for file in $(find Pictures -name *.jpg);do cp ${file} All_Pictures/; done[/COLOR]

Or why not resize your images on the fly without moving them:
#) [COLOR="DarkGreen"]for file in $(find Pictures -name *.jpg);do mogrify  -resize 1024x768 -quality 80% ${file}; done[/COLOR]

NOTE!
to get mogrify to work you need to install:
ImageMagick
#) [COLOR="DarkGreen"]sudo apt-get install imagemagick[/COLOR]

Best regz,
/G

---

### Post by gorlop on 2008-01-18
Thanks for the suggestions. I tried both of these in a test folder:

> **gvartser said:**
> #) [COLOR="DarkGreen"]for file in $(find Pictures -name *.jpg);do cp ${file} All_Pictures/; done[/COLOR]

Or why not resize your images on the fly without moving them:
#) [COLOR="DarkGreen"]for file in $(find Pictures -name *.jpg);do mogrify  -resize 1024x768 -quality 80% ${file}; done[/COLOR]
/G

It worked on some of the files, but I received a "No such file or directory" message for the majority of files.

---

### Post by heindsight on 2008-01-18
> **gorlop said:**
> Thanks for the suggestions. I tried both of these in a test folder:



It worked on some of the files, but I received a "No such file or directory" message for the majority of files.

The problem with using a for loop for this, is that if some filenames have spaces in them, they'll be split into separate words. 
A better way to copy all your .jpg files from directories under ~/Pictures into ~/All_Pictures, would be:

```
find ~/Pictures -name "*.jpg" -exec cp \{\} ~/All_Pictures/ \;
```
(of course this assumes that the directory ~/All_Pictures already exists...)

---

### Post by gvartser on 2008-01-19
[QUOTE=heindsight;4160916]The problem with using a for loop for this, is that if some filenames have spaces in them, they'll be split into separate words. 

Yes this is true, didn't think about that. Just assumed that the files didn't have spaces in them. Silly me..

---

