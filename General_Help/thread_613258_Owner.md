---
title: "Owner?"
date: 2007-11-14
forum: General Help
---

### Post by Jim Lewis on 2007-11-14
OK.  I've read the other "owner" related files and my mind is reeling.

I downloaded a plugin -- the "Totem Browser."  I don't care for it at all and want to zap it because it somehow thinks it is THE application for showing videos.  There's a "Movie Player" on my system that I'd rather use.

I found the directory/folder that it is in, but have the same problem the others have in that I'm not the owner.

Can I create a "launcher" as one of the old "owner" threads suggested and simply pull that folder into it then click on "properties" and make it go away?

I'm so new at Linux I'm tiptoeing everywhere for fear of messing things up.

Help will be appreciated.

---

### Post by madcow72 on 2007-11-14
It sounds like all you need to do is to uninstall totem-browser.  The GUI way to do this is to go to System->Administration->Synaptic Package Manager.  You will be required to enter your password, and then a window that manages all of your programs will appear. 
Click the "Search" button up top.
Type in "totem" and hit enter.  Then you will see a variety of packages appear in the main window.  Some of them have green boxes (these are already installed on your system) and some have clear boxes next to 'em.  Click on the green box next to the "totem" package, and then choose "Mark for Removal."
After than, click the "Apply" button up top.  

That's it!  Synaptic will remove the package and other packages associated with it that are no longer needed.

Now, a bit of philosophy:  Don't be afraid to break your computer!  The best way to learn about your computer and your OS is to break it from time to time, and then learn how to fix it.  Honestly, it's getting more and more difficult to "break" Ubuntu anyway, but even if you do, it only takes about 20-25 minutes to put back together from scratch!

Hope this helps!

---

### Post by dpar on 2007-11-14
The reason you have 'ownership' problems is because you can't install or uninstall to a root directory without administrator permission. madcow72 is right, the easiest way is to use Synaptic.

---

### Post by mikewhatever on 2007-11-14
Can you specify where that directory/folder is in the filesystem. Post something like /media/mountpoit/....

---

### Post by Jim Lewis on 2007-11-14
Many thanks.  I usually look for the hardest way first.  :)

---

