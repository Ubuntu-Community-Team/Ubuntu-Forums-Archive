---
title: "OOo Documents Won't Open after upgrade to Hardy"
date: 2008-06-21
forum: General Help
---

### Post by varaonaid on 2008-06-21
Hello,

I'm having a problem that I can't seem to solve.  I upgraded to Hardy today (a less than painless procedure, unfortunately) and now, I no longer have any OpenOffice icons and when I click on a OOo file (be it an odt, ods, doesn't matter) it refuses to open.  If I click "open with" on the right click menu, no difference.  I can open OOo 2.4 from the main menu, navigate to the file under "open" and it will open the files just fine so there isn't any corruption in the files themselves.

I tried a reinstall of OOo through synaptic and then I removed writer and reinstalled.  No change.  Strangely, when I uninstalled writer, it still showed up on the main menu.  

In terms of addressing the icon problem, I searched and found that I needed to install the OO styles packages and did so.  Didn't fix the problem, even after a full restart.  I also tried switching back to the "human" icon theme and that didn't fix it either.

So, I think somewhere along the line during the upgrade, OOo got completely screwed up.  What should I do to fix it?  I've got to have it working. 

Any help you could give would be awesome.  Thanks in advance...

Rae

---

### Post by ctw on 2008-06-21
I have the same problem too.:(

---

### Post by varaonaid on 2008-06-23
Any ideas?

---

### Post by ctw on 2008-06-23
Try to do this: 

[http://ubuntuforums.org/showthread.php?t=835630](http://ubuntuforums.org/showthread.php?t=835630)



Remove all openoffice packages:-
Code:

sudo apt-get purge openoffice.org*

Then reinstall the whole suite
Code:

sudo apt-get install openoffice.org







for me it works.

Bye

---

### Post by varaonaid on 2008-06-24
Thanks so much for taking the time to reply.  Unfortunately, it didn't work for me.  Tried it twice, too. :(

Anyone have any other thoughts?

---

