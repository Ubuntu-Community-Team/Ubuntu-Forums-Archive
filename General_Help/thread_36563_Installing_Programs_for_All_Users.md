---
title: "Installing Programs for All Users"
date: 2005-05-23
forum: General Help
---

### Post by cinematography on 2005-05-23
Where are programs for all users stored? For example, I just downloaded the latest Firefox, but I don't know where to install it to update my existing version, and now I think I have two Firefoxes installed. :(

---

### Post by JonahRowley on 2005-05-23
The firefox that was there before was packaged for Ubuntu, so it'll install in different places than the Firefox installer.  If you want to use the Firefox installer, uninstall the Firefox Ubuntu package with **sudo apt-get remove mozilla-firefox** first.  I'm not sure, but the Firefox package might not do things like add entries to your Gnome menu, you might have to add those manually.

Also, if you want the latest firefox, look for a backport.  I haven't done any of those yet, so I can't give you much more info on that.

---

### Post by cinematography on 2005-05-23
That worked beautifully. Thanks a lot for your help. I've decided to just install Firefox to a bin folder in the home directory of each user account.

---

### Post by JonahRowley on 2005-05-23
That works I guess, but it's not exactly "clean".

---

### Post by cinematography on 2005-05-23
[QUOTE=JonahRowley]That works I guess, but it's not exactly "clean".[/QUOTE]
You never told me the proper place to put it. :(

---

### Post by John Bennett on 2007-03-27
I would also like to know where and how to install programs so they are available to all users.

---

### Post by hikaricore on 2007-03-27
May 23rd, 2005... you're better off making a new thread

---

### Post by John Bennett on 2007-03-27
I was just trying to be a good citizen by diligently searching the archives before starting a new thread.

Example:  I want to install Real Player, once, for all users, not in everyone's home folder.

How does one do that?

---

### Post by zvacet on 2007-03-28
Put bin files in** usr/bin**.That is common place for executable files.From there any user can use it.

---

