---
title: "Main Menu startup delay very annoying"
date: 2008-05-04
forum: General Help
---

### Post by peakpc on 2008-05-04
Has anyone else noticed that if you use the _main menu_(the one without App's,places,system), when you first start your computer or log in to gnome, there is a couple seconds (sometimes as much as 10) delay between when you click on the icon and when the menu appears. I assume this is because it is loading the menu and icons into memory. After the first time, it loads up instantaneously (so must be cached). Is there a way to cause the menu and its icons to always be loaded into memory when you log into gnome - so you don't have the delay later when you click on the main menu. This is very annoying.

If I put the Menu Bar back on the panel (the one with App's,places,system) then both menus have little or no delay, but I don't like the Menu bar as it takes up sooo much panel space and with changing backgrounds I can't always read the words anyway (panel set translucent).

I have searched everywhere for some cashing code, tried some things that are suppose to speed up menus but they don't fix this.

---

### Post by djs_uk on 2008-05-04
Yep... I find this totally annoying too. 

I've recently upgrading my memory from 0.5GB to 2GB, and I'm noticing much much less.

---

### Post by peakpc on 2008-05-05
Well it's good to know I'm not totally alone.  I'm running 1gb in my laptop, but I don't think it's a hardware issue. That would be Kind of the Microsoft way out of poorly implemented code. 

Thanks for the input though

---

### Post by peakpc on 2008-05-17
I guess I really am alone on this one, well I'll keep working on it with my limited understanding of how things work...who knows...maybe I will learn something new and share it.   I would take any help I can get though!

---

### Post by peakpc on 2008-06-14
For all who stumble across this thread I found a reasonable way to use the menu-bar and not take up so much panel here [http://ubuntuforums.org/showthread.php?t=89136&highlight=Possible+to+change+%26quot%3B%26quot%3BApplications-Places-System%26quot%3B%26quot%3B+menu%3F&page=2]("http://ubuntuforums.org/showthread.php?t=89136&highlight=Possible+to+change+%26quot%3B%26quot%3BApplications-Places-System%26quot%3B%26quot%3B+menu%3F&page=2") it works for me! and there is no noticeable delay on the first click of the menu!!!!:)

---

### Post by Genius314 on 2008-06-14
I also noticed the delay, and it's really annoying.

I don't like the separate menus, though, and not just because of the space they take up. I like to just have one menu.

---

### Post by DaymItzJack on 2008-06-14
Have you tried installing readahead? I'm pretty sure it was made for stuff like this.

---

### Post by iolapiu on 2009-04-26
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/12040/comments/32](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/12040/comments/32)

:guitar:

---

### Post by peakpc on 2009-04-26
I had hoped that they (Gnome) would address this bug in some revision.:(..I hope that these work arounds help others like me that don't care for the way the default menu is. (see my previous post for my fav:))

---

### Post by oakgrove on 2009-09-06
If you make a drawer on the panel somewhere and put the regular "applications | places | system" menu in it to hide it away, just by virtue of that being cached when Gnome starts, your main menu will be cached too and open up much more snappily.  Why having the bar loaded causes it all to be cached and the main menu by itself doesn't, I don't know, but this terrible hack actually does work.

---

### Post by peakpc on 2009-09-07
Thanks Oakgrove this is a very valid workaround though now I've grown use to my shortened "Apps,Goto,Sys" it's not as big of an annoyance as it once was.  I would still like to see it fixed to give us more flexibility.

---

### Post by peakpc on 2009-11-05
I just loaded Karmic and as one of my standard tweaks I move everything to one panel to save space. Again I used [http://ubuntuforums.org/showthread.php?t=89136&highlight=Possible+to+change+%26quot%3B%26quot%3BApplications-Places-System%26quot%3B%26quot%3B+menu%3F&page=2]("http://ubuntuforums.org/showthread.php?t=89136&highlight=Possible+to+change+%26quot%3B%26quot%3BApplications-Places-System%26quot%3B%26quot%3B+menu%3F&page=2") to condense the menubar to a reasonable size and it works flawlessly.:D

---

### Post by oakgrove on 2009-12-04
Excellent.  I really needed this as, don't ask but I regularly run my desktop at 1600x1200 and at other times 800x600 and the regular menubar is HUGE at the low res.  I tried this method in Debian Lenny a few weeks back and it didn't work but I'm running Karmic on the desktop now and it works great.

---

### Post by Topazgb on 2010-08-27
> **oakgrove said:**
> If you make a drawer on the panel somewhere and put the regular "applications | places | system" menu in it to hide it away, just by virtue of that being cached when Gnome starts, your main menu will be cached too and open up much more snappily.  Why having the bar loaded causes it all to be cached and the main menu by itself doesn't, I don't know, but this terrible hack actually does work.

Yes that works well but how is the drawer hidden ?


Edit
The problem now seems to have been fixed.

---

