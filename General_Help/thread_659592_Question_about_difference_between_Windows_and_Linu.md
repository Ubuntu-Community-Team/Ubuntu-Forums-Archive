---
title: "Question about difference between Windows and Linux..."
date: 2008-01-05
forum: General Help
---

### Post by at0myx on 2008-01-05
While using linux now I have noticed that many people recommend to simply remove files using terminal in order to uinstall programs.  However, with Windows, doing this always leaves plenty of files scattered about in your drive and registry changes that can't be undone unless you use the uninstaller (and even then it still sometimes leaves junk on your PC).

Is this something I don't have to worry about anymore with linux?  Do programs run from the directory they were installed in and that's it?  Simply removing that directory (and menu/panel shortcuts) does the job?

---

### Post by yabbadabbadont on 2008-01-05
The short answer is, "not usually".  Sometimes that is enough, but generally not.  Packages installed using the approved methods should be removed using those same methods.  (apt-get, aptitude, synaptic, adept, ...)  Otherwise, strange things may happen.

---

### Post by at0myx on 2008-01-05
What about programs/games/apps installed from discs?

---

### Post by yabbadabbadont on 2008-01-05
How many discs do you have that have native linux games on them?  ;)

A commercial linux game that provides its own installer, usually includes an un-installer too.

---

### Post by NineseveN on 2008-01-06
Follow this thread, it should at least clear out unused and unnecessary dependency files if you have them.
[http://ubuntuforums.org/showthread.php?t=20001](http://ubuntuforums.org/showthread.php?t=20001)

---

### Post by yabbadabbadont on 2008-01-06
> **NineseveN said:**
> Follow this thread, it should at least clear out unused and unnecessary dependency files if you have them.

Did you forget to provide a link in your post?  ;)

---

### Post by NineseveN on 2008-01-06
> **yabbadabbadont said:**
> Did you forget to provide a link in your post?  ;)

I don't have the foggiest idea what you're talking about. :cool:


Just ignore the edit flag on my post...:mrgreen:

---

### Post by at0myx on 2008-01-06
I was trying to install UT2004 on ubuntu.  I installed it on /usr/local/games (which was the default directory) but for some reason:

1.  It Screwed with my sound.  I had to play with the settings to get it working again.
2.  The only way I could run the game was by using sudo ut2004 in the terminal.
3.  I tried to uninstall it after realizing it had no sound and the uninstaller wouldn't work (uninstall.sh in the installation directory).

So I searched ubuntu and someone posted that to simply remove the files, links, and directories because that is what the uninstaller does anyway.

Which is why I asked this question. :)

---

### Post by isecore on 2008-01-06
There's no easy answer to this question.

A well-behaved program installed from scratch (i.e. not using a package-manager) will uninstall simply by deleting the directory it installed into. This is a well-behaved program, self-contained and easily deleted. Many games tend to do it this way (i.e. I've seen it with Return to Castle Wolfenstein, Doom 3, Quake 4, etc)

But there's no rule to do it that way. UNIX and it's derivatives never focused very much energy on uninstalling a program, and as programs grew complex and started branching off in multiple files in multiple directories this has become a problem. Pretty much every distribution solved the problem by developing Package Managers that install and keep track of every installed file, and when uninstalling that package simply deletes the files it kept track of.

But there are plenty of programs which when you compile them from source, or use a less well-behaved installer will happily spread files all over your drive. These are usually a pain in the neck to remove.

---

### Post by at0myx on 2008-01-07
Ok.  So is there any real way to know whether I really uninstalled UT2004?

---

### Post by danwood76 on 2008-01-07
If you can no longer run it then I would have thought so, you will also need to remove the sym links in the /usr/sbin directory.

To be honest if you have removed the main directory I would doubt there will be much of it left, possibly some settings but that wont normally affect your system.

When comparing to windows which in general some of the registry entries and other files are generally put in to protect their proprietry software with masked file names and registry keys etc, which makes it harder to manually remove software in doze. You wont get this in linux.

---

### Post by at0myx on 2008-01-08
Ok.  Thanks for that.  I guess it should be ok then.  Perhaps UT3 will run better...

---

