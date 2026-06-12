---
title: "Printing to PDF"
date: 2013-07-04
forum: General Help
---

### Post by KWS48 on 2013-07-04
Recently I updated to the newest version of Ubuntu.  Well, now I am having problems.  Seems every time I update, something stops working!  

I was always able to go to File/Print/print to file (pdf or postscript )  Now when I try to do this, my laptop still goes thru the motions.  Drop down menu works, printer dialog box opens.  I can click on "print", it shows a progress dialog but then when I go to my desktop folder  --- nothing is there!

I have no idea what is wrong.  This happened once before and by total accident it started working( nothing Ubuntu Forums suggested did any good ) I suddenly was able to print **TO** pdf files. In an earlier thread, people misunderstood what I was saying.  [COLOR=#ff0000]I can print pdf files.[/COLOR]  I just can't print [COLOR=#ff0000]AS[/COLOR] a pdf file ( to one of my folders ).   Evidently something is missing.  I have both cups and hplip installed.  I have no idea what is missing.  I'm not a newbee to Ubuntu been using it for six years!  However I am not a computer geek.  I know the basics, but am not a programmer.  I can follow instructions if someone gives them.  I know I cannot expect perfection, when something is free for all to use.  I do like it when things work however.  Printing to file for me, seems like a basic function.  I also had problems at first printing pages, but now that works fine.  So I guess my question is, why can I print out a page, but not print it to file?:confused:  This is the only way I can save my bank statements ( the bank only offers them in Microsoft Money format ) and also sometimes I like to save a page for future reference.  This is what I use that option for.  I would post screenshots, but evidently drop down menus etc, do not show in screenshots.

Please do not reply with smart remarks.  Too many times here on Ubuntu I get condescending remarks. Maybe it's the age thing, but I really have no use for smart alecs!

---

### Post by DJ_Max on 2013-07-04
I'm not a computer geek either, but running 13.04 PDF's are saved in ~/PDF

---

### Post by kurt18947 on 2013-07-05
Perhaps  the resulting .pdf files are being placed somewhere other than where you're expecting?   I *think* by default they're placed in the user's directory.  You'd need to specify Desktop, Documents or where ever.

---

### Post by sudodus on 2013-07-05
```
sudo find * -ctime -1 -type f
```

will show all the regular files at the current directory and in subdirectories, that were created within the last day (24 hours).

So if you open a terminal window at your home directory and run that command, you are likely to find your pdf file (which may or may not have the pdf extension).

---

### Post by andrew.46 on 2013-07-05
> **KWS48 said:**
>  I would post screenshots, but evidently drop down menus etc, do not show in screenshots.

Try doing this with Gimp, I attach a screenshot to demonstrate. I have taken a full screen snapshot and asked to include the mouse pointer, Cropped the final image and there it is...

---

### Post by KWS48 on 2013-07-15
OK, thank you!
I found my missing pdf files.  As someone mentioned they are in pdf which I only found when I clicked on View/Hidden Files.  Never thought to do that.  Duh!  However that does bring up something else which I will post another thread on.  The fact that in 13.04 there is no search files feature!  Or if it's there somewhere it's not showing anywhere!

---

### Post by KWS48 on 2013-07-15
How do I mark this SOLVED?

---

### Post by pqwoerituytrueiwoq on 2013-07-15
edit the 1st post go to advanced and change the prefix (where you pick ubuntu/ubuntu/kubuntu/etc)

---

