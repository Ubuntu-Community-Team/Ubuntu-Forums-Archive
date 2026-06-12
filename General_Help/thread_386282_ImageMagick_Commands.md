---
title: "ImageMagick Commands"
date: 2007-03-16
forum: General Help
---

### Post by Guns90 on 2007-03-16
Hello all.  What I'm trying to do is  simply find a quick and simple way to resize photos.  I think a command-line making use of ImageMagick would work real nice, but I just can't figure out what I'm doing wrong.  My file is called Eagle.jpg and It's file size is 830Kb.  I want to reduce it's widthe from 2816 to 1024 and have the heighth automatically adjust itself to keep conformity.  Here is the command(s) I've been using and what happens:

gary@Faith:~$ convert Eagle.jpg -resize width 1024
convert: unable to open image `Eagle.jpg': No such file or directory.
gary@Faith:~$


Can someone tell me please what I'm doing wrong?  Thanks
 Gary

---

### Post by llamakc on 2007-03-16
You need to be in the same directory as the image for starters. If it's on your desktop, do a

cd ~/Desktop

first.

Secondly, doesn't `convert` require a target image-name?

---

### Post by Guns90 on 2007-03-16
Sorry about that, llamkc.  I typed that command into my post, not copy/paste.  I was in the correct directory when I typed in the command.  The only decent tutorial I have found is [http://www.imagemagick.org/script/command-line-options.php#resize](http://www.imagemagick.org/script/command-line-options.php#resize) . It doesn't say anything about target image-name that I see.  I've been trying variouys ways, but still no luck.

gary@Faith:~$ cd ~/Desktop
gary@Faith:~/Desktop$ convert -resize x1024 Eagle.jpg
convert: missing an image filename `Eagle.jpg'.
gary@Faith:~/Desktop$ convert -resize x1024 -Eagle.jpg
convert: missing an image filename `-Eagle.jpg'.
gary@Faith:~/Desktop$

---

### Post by llamakc on 2007-03-16
So the way it works is it takes input.jpg and creates output.jpg. You need to be typing:

convert filename.jpg (-your options) targetfile.jpg

You have to tell it what the new filename is going to be.

---

### Post by Guns90 on 2007-03-16
Thank you llamakc.   You're right.   This is what works for me:

gary@Faith:~$ cd ~/Desktop
gary@Faith:~/Desktop$ convert -resize x800 0001.jpg truck.jpg

---

