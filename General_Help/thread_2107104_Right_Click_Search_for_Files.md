---
title: "Right Click Search for Files"
date: 2013-01-21
forum: General Help
---

### Post by SillySod on 2013-01-21
I'd like to be able to start a search for files whilst I am looking at a directory viewer.  I use Thunar, so what I would like to be able to do is to right-click on a directory name or in the "white space" and have a search option, and the starting directory for the search would be wherever I have clicked.

At the moment I have to go to Applications...Accessories...Search for Files and then navigate to the starting directory all over again.  When I am accessing files on my sambashare shared folders it is a bit of a pain as I have to go to home/username/.gvfs/share name because I don't get an option to go straight to the network share as a shortcut.  That all takes time and is frustrating because I'm already "there" in the Thunar window.

Is there something I can install to add this facility, or even could I build some kind of script to open the file search utility from the "current" directory and add it to the right-click context menu?

---

### Post by nuk28 on 2013-01-21
Try checking this page out: [http://xubuntu.wordpress.com/2006/07/12/how-to-search-for-files-with-thunar/](http://xubuntu.wordpress.com/2006/07/12/how-to-search-for-files-with-thunar/)

---

### Post by SillySod on 2013-01-21
I tried that, it gave me some really good pointers, so thank you.

The method suggested didn't quite work, because I don't have a uca.xml in my Thunar configs directory.  There were links to another way of doing it, and it appears that Thunar has the facility for you to add items to the context menu anyway, accessed from Edit...Configure custom actions.

I went into that and put the location of the script file in the command box and it worked fine.

I then realised that it was bringing up a different search utility.  After a bit of scratching around I found that the search tool I always use is in fact called "gnome-search-tool" so I made another context menu entry in Thunar with the command line as "gnome-search-tool --PATH=%f" and that works too, with the search utility which is familiar to me.

However, neither of these work with my sambashare folders, if I am in one of the shared folders, right clicking doesn't bring up either of the search options I created in the context menu.  Is there a way to do that?

---

### Post by LewisTM on 2013-01-21
Thunar user custom actions and Send to items are disabled inside GVFS locations. Not sure exactly why, perhaps because these locations are difficult to describe for the target scripts.

In your case, you might want to mount your samba share from within [fstab]("https://help.ubuntu.com/community/MountWindowsSharesPermanently"). Custom actions work for those. In [Thunar 1.6]("http://www.webupd8.org/2012/11/install-thunar-with-tabs-support-in.html"), Samba/CIFS shares appear on the side pane, whether they are gvfs or fstab mounts.

Cheers!

---

### Post by SillySod on 2013-02-14
I installed the later version of Thunar, although I think I now have a slight confused variant of Ubuntu running, as it appeared to involve partially upgrading to the next release.

I couldn't get my head round how to add the sambashares to my fstab file so I've abandoned that option, but the new version of Thunar shows each share as a "mounted" shortcut, so that's good enough for me.  It also remembers short cuts I have made to sub-directories in my shares, even when the share computer isn't switched on, so that helps too.

Today I had another idea about the original question.  I've made a launcher icon on the panel which runs "thunar /home/username/.gvfs" so that I can see my shares as a "local" directory as well as the "network" way.  This allows me to use my right-click search option, and terminal as well, so I think that fixes it for me.

---

### Post by LewisTM on 2013-02-14
Good to know it's working for you.
Accessing .gvfs is a common workaround for Thunar users. You can create a bookmark or symlink pointing to it, and give it a more descriptive name like 'Fileservers'.

Oh, and please mark the thread as SOLVED.:KS

P.S. If you ever upgrade to 12.10+, you will find your gvfs folder in /run/user/you/gvfs

---

### Post by SillySod on 2013-03-07
> **SillySod said:**
> After a bit of scratching around I found that the search tool I always use is in fact called "gnome-search-tool" so I made another context menu entry in Thunar with the command line as "gnome-search-tool --PATH=%f" and that works too, with the search utility which is familiar to me.


I have discovered that it isn't quite working when I use it from within a .gvfs folder.  I think it is because there are spaces in the pathname in %f, which is along the lines of "/home/user/.gvfs/sharename on sharemachine/searchfolder" and it is truncating the path at "sharename" when it encounters the first space, instead of navigating to "searchfolder".  Because a folder called "sharename" doesn't exist in ".gvfs", the search tool opens in ".gvfs" which isn't what I want.

Is there a way to pass the search pathname in inverted commas so I can make it work?

---

