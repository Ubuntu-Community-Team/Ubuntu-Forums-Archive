---
title: "Windows has &quot;windows/system32/&quot; what does ubuntu have?"
date: 2008-05-23
forum: General Help
---

### Post by jellylogix on 2008-05-23
in windows you can go to command prompt (terminal for ubuntu) and type something like sol.exe and up pops solitare... this file is in the system32 folder and thats what windows checks when you do not specify a directory. In Ubuntu you can also do this, typing something like "blender" and up will "pop" blender 3D animation software. i was wondering if Ubuntu has a "program folder" that has all these programs in. and if so, What is it? 

-Ryan

---

### Post by VMC on 2008-05-23
> **jellylogix said:**
> in windows you can go to command prompt (terminal for ubuntu) and type something like sol.exe and up pops solitare... this file is in the system32 folder and thats what windows checks when you do not specify a directory. In Ubuntu you can also do this, typing something like "blender" and up will "pop" blender 3D animation software. i was wondering if Ubuntu has a "program folder" that has all these programs in. and if so, What is it? 

-Ryan
Here's where mine goes when I type a command. If that's what your asking. You can add to the command path
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by jellylogix on 2008-05-23
I'm sorry but I'm really new... what exactly does that mean? does that mean that "/usr/local/sbin:"   is one of the directories that it checks...?

---

### Post by VMC on 2008-05-23
> **jellylogix said:**
> I'm sorry but I'm really new... what exactly does that mean? does that mean that "/usr/local/sbin:"   is one of the directories that it checks...?

See the ":" colon? Each colon is what separates the directories. He passes your command to the first directory, and if not found to the second, etc.

---

### Post by jellylogix on 2008-05-23
OH OK! thanks that explains a lot and narrows down my search a great deal. 

Thanks!

-Ryan

---

### Post by VMC on 2008-05-23
For example, here is a command to find commands:

$ whereis ls
ls: /bin/ls /usr/share/man/man1/ls.1.gz

Do you see the command ls is found at /bin directory , the 6th directory I showed that were separated by ":". Get it?

---

### Post by jellylogix on 2008-05-23
you may have just answered 2 vital questions that i have been wondering for a while. i ran the command "whereis blender" and it gave me this

$ whereis blender
blender: /usr/bin/blender /usr/lib/blender /usr/share/blender 
/usr/share/man/man1/blender.1.gz

so the first bit of information it gave me was directories that contained the string "blender" and the second/final peice of information was an actual program that it gave... "blender.1.gz" does that mean programs in Ubuntu are in the extension ".1.gz"

and a final question related to extension is "How can I see these extensions on the end of all my files?"

---

### Post by y-lee on 2008-05-23
Linux doesn't use file extensions the same way windows does. Some executable files in linux end in .bin some in .sh but some have no extension.

Considering it's location blender.1.gz is a [man page]("http://en.wikipedia.org/wiki/Man_pages"), not the executable file.

The [gz part]("http://en.wikipedia.org/wiki/Gzip") means this file is compressed.

---

### Post by jellylogix on 2008-05-23
whoa... thats really confusing... so how does linux know how to open these files with no extensions... does it guess?

---

### Post by y-lee on 2008-05-23
As i understand it information on what type a file is is stored with the file in some way.

---

### Post by jellylogix on 2008-05-23
wow thats a really non-user friendly idea... they should have some sort of program that will grab this data from each file, read it and then virtually put extensions on the files so that us humans know what the heck the file is!... or I can stop complaining and go back to Vista.. BLAH!

---

### Post by y-lee on 2008-05-23
I don't really understand what is not friendly about it. you can right click a file and then choose properties. Click on the permissions tab and tell if it is executable or click on open with to see what program opens it. Most of the time you can just double click a file and it will do what it is supposed to do. Linux is not windows or ms/dos so there are differences in the way it does things and in the way it handles things. Once you adapt to it you will find it makes sense in its own kind of way.

---

### Post by jellylogix on 2008-05-23
ya i totally agree with you. It may seem totally different and weird right now, but if I orignally learned linux as my main OS then I would have a totally different perspective on things, probably even thinking that the windows concept of file extensions was "dumb" or useless... just my overall perspective on thigns right now... but they will change over time, and as I learn more about Linux. Thanks for all the help, I now have a better understanding on how the files are used in linux... haha up next "finding out what the heck all those /usr, /etc, /lib folders are.. haha!

Thanks

-Ryan

---

### Post by RequinB4 on 2008-05-23
> **jellylogix said:**
> whoa... thats really confusing... so how does linux know how to open these files with no extensions... does it guess?

File extensions can be meaningless - it all depends on the MIME type (file type, bascially).  Ubuntu is smart enough to tell the difference between a specific audio file and a executable, for example.  This feature is especially useful when scripting.

Edit:  In answer to your next post, [http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/)

---

### Post by Frak on 2008-05-23
> **jellylogix said:**
> wow thats a really non-user friendly idea... they should have some sort of program that will grab this data from each file, read it and then virtually put extensions on the files so that us humans know what the heck the file is!... or I can stop complaining and go back to Vista.. BLAH!
Why waste space on extensions when it can just read the internal MIME type.

Mac OS X does this too.

---

