---
title: "segmentation fault due to qt4/5 in digikam"
date: 2015-04-16
forum: General Help
---

### Post by jazzvibes on 2015-04-16
Hi all

I've posted my question in a few places but yet to get any real advice.
Here is the current state of the question on askubuntu 
[http://askubuntu.com/questions/606572/programdigikam-chooses-wrong-qt-lib-and-crashes](http://askubuntu.com/questions/606572/programdigikam-chooses-wrong-qt-lib-and-crashes)

Essentially I have all the qt libraries installed from the official repos yet digikam crashes. After doing a little investigation using gdb I received feedback from the Digikam mailing list that the problem is not theirs as my machine is loading a qt5 library when digikam is written to use qt4. 

I'm really at a loss at how to fix this problem. Any help is greatly appreciated and if you answer the question on askubuntu over the next 3 days, you'll get a bonus 50 reputation points :)

Thanks again

---

### Post by dino99 on 2015-04-16
then send a launchpad's report to request a fix.
as i see from synaptic, digikam 4.7 use libqt4, so if the required libqt4 packages are installed, it should load them; check them first before bug report.

---

### Post by pmi2 on 2015-04-16
On askubuntu, you wrote, > I run Ubuntu 14.04 64bit. Digikam used to work but recently stopped working. This is similar to other reviews of the program, for example in Ubuntu Software Center,

> Excelent software... but too buggy in Ubuntu 14.04!

This is a great image and video management software.  It worked like a charm in ubuntu 12.04, but in 14.04 it crashes so often that it may become hardly usable because you never know when will it crash (although previewing two videos on a row fails almost always...),  and even a simple click on another album may crash it! Sometimes I manage to work for 15 minutes, but normally the average time has been much less than that! I even tried the version 4.1 from another PPA, but it is the same! It is indeed a pity. I hope that developers fix this soon, or I will stop using it and keep looking for alternatives, which is not easy due to the overwhelming set of features that Digikam has, but I will probably have to conform with less versatile solutions.This is one of many similar (select "Newest First" in the dropdown box) reviews. Pretty much the reason why I decided not to run it in Ubuntu 14.04, at least not for now, even though it is one of the programs I was looking forward to using in this distribution... :(

I doubt if there is anything you can do, until the developers fix some of these issues.  Only solution if it is really important to you would be to run 12.04.

---

### Post by jazzvibes on 2015-06-02
I still haven't managed to fix this issue. 

I'm fairly sure its something to do with the qt4 and qt5 installations on my computer, but reinstalling everything on apt doesn't seem to help...

Can anybody help diagnose the problem?

---

