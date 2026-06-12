---
title: "[SOLVED] select default OS in Grub"
date: 2007-09-07
forum: General Help
---

### Post by Russty of Oz on 2007-09-07
I have just reinstalled Feisty and previously I used something to change the default os at startup but I can't find it now.  I have searched the forum and found a way to do this by using the terminal and editing grub, but before I used something in either the preferences or administration where I could change the default os, choose how many Ubuntu kernels are shown and change the background of the Grub menu.

Can anyone suggest what I used and where to find it?

Russty.

---

### Post by aJayRoo on 2007-09-07
It sounds like you are referring to GrubEd or GrubConf. I think it is probably GrubConf that you want though, you can find it [here](http://grubconf.sourceforge.net/). Take a look and see if it is what you want. Hope that helps.

---

### Post by Russty of Oz on 2007-09-07
That looks similar to what I used before, but I didn't actually install anything that I can remember, I thought it was already in Ubuntu.  However, I downloaded that and tried to install but when I got to the "make" command I got this error:

make[2]: *** [partitioning.o] Error 1
make[2]: Leaving directory `/home/russty/Desktop/grubconf-0.5.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/russty/Desktop/grubconf-0.5.1'
make: *** [all-recursive-am] Error 2
russty@russty-desktop:~/Desktop/grubconf-0.5.1$ 


What is an "all-recursive" error??  

Russty

---

### Post by aJayRoo on 2007-09-07
Actually I just realised how old GrubConf is! Perhaps it isn't what you or I were thinking of. Now I am annoyed that I can't remember what tool it is I used before to alter the grub menu! I think you might want to try GrubEd, it seems that it is still being updated, check out [this](http://ubuntuforums.org/showthread.php?t=228104) thread. On a side note I can't even get the configure script of GrubConf to work... it doesn't give an error it just stops in the middle for no reason! Sorry for leading you down the wrong path!

---

### Post by AndyCooll on 2007-09-07
You could always manually edit the menu.list file, or are you specifically looking for a gui approach?

:cool:

---

### Post by AlexenderReez on 2007-09-07
hm...use startup manager

[http://www.getdeb.net/search.php?keywords=startup+manager](http://www.getdeb.net/search.php?keywords=startup+manager)

---

### Post by Russty of Oz on 2007-09-07
> **AlexenderReez said:**
> hm...use startup manager

[http://www.getdeb.net/search.php?keywords=startup+manager](http://www.getdeb.net/search.php?keywords=startup+manager)

YES!  That was it.  I don't remember installing it before, but I guess I must have.  

Thanks for finding what I wanted, and thanks to the others for their help also.

Russty. :)

---

