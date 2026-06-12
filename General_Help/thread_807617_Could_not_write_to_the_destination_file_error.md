---
title: "Could not write to the destination file error"
date: 2008-05-26
forum: General Help
---

### Post by jason1500 on 2008-05-26
Hello, this is my very first linux install and I can't unzip a zip file :(  I double click the zip file and Ark comes up I hit extract and in the output folder box i type /home/jason/Desktop then I hit ok and I get the error "Could not write to the destination".  What am I doing wrong??  I even get the error if I try extracting to /home/jason/Documents. Help please! thanks

---

### Post by anjilslaire on 2008-05-26
Right-click the archive and select
Extract To 'nameoffile/'

It'll create a folder the same name as the archive file and place the contents in it, in the same location as the original.

---

### Post by jason1500 on 2008-05-26
There is no such option is the right-click menu.  I am using Kubuntu with KDE 4 is that helps any.

---

### Post by anjilslaire on 2008-05-26
Weird, I run Hardy Kubuntu with KDE3. Perhaps I have some extra archive tools installed I've forgotten about...

Is this a zip file? tar? 

1st off, KDE is a single-click environment by default. Break yourself of the double-click habit.
1. Click on the archive. 
2. When ark opens, click the Extract button. 
3. Then, in the next window, instead of typing the location, click the Folder icon to the right, and browse to where you want it extracted, 
4.then click OK, and then OK again. 

It should be extracted correctly.
I had too many buggy issues with KDE4, so I went back to KDE3.5.9

---

### Post by Chronon on 2008-10-09
Hi, I am getting the same problem and am also using KDE4.  Ark has worked quite well in other situations (from a Knoppix LiveCD, for instance).  But here, I can't seem to get it to extract, even when going through the exact procedure that you listed.

Perhaps this is one of those buggy issues.  I also notice that the the Configure Ark option is missing from the Settings menu.  (By the way,I'm using ark-kde4.)

---

### Post by SuperSonic4 on 2008-10-09
Right Click on the zip and click open with ark

Then click extract and try putting it in /home/jason (or whatever). Be sure to tick the extract all box. What file is it? Link me and I'll test it

---

### Post by Chronon on 2008-10-09
The zip archive I'm trying to extract can be found here: [http://build.rockbox.org/dist/build-mrobe100/rockbox.zip]("http://build.rockbox.org/dist/build-mrobe100/rockbox.zip").

I appreciate your response.  But understanding how to open the archive with Ark is not my problem.  I can open the archive fine.  I can browse the contents.  I cannot extract either selected files or all files to any location I have tried. .  not my home directory or download folder or the device that I actually would like to extract it to.  I guess I should just extract it from the command line.  It's just a bit frustrating that it has worked so easily before and now something is mysteriously broken.

There's nothing wrong with the archive itself. I'm quite certain of that, as I have had this problem before and then successfully extracted with another method.

----

edit: Entering the archive from Dolphin allows me to simply copy and paste to the desired destination, but is not my preferred method, since hidden directories can complicate matters.  I'll keep an eye out for any new info about this.  Until then I'll just extract from bash.

---

