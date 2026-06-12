---
title: "Why can't I make a launcher on my desktop correctly?"
date: 2007-10-30
forum: General Help
---

### Post by mmilitia9 on 2007-10-30
Hey everyone.  I installed IE4Linux awhile back for my active x needs.  Anyway, my launch icon vanished the other day.

I can still run IE6 if I open a terminal and type ie6.  It opens just fine.  But how come my icons vanished?  I thought by reinstalling it would solve the problem.. but it didn't.

Soo.. I figured it would be as simple as.. Right clicking the desktop, Create Launcher, and put "ie6" in the command.. that didn't work. 

 I get this error message.. when I make the launcher and click it. [http://img145.imageshack.us/img145/6360/errorcg7.png](http://img145.imageshack.us/img145/6360/errorcg7.png)


What should I do to make a shortcut for IE6?

thanks,

Dom

---

### Post by Green_Star on 2007-10-30
I can suggest correctly when I am at my computer, but mean while you can try by creating a launcher with following command.

wine "C:\Progra~1 <rest of the path to internet explorer exe>"

good luck

---

### Post by mmilitia9 on 2007-10-30
Aye... that's kind of difficult for me to follow...  Does that put a shortcut onto the desktop or something?

---

### Post by zvacet on 2007-10-30
In launcher on the right from command box is search botton.Click on it and browse file system to find exe you need.In this case is in your home folder under hidden files.There is .wine folder and in it is your exe.Sounds complicated but in reality it is very simple.Good luck!

---

### Post by mmilitia9 on 2007-10-30
I tried.. but that doesn't work either.. ugh.. I still get the same error after I make the launcher..

Any more suggestions?

---

### Post by zvacet on 2007-10-31
When you click on search you will see window choose program.Select your home folder.In location bar type ** ~/.** and you will see all your hidden files in your home folder.Select .wine and click on it.You will see content of .wine(dosdevices,drive_c...).Click again on one of them to open it and at the end you will see your exe.When you see it click on the bottom right button **open**.That should do the trick.

---

### Post by nowshining on 2007-10-31
if u don't see .wine right click and select show hidden files if it's not checked.

---

