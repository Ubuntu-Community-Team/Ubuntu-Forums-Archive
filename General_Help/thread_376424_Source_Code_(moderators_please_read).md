---
title: "Source Code (moderators please read)"
date: 2007-03-04
forum: General Help
---

### Post by kevanr on 2007-03-04
How can I get the source for Ubuntu, and is it legal to edit some stuff to make it my own? If so, how do I compile it into an iso when I am done?

---

### Post by aysiu on 2007-03-04
If you *really* want the source code, [this post](http://ubuntuforums.org/showthread.php?p=67109#post67109) may help.

But it sounds to me as if you want [Reconstructor](http://reconstructor.aperantis.com/), which is a program that allows you to modify the ISO. That's how [Linux CE](http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/about-ubuntu-christian-edition.html) was made, and I think that's how [Linux Mint](http://linuxmint.com/) was made as well.

And, yes, it's perfectly legal.

---

### Post by kevanr on 2007-03-04
Sweet! Does the reconstructor also allow for a new logo to be used, etc?

---

### Post by llamakc on 2007-03-04
> **kevanr said:**
> Sweet! Does the reconstructor also allow for a new logo to be used, etc?

[http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=29&Itemid=39](http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=29&Itemid=39)

Apparently so. Did you check out the link yet?

---

### Post by kevanr on 2007-03-04
Yes, I did, it has a very nice graphical interface. Is some of it cmd line too or is it just graphical? (I prefer graphical, but it doesn't matter)

---

### Post by kevanr on 2007-03-05
How do you actually install it? Look at the readme.txt file attached to this. I use 6.1 Edgy.

---

### Post by aysiu on 2007-03-05
Download the .deb from [this page](http://reconstructor.aperantis.com/index.php?option=com_remository&Itemid=33&func=fileinfo&id=119) and then double-click it.

---

### Post by kevanr on 2007-03-05
OK-here is what I got:

[http://www.geocities.com/whitehat4u/install.png](http://www.geocities.com/whitehat4u/install.png)

---

### Post by aysiu on 2007-03-05
Looks good. It's installed. 

Now you need an ISO to remaster and you can launch Reconstructor to do the task. I think it needs to be launched as root: ```
kdesu reconstructor
```

---

### Post by kevanr on 2007-03-05
OK-sweet. I have it set up with a launcher that give the command and it just asks for the root password when I start it up.

---

