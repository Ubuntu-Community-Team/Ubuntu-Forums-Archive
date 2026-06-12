---
title: "looking for a video screen capture program"
date: 2005-07-27
forum: General Help
---

### Post by ^NoX on 2005-07-27
where can i find it? all the programs that i know can only do 1 screen shot, and i need a 10 minutes video.
anyone can help? thanx alot :)

---

### Post by SFN on 2005-07-27
You want xvidcap.

[http://prdownloads.sourceforge.net/xvidcap/xvidcap_1.1.2-1_i386_testing.deb?download](http://prdownloads.sourceforge.net/xvidcap/xvidcap_1.1.2-1_i386_testing.deb?download)

Once you have that, just do:

```
sudo dpkg -i xvidcap_1.1.2-1_i386_testing.deb
``` 

For a more recent version get:

[http://rpm.pbone.net/index.php3/stat/4/idpl/1137200/com/xvidcap-1.1.3-2.i386.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/1137200/com/xvidcap-1.1.3-2.i386.rpm.html) 

Then do a

```
sudo alien --to-deb xvidcap-1.1.3-2.i386.rpm
``` 

and

```
sudo dpkg -i xvidcap_1.1.3-3_i386.deb
```

To run it, just type xvidcap at the prompt. That may cause your machine to complain that it can't find libpng.so.2. If so, do

```
sudo apt-get install libpng2
``` 

Once it's open, you'll see the xvidcap toolbar and a little red box. That red box indicates what area will be captured. You'll almost certanly want to resize it. To do that, click the button that looks like a circle with a cross through it. Then use your mouse to drag across the area you wish to capture. Once you've done that, click the record button (little red dot). When you're done recording, click the stop button (little black square).

It may complain a bit more about settings. Those can be changed by clicking File, then Options.

There's more to it than that but that should get you started.

---

### Post by ^NoX on 2005-07-27
i just don`t know what to say, so ill just start at:
**THANK YOU VERY VERY MUCH FOR YOUR TIME!!!** 

thank you, thank you, and thanx again for everything :)  :grin:  :grin:  :grin:  :grin:

---

### Post by SFN on 2005-07-27
Wow. No problem.

Just remember when you get good with something to offer the same kind of help to others.

---

### Post by hod139 on 2005-07-27
These two sites are really useful for video capture
[http://wiki.vislab.usyd.edu.au/moinwiki/VideoCreationGuide](http://wiki.vislab.usyd.edu.au/moinwiki/VideoCreationGuide)
and
[http://wiki.vislab.usyd.edu.au/moinwiki/MakingVideoTutorials](http://wiki.vislab.usyd.edu.au/moinwiki/MakingVideoTutorials)

---

### Post by Craftycorner on 2006-10-10
I googled up this.

[http://business.newsforge.com/article.pl?sid=06/07/20/1918210&tid=35](http://business.newsforge.com/article.pl?sid=06/07/20/1918210&tid=35)

---

### Post by Craftycorner on 2006-10-15
I successfully installed via SFN's instructions xvidcap  according to the text on my machine using

sudo dpkg -i xvidcap_1.1.2-1_i386_testing.deb

cuz the other site was down.  But the program disapeared...I can't find it.

---

### Post by Craftycorner on 2006-10-15
> **Craftycorner said:**
> I successfully installed via SFN's instructions xvidcap  according to the text on my machine using

sudo dpkg -i xvidcap_1.1.2-1_i386_testing.deb

cuz the other site was down.  But the program disapeared...I can't find it.

Here is a pic of the code in question of the install...

[http://img213.imageshack.us/my.php?image=3696bt5.png](http://img213.imageshack.us/my.php?image=3696bt5.png)

---

### Post by chikko on 2007-02-15
here's a newer version - debbian :)

[http://sourceforge.net/project/downloading.php?group_id=81535&use_mirror=heanet&filename=xvidcap_1.1.5rc1_i386.deb&27116804](http://sourceforge.net/project/downloading.php?group_id=81535&use_mirror=heanet&filename=xvidcap_1.1.5rc1_i386.deb&27116804)

---

