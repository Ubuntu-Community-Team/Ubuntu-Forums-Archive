---
title: "i used newsleecher in win.  make or break distro habit.  whats *best binary reader ?"
date: 2007-05-23
forum: General Help
---

### Post by kraymore on 2007-05-23
i used newsleecher in win.  make or break distro habit.  whats *best binary reader  ?

i'm using feisty.  pan isn't good enough for me.

---

### Post by thehuman on 2007-05-23
Hellanzb all the way. It's all command line, but it downloads, checks/repairs via .par2 files, and unpacks from zipped archives all just by feeding it an nzb file. You will wonder how you ever got by with Newsleecher. That was my big reservation about leaving Windows as well. I will try to find the tutorial I used to install it...

edit:
[Hellanzb installation.]("http://www.ubuntugeek.com/nzb-par-and-unrar-all-in-one-using-hellanzb.html")

Have fun. Downloading from newsgroups is so much easier with Hellanzb.

---

### Post by DoktorSeven on 2007-05-23
Might also try klibido (it's in the Universe repositories), it's a GUI and concentrates on binary downloads unlike Pan which does both text and binary.

---

### Post by robertpolson on 2007-05-23
How can I control klibido font size in gnome? It is a KDE program, how can I adjust the font size ?

---

### Post by DoktorSeven on 2007-05-23
I don't know any way to set KDE font size other than KDE Control Center which is in the **kcontrol** package, but installing that will probably pull 3/4 of the rest of KDE in with it...

---

### Post by kraymore on 2007-05-24
i tried klibido last night and i found that simply clicking on a link once would cause it to want to open in another tab.  i found this gravely annoying depsite fixing my preferences.  i dont know if it needs a restart or not.  hopefully thats all it will take.  one thing i am curious of if there is a website equivalent of newsleechers supersearch ?  anyway any tips on optimizing klibido for typical gnome users would be nice.  the download on single click i dont like.  also the one album i did grab.. it had mp3.1 and mp3s next to each numbered file name.  any ideas on that one as well ?  i might try the command line hellnzb if only i knew how to get my terminal to resolve at 1024x768.  

thank you

---

### Post by robertpolson on 2007-05-25
Newsgroups are very easy on Linux. Much easier than on Windows.

All you need is :

1) Go here and read the comment by sizzam 
[http://ubuntuforums.org/showthread.php?t=169749&page=16&highlight=hellanzb](http://ubuntuforums.org/showthread.php?t=169749&page=16&highlight=hellanzb)

2) Get your nzb from newzbin.com 


One click and you are done. 

There is also a great newsgroups provider that is only $13.95 for unlimited newsgroups. P.M. me if you are interested.

---

### Post by teknosexual on 2007-06-01
> **kraymore said:**
> i tried klibido last night and i found that simply clicking on a link once would cause it to want to open in another tab.  i found this gravely annoying depsite fixing my preferences.  i dont know if it needs a restart or not.  hopefully thats all it will take.  one thing i am curious of if there is a website equivalent of newsleechers supersearch ?  anyway any tips on optimizing klibido for typical gnome users would be nice.  the download on single click i dont like.  also the one album i did grab.. it had mp3.1 and mp3s next to each numbered file name.  any ideas on that one as well ?  i might try the command line hellnzb if only i knew how to get my terminal to resolve at 1024x768.  

klibido is a very easy transition from Newsleecher. Since it is a KDE application however, it is single-click by nature. If you don't want tabs, just change that option in the settings menu. Settings > Configure klibido > View > Check "View files in one tab".

You can find nzb's at [http://binsearch.info](http://binsearch.info) or [http://alt.binaries.nl](http://alt.binaries.nl) and many other places.

For par2 support, install **par2** via Synaptic. It is a command line program, but very easy to use. Once it's installed, just type "par2" in the terminal (click maximize if you want your terminal window larger btw). That will bring up a list of commands and options. Basically, just navigate (cd) to the directory where your files are, then type par2verify "filename.par2". And of course, use par2repair "filename.mp3" to repair damaged files.

---

### Post by the100thmonkey on 2007-06-01
> **kraymore said:**
> i used newsleecher in win.  make or break distro habit.  whats *best binary reader  ?

i'm using feisty.  pan isn't good enough for me.i'm another HellaNZB fan. it really is good - i think it's around five clicks to get something downloaded. it's great.

---

