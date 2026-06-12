---
title: "How do I reset XChat colors under Ubuntu Hoary"
date: 2005-04-22
forum: General Help
---

### Post by occy on 2005-04-22
Hello everyone,

I'm trying to figure out how to get default XChat colors that come with the actual application. 

Someone, xchat - ubuntu packager?, decided to change the default colors, and I'm not partial to them.  

Did they compile these colors in to the application?  If so, isn't that a bad thing?

If anyone could tell me howto fix this, I'd appreciate it.

Thanks in advance for your time,
Trae

---

### Post by occy on 2005-04-22
Well, 

I found out how to fix the problem more or less and decided to post the answer here in case someone else wanted to know.

SImply do the following:

Open a Terminal and type: wget [http://www.xchat.org/files/themes/blacktheme.zip](http://www.xchat.org/files/themes/blacktheme.zip)

unzip the file, and then stick the *.conf files in ~/.xchat2/ 

Exit XChat and restart it.

Poof.  

Enjoy.
Trae

---

