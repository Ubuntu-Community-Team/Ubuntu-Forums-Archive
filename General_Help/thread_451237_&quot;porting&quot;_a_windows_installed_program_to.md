---
title: "&quot;porting&quot; a windows installed program to a wine drive_c"
date: 2007-05-22
forum: General Help
---

### Post by the_it on 2007-05-22
I've been wondering for a while about this.  I have both XP and Ubuntu installed on this one box.  On my Ubuntu partition, I used to have individual users all having their own wine drives.  But that meant I had to install Flash studio 3 to 5 times.  So what I did was I set up a universal drive_c for everyone's wine, /home/wine.  Of course, it would be even better if I could save even more disk space by having wine refer to the programs installed in my windows drive C, complete with all the DLL dependencies and the like that windows loves to have.

Is that at all possible, by the way?  To "port" an already installed Windows app to your wine's drive_c, or to have the drive_c linking to windows C:?  Or is it also possible to install a program on Windows and on Wine, then to delete the wine installation, then ln -s from the windows Program Files folder to the one in wine?  What considerations would I have to take if I do that?  Any files I have to edit and stuff?

---

### Post by Nehvrook on 2007-05-22
I think this post should have been in the gaming and leisure section.

I'm not sure if it's safe to do what you're asking. Writing to NTFS partitions can cause problems. There are some drivers you can get that let you do it which are apparently fairly stable.
I'm not sure how many games would work in this way, and you'd probably have to enter a bunch of registry entries for each game too

---

### Post by anaconda on 2007-05-22
yes. Both options are possible. 

But you will need to copy the relevant parts of windows registry to wine.

This is how I gor farcry working with wine: installed it ot windows, copied the installation and some registry keys to wine added the needed DLL:s and it worked perfectly..

And photoshop 9 works both ways. from windows partition and if copied to drive_c it works from there too..

---

### Post by the_it on 2007-05-22
> **Nehvrook said:**
> I'm not sure if it's safe to do what you're asking. Writing to NTFS partitions can cause problems.

ntfs-3g has been reported safe and stable for quite a while now, and I haven't had any problems using it so far.

[QUOTE=anaconda]This is how I gor farcry working with wine: installed it ot windows, copied the installation and some registry keys to wine added the needed DLL:s and it worked perfectly..[/QUOTE]

How do I do that?  Any guides or tips on adding registry keys and dls? googling "wine howto override dll" brings up a lot of junk to me.

---

