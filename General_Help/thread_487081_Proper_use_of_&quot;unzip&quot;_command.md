---
title: "Proper use of &quot;unzip&quot; command"
date: 2007-06-28
forum: General Help
---

### Post by FlyingIsFun1217 on 2007-06-28
Hey!

Me again! This time I'm trying to use the command line to unzip a file. I've found that I need to use the command "unzip file.zip". But lets say that I want to extract the contents to a folder named Test on my Desktop. So I should type:

> unzip /home/usr/Desktop/Test/Test.zip

...and that should unzip it there, right? And if I want to unzip it somewhere else, I would use:

> unsip /home/usr/Desktop/Test/Test.zip -x /home/usr/Desktop/OtherFolder/

...right? Then how come it doesn't work?

Thanks!
FlyingIsFun1217

---

### Post by stchman on 2007-06-28
> **FlyingIsFun1217 said:**
> Hey!

Me again! This time I'm trying to use the command line to unzip a file. I've found that I need to use the command "unzip file.zip". But lets say that I want to extract the contents to a folder named Test on my Desktop. So I should type:



...and that should unzip it there, right? And if I want to unzip it somewhere else, I would use:



...right? Then how come it doesn't work?

Thanks!
FlyingIsFun1217

Use the -d switch, this tells unzip that you want to extract the contents to a different folder.  Lets say you have files.zip in /home/joe/stuff and you want to unzip files.zip into /usr/local/bin/stuff

unzip -d /usr/local/bin/stuff /home/joe/stuff/files.zip

Hope this helps.

---

### Post by FlyingIsFun1217 on 2007-06-28
Thanks so much for your help!

FlyingIsFun1217

---

