---
title: "Need help with writing script for ubuntu"
date: 2015-12-09
forum: General Help
---

### Post by nzdreamer55 on 2015-12-09
Hello everyone,

I am new to Linux and have little computer working knowledge.  I have put together a raspberry pi and I want it to do some file organization.  I use a program that is written in java and works via the command line (terminal).  Now I run it in windows via the command line and a .bat file.  I have installed it on my raspberry and it seems to work (I only had it give me it's version number) when I use it via the terminal window.

Here is the scenario.  Files are put into a folder with cryptic names.  The program filebot then takes the files renames them and moves them to their proper spots.  I would like to write a script that handed each file to filebot, one at a time, let filebot work on it and then when it was done move to the next file in the folder until they were all finished.  Under windows, I put in a folder where the files would be and filebot worked on them all at once which lead to some problems.  So here is what the windows code looked like
```
filebot -script fn:amc "D:/TV"
```

So I think that I need to put some sort of variable into the area where "D:/TV" is and design a for next loop to fill this variable with the names of files in the source folder.  Does this sound correct and where do I start?

Thanks

---

