---
title: "[SOLVED] tar files"
date: 2008-05-19
forum: General Help
---

### Post by luckymoonboy1 on 2008-05-19
how do i install a tar i read the thing in the help and it said to type the stuff in a terminal so i did and it said no such file or directory exists. how do i do this becouse i think i'm doing it wrong. i need moron instructions im not that good with techno bable. i would apritiate any help possible.

---

### Post by ivze on 2008-05-19
That would be difficult to understand what' going wrong without the aid of telepatics :). Please, post more details. 
If you are installing something from a .tar.bz2, you have probably stuck at the stage of extracting the archive contents. 
By the way, what application is this? If it's in repositories, that would be much simpler to install.

---

### Post by sdennie on 2008-05-19
It might be easier to go to Places->Home Folder, locate the thing you downloaded and double click on it.  That should bring up an application that can extract the archive for you.

---

### Post by luckymoonboy1 on 2008-05-20
first: the files are .tgz and second: my computer is not connected to the internet. every file sent to it is sent via usb drive and i'll try the clicking on it i dont know why i didn't try that in the first place.

---

### Post by sdennie on 2008-05-20
I believe that files that end with .tgz are actually just files that are .tar.gz.  Once you've downloaded them, finding them in the normal file manager should work fine.

---

### Post by cdtech on 2008-05-20
Files with extension tar.gz or .tgz are tar files compressed with gzip. In Ubuntu extract them with:

    tar xvzf file.tar.gz
    tar xvzf file.tgz

Remove the "z" if it's just a plain tar file, replace it with a "j" for .tar.bz

Hope this helps.......

---

### Post by bingoUV on 2008-05-20
How to install anything in Ubuntu : [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by luckymoonboy1 on 2008-05-22
thanks every one fro trying to help and thanks BingoUV for the guide to installation it will help with many more problems as well. Thanks all For your help!:)

---

