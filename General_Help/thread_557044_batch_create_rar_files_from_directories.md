---
title: "batch create rar files from directories?"
date: 2007-09-22
forum: General Help
---

### Post by helwitch on 2007-09-22
I have 100+ directories, each of which has between 20-50 files in it. I want to create one rar file for each directory, with the name of the directory being the name of the rar file, and with the rar file having in it the files that were in the directory, without any directory/path info in the rars. And I want to NOT do this manually for each directory. Is this possible?
To elaborate, I have directories a through z, each of which has files 1.jpg through 25.jpg. I want rar files named a through z, and in each rar file, files 1.jpg through 25.jpg. (I want to create rars so I can rename them to cbr so they'll open in comicbook reader software, and I can just give people one cbr file instead of a bajillion jpgs.)

---

### Post by ghantoos on 2007-09-22
Create a shell script. Shouldn't be very hard. Here are some links.

[http://steve-parker.org/sh/intro.shtml](http://steve-parker.org/sh/intro.shtml)
[http://www.freeos.com/guides/lsst/index.html](http://www.freeos.com/guides/lsst/index.html)
[http://www-128.ibm.com/developerworks/library/l-bash.html](http://www-128.ibm.com/developerworks/library/l-bash.html)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

cheers,

ghantoos

---

### Post by jdusablon on 2008-02-25
Jeez. Not very nice. "Go read a book."

---

### Post by helwitch on 2008-02-25
Yeah, I never did work out how to make rars from those links. *shrug*

---

### Post by danwood76 on 2008-02-25
A shell script is the ideal way to do it.
There arent any GUIs that will do that for you, winrar doesnt even do that without you telling it each individual dir.

You can make a shell script that parses dir names and issues the rar command to generate the .rar file.

---

### Post by mm2004 on 2008-02-26
> **helwitch said:**
> I have 100+ directories, each of which has between 20-50 files in it. I want to create one rar file for each directory, with the name of the directory being the name of the rar file, and with the rar file having in it the files that were in the directory, without any directory/path info in the rars. And I want to NOT do this manually for each directory. Is this possible?
To elaborate, I have directories a through z, each of which has files 1.jpg through 25.jpg. I want rar files named a through z, and in each rar file, files 1.jpg through 25.jpg. (I want to create rars so I can rename them to cbr so they'll open in comicbook reader software, and I can just give people one cbr file instead of a bajillion jpgs.)

hi i have made a little nautilus-script with gui (front end so to speek) dialog many scripts are using it these days if anyone is interested i can post it somewhere somehow so you guys can get it

i have 2 versions of this script as iv never made a script with gui b4 iv tried to keep it as simple as possible here are a few screenshots so you can get an idea onwhat it does.

[img]http://img101.imageshack.us/img101/1792/screenshotsf3.png[/img]
[img]http://img101.imageshack.us/img101/9984/screenshot1rt6.png[/img]
[img]http://img101.imageshack.us/img101/9585/screenshot2eh8.png[/img]
[img]http://img521.imageshack.us/img521/6017/screenshot3vc1.png[/img]
[img]http://img521.imageshack.us/img521/4812/screenshot4vs9.png[/img]
[img]http://img521.imageshack.us/img521/6826/screenshot5nu3.png[/img]

PLEASE NOTE its my first time at this. Im running ubuntu 7.10 gutsy and it works FLAWLESS not an error from it. works everytime the only thin it cant do is rar multiple selected files but what can be done is create a folder on the desktop put all the files you want in the rar in that folder.
Then right click the folder goto scripts rar it will rar a folder and everything in that folder.


let me know ppl i might even work on a updated version if its wanted enough. also in the option is an option to split the rar's like default.rar. default.r00 default.r01 and so on not like archive manager where it makes default.part00.rar default.part01.rar and so on.

there you go ppl its fully working thats mysecond version ppl my first version is plain also screenshots above are from the second version i have to sort out the instructions in the text to be more friendly lol.

download the attatchment below extract it and put the rar file in your  ~/.gnome2/nautilus-scripts then make it executable to do this open you home folder hit the right Ctrl + h go into .gnome2/nautilus-scripts right click the rar file the in teh tabs at the top click permissions. click the little box for Execute Allow executing file as program. thats it you should now be able to use it. have fun i do lol

---

### Post by danwood76 on 2008-02-26
could you post it up here as an attatchment?
It sounds like a nice little script.

---

### Post by luckypayal on 2008-05-29
just select all the folders the right-click and select "add to archieve" from winrar options....a dialog box will apear...select files tab and check "put each file to seperate archieve"...and click OK ...here u go....:)

---

### Post by yota on 2008-05-29
This command, executed from the folder where all the 100 dirs are located, should do it:
```

find . -type d -mindepth 1 -maxdepth 1 -exec rar a -r {}.rar {} \;

```
In human language means: find in the current path (.) all directories (type d) recursing at least one level but not more, and for each of them launch "rar a -r <directory name>.rar <directory name>"

It can be made a script too, which has to recieve the base folder as the first argument.
```

#!/bin/bash
if [ "$1" -eq "" ]
then
   echo "Please specify the base directory"
   exit 1
fi
find $1 -type d -mindepth 1 -maxdepth 1 -exec rar a -r {}.rar {} \;

```

Hope this helps

---

### Post by helwitch on 2008-05-29
> **luckypayal said:**
> just select all the folders the right-click and select "add to archieve" from winrar options....a dialog box will apear...select files tab and check "put each file to seperate archieve"...and click OK ...here u go....:)
....That only works on windows. This is an Ubuntu forum.

---

### Post by helwitch on 2008-05-29
Thanks Yota, I'll give that a shot!

---

### Post by executive on 2008-06-23
> **luckypayal said:**
> just Select All The Folders The Right-click And Select "add To Archieve" From Winrar Options....a Dialog Box Will Apear...select Files Tab And Check "put Each File To Seperate Archieve"...and Click Ok ...here U Go....:)



Lol..

---

