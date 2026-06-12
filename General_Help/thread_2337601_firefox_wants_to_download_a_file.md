---
title: "firefox wants to download a file"
date: 2016-09-20
forum: General Help
---

### Post by Skaperen on 2016-09-20
*firefox* wants to download a file that ends in *.py*, but i just want to see it.  so i have to download it and view that file.  if i make a duplicate that ends in *.txt* then i can view it directly.  or i can use lynx to view it in a terminal window running a shell.

it has been said (elsewhere, in the past) that it is some *MIME* file type issue.  so that probably explains why this happens on many sites.  can someone explain the *firefox* issue and what to do about it when i don't have control of the web site (how to make *firefox* just display it)?

here are two URLs of the same file.  the first one causes *firefox* to just try to download it.

[http://stratusrelay.com/free/printobject.py](http://stratusrelay.com/free/printobject.py)
[http://stratusrelay.com/free/printobject.py.txt](http://stratusrelay.com/free/printobject.py.txt)

---

### Post by Bucky Ball on 2016-09-20
*Thread moved to **General Help**.*

Better chance of support as not related to ***Desktop Environments***.

Erm, the second link is it. You are looking at the contents of what looks to be the python script that downloads with the first link.

I don't use python but imagine you can view the downloaded file by right-click> open with ...

... and choose a text editor; leafpad, gedit, whatever. If you double-click the file, yes, it will open with whatever app the system believes to be the default for opening files of the type .py

You should also be able to view in a terminal with:

```
nano <path_to_file>
```

... where <path_to_file> = the path and name of your file. If you 'cd' in a terminal to the directory the file is in (Downloads?) then you just need 

```
nano <filename>
```

... where <filename> is the filename.

---

### Post by Skaperen on 2016-09-20
i know i can use these other ways to view files in cases like this but in many cases this is inconvenient.  the firefox developers "dropped the ball" on this.  they should have had another option:  "view this URL in Firefox".

BTW, i have run into this with some other file types, too.  it is not python specific.

both links are to identical files.  i wrote the code in this example.  it is just an example.  i can fix it and/or put it under a different URL.   my question is about how to deal with this on my GUI environment.  sorry for the wrong area.  i am a systems/network person.  all this GUI stuff just all melds together for me.  i'm a very basic user for this ... who has coded a web server in assembly language (a rather useless thing these days).

---

### Post by ajgreeny on 2016-09-20
So go to firefox ->Edit ->Preferences ->Applications, search for py and you will probably see an option to change the default to "Use Mousepad" or "Use Other" or whatever you want to happen.

---

### Post by &amp;KyT$0P# on 2016-09-20
This works in SeaMonkey, don't have Firefox in front of me at the moment so not sure if it would work there
```
view-source:http://stratusrelay.com/free/printobject.py
```

---

