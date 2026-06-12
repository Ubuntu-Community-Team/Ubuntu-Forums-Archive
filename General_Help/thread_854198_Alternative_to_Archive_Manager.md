---
title: "Alternative to Archive Manager?"
date: 2008-07-09
forum: General Help
---

### Post by ybd on 2008-07-09
Well... I don't like the Archive Manager (the default one that comes with Hardy). I have reasons... but I'm a bit too tired to type them and besides, who cares.

I tried WinRAR with Wine but it's too slow (probably the result of the emulation and my somewhat old PC). Is there a "Linux-native" archive manager, preferably with a GUI similar to that of WinRAR?

---

### Post by VMC on 2008-07-09
> **ybd said:**
> Well... I don't like the Archive Manager (the default one that comes with Hardy). I have reasons... but I'm a bit too tired to type them and besides, who cares.Maybe after you get some rest and can tell us why you don't like Archive Manager. If you have 7zip , rar, installed then Archive Manager will work on almost any zipped file including ISO's.

If your referring to the many r00 - rar files, it can work with that as well

---

### Post by ybd on 2008-07-13
So is there no alternative to Archive Manager? Surely there's something. I just want to experiment and possibly find something I'm more comfortable with.

---

### Post by ibutho on 2008-07-13
File Roller (Archive Manager as you called it) will work with any file formats as long as you have the required libraries installed. To manage rar files, you need to install a package called unrar. You can look for more archive managers at [GNOME Files]("http://www.gnomefiles.org").

---

### Post by ad_267 on 2008-07-13
Well I guess you could try karchiver, and there's probably more. But that's a kde app and probably depends on a lot of other packages you might not have.

What's wrong with file roller anyways? Personally all I ever do is right click on a file in nautilus and select extract here or right click on a directory and select create archive. As everyone else already mentioned the number of formats supported by file roller is limitless.

---

### Post by ybd on 2008-07-13
To everyone who suggested I get the libraries for more file support: I've done this already. What I don't like about File Roller (sorry, now I'll get the name right) is the interface - it's too simplistic and limited in my opinion. I really don't see why everyone seems to take this so personally.

I'll try karchiver, thanks.

---

### Post by ibutho on 2008-07-13
If you don't mind installing kdebase packages, look at an app called ark. File Roller is simplistic because thats the philosophy of the GNOME developers. The try to make apps as simplistic as possible and adhere to their HIG. This sometimes does not go well with some users because they had a tendency to remove features to achieve their goals.

---

### Post by ad_267 on 2008-07-13
> **ybd said:**
> To everyone who suggested I get the libraries for more file support: I've done this already. What I don't like about File Roller (sorry, now I'll get the name right) is the interface - it's too simplistic and limited in my opinion. I really don't see why everyone seems to take this so personally.

I'll try karchiver, thanks.

Ok well I hope you find something more suited to your needs. I don't really see what more you could want to do with an archive manager myself though.

I did a search for archive in add/remove applications and also found xarchiver, xarchive manager, ark, squeeze and xnc.

---

### Post by ybd on 2008-07-13
Thanks guys. xarchiver (even though I've only used it for about 5 minutes) seems perfect for me.

---

### Post by aelfwyne on 2008-07-26
Still looking for one myself...

It seems that unarchiving via the GUI in linux is slower than it was in XP for me - not quite sure why. Also, I don't like the fact that none of the archivers I've tried yet (xarchiver, squeeze) have a progress meter! They have a busy meter, but no way to tell how much of that 4GB archive is done yet, without opening a folder in the file browser and watching the file increase in size.

---

### Post by iaculallad on 2008-07-26
> **aelfwyne said:**
> Still looking for one myself...

It seems that unarchiving via the GUI in linux is slower than it was in XP for me - not quite sure why. Also, I don't like the fact that none of the archivers I've tried yet (xarchiver, squeeze) have a progress meter! They have a busy meter, but no way to tell how much of that 4GB archive is done yet, without opening a folder in the file browser and watching the file increase in size.

Try peazip, it's a GUI multi-archive type handler and it's available in the repo.

```
sudo apt-get install peazip
```

---

