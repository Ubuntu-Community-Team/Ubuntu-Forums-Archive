---
title: "Can someone help me with a shell script?"
date: 2013-07-14
forum: General Help
---

### Post by jigsaw2012 on 2013-07-14
Hi, I am fairly new to Linux, but i need it for my job. I need to work on a program, but every time i want to use that program i need to type in some commands in the terminal, i was wondering if i can create a shell script so i don't have to type them every time?, but just click a file and run them?

The commands i needs to type in are : 

cd Documents
export path=$path:/home/jigsaw/Documents/mira_3.9.18_linux-gnu_x86_64_static/scripts/
export path=$path:/home/jigsaw/Documents/mira_3.9.18_linux-gnu_x86_64_static/bin/
export path=$path:/home/jigsaw/Documents/3rdparty/

Can someone help me with this?

---

### Post by oldfred on 2013-07-14
Welcome to the forums.

I am no expert on scripting, but what I have done to learn was just copying some commands from history into a file, edit to fix the typos and add the header and change it to executable.

I make this the first line, I like to make second line the file name.

#!/bin/bash
# filename.sh

       Lots of links on scripting in this thread
[http://ubuntuforums.org/showthread.php?t=1893106](http://ubuntuforums.org/showthread.php?t=1893106)

 [http://www.gnu.org/software/bash/manual/html_node/index.html](http://www.gnu.org/software/bash/manual/html_node/index.html)
Pitfalls often spaces in file names:
[http://mywiki.wooledge.org/BashPitfalls#cp_.24file_.24target](http://mywiki.wooledge.org/BashPitfalls#cp_.24file_.24target)
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)


 Note that it is a good idea to put your scripts in one place, so you can run them without requiring a path. If you create a bin directory in your home ( mkdir ~/bin ) the next time you login, that will automatically be included in your PATH. Then you could make a panel or desktop launcher as "Application in Terminal" to run your script with a click or double click of the mouse.

      
 chmod 755 ~/bin/filename.sh

---

### Post by Cheesemill on 2013-07-14
The 3 export lines can be turned into 1 and added to your .bashrc file which lives in your home folder.

Fire up gedit and open your ~/.bashrc file (files that begin with a . are hidden so you will have to hit CTRL+H to see them).
Add the following line to the bottom of the file and save
```
export PATH=$PATH:/home/jigsaw/Documents/mira_3.9.18_linux-gnu_x86_64_static/scripts:/home/jigsaw/Documents/mira_3.9.18_linux-gnu_x86_64_static/bin:/home/jigsaw/Documents/3rdparty
```

Your .bashrc file gets run automatically every time you open a terminal, so you won't need to enter them manually any more.

---

