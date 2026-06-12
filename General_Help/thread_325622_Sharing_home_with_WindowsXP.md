---
title: "Sharing /home with WindowsXP"
date: 2006-12-26
forum: General Help
---

### Post by Freck on 2006-12-26
I have my /home mounted on its own partition (ext3) which I'm sharing with Windows while I'm getting grounded in the new world of Ubuntu.
Anyway how do you hide the ubuntu files and folders (ie; .metacity .config) from Windows?


Also if/when I add a new user to ubuntu how are files shared between users eg. music?
Links?
Just want to know up front 'cos I'm a bit of an organization freak when it comes to files and folders.

Thanx.

---

### Post by Ecthelion on 2006-12-26
> Also if/when I add a new user to ubuntu how are files shared between users eg. music?
Links?
If you add a new user there will be an extra dir in /home/
You can read everything in that new user dir and the new user can read everything in your dir.
You can't write to the new usr his dir and the new user can't write to your dir.
> Links?
How do you mean? Like links bookmarks in firefox?
I suppose you can make a symbolic link to the other's folder and eventually change some permissions, but please be very carefull and never use the recursive option except if your really sure.

---

### Post by Ecthelion on 2006-12-26
> Anyway how do you hide the ubuntu files and folders (ie; .metacity .config) from Windows?
As far as I know you can't.

---

### Post by Freck on 2006-12-26
Thank for the info.  After 10 hours straight into the wee hours of this morning, I think I'm hooked and won't be worrying about Windows XP anymore.

I'm actually glad that I tried the RTM release of Windows Vista to see that it is just the same ol' same ol' for squeezing more $$$$$ out of the main stream home users.
Thanks to Vista, I have now embraced the world of Linux.

My 2c.

---

### Post by ~LoKe on 2006-12-27
The only way to hide those folders would be to set them as hidden files in Windows.

---

### Post by WiseElben on 2006-12-27
If you're still interested, there are several Firefox addons that will merge all your bookmarks from different computers and OS's. [Foxmark is]("http://www.foxmarks.com/") one, but there are other choices.

---

### Post by lol on 2006-12-27
out of curiosity, how do you share your ext3 partition with Windows?

Otherwise, for sharing files between users here is how I usually do: we are 2 using the same computer, but we have several documents in common (and music, pictures, etc.). Each user has it's own home folder of course, but I also created a /home/shared folder on which I gave read/write access to both users using ACLs (that's handy to manage permissions on newly created files).

---

### Post by Freck on 2006-12-29
Share ext3 with Windows using Ext2 IFS [http://www.fs-driver.org](http://www.fs-driver.org)

---

