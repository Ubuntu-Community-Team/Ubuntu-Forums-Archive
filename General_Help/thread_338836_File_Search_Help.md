---
title: "File Search Help"
date: 2007-01-15
forum: General Help
---

### Post by allwin on 2007-01-15
I have Gnome and Nautilus.  I cannot seem to get it to find files "the way I want".

What I'm looking for is something that will find a file such as "hdparm.conf" wherever it is!  I want to look in all folders.  The only options given by the search seem to be things like file types ("music", "pictures" and so on) or maybe file data like what's IN the file.  I don't care about that.  I want to just find all files names "hdparm.conf" wherever they are.

Secondly, I'd like to find files by modification date.  I'd like to get a list of all files changed, like today, or like since the last time I installed UBUNTU.  Yeah, I know that would be a huge list but I'm willing to eyeball it to refresh my memory on what exactly I changed.  Objective is to yank my own customizations off and save them somewhere, also to resolve "how did this file get changed" questions when some automated process clobbers a change I made.

Sigh, is there a file manager out there that looks just like W*** Explorer, with a treeview on the left and a pane on the right (which refreshes when you click an entry on the treeview), and a search filename by wildcard, size, moddate, and extension.  I don't care if it doesn't come with a little puppy dog.  KTHXBYE.

---

### Post by meng on 2007-01-15
Main menu (left hand corner): Places > Search/Find files, and choose Filesystem as the place to search in.

---

### Post by ~LoKe on 2007-01-15
I'm a sucker for the commandline, so in addition to what was posted above (does what you need exactly), I would use this.
> loke@x04d:~$ ls -la /etc/|grep hdparm.conf
-rw-r--r--   1 root root      4728 2006-01-04 06:13 hdparm.conf
-rw-r--r--   1 root root      4793 2006-11-27 10:37 hdparm.conf.dpkg-new

---

### Post by bscbrit on 2007-01-15
At a terminal, type

man find


There are more options there than you will ever need!  But here are a few examples:

[http://www.linuxforum.com/linux_tutorials/92/1.php](http://www.linuxforum.com/linux_tutorials/92/1.php)

---

### Post by allwin on 2007-01-15
> **~LoKe said:**
> I'm a sucker for the commandline, so in addition to what was posted above (does what you need exactly), I would use this.
Thanks for the command line stuff.  That is a big help in one way, but I'm also looking for a GRAPHICAL method of manipulating the found files.  Because having located them, I might want to display them, edit them, or drag n drop them somewhere else, or maybe cut and paste copy them.

---

### Post by allwin on 2007-01-15
> **meng said:**
> Main menu (left hand corner): Places > Search/Find files, and choose Filesystem as the place to search in.
Thanks but, there is no FILESYSTEM option.  Furthermore, when I check PREFERENCES in SEARCH, it offers me a chance to INDEX certain folders.  I don't WANT to do that!  I don't want to see files based upon "meta data", and I don't want to deal with the command line.

---

### Post by ~LoKe on 2007-01-15
> **allwin said:**
> Thanks but, there is no FILESYSTEM option.  Furthermore, when I check PREFERENCES in SEARCH, it offers me a chance to INDEX certain folders.  I don't WANT to do that!  I don't want to see files based upon "meta data", and I don't want to deal with the command line.

In the search dialog, it'll say **Look in:** and there'll be a dropdown box.  Click the box, choose "other".  A new dialog will open up, on the left there'll be a panel, one of the items in the panel will be "Filesystem".  Choose that.

I believe that's what he was referring to.

---

### Post by allwin on 2007-01-15
> **~LoKe said:**
> In the search dialog, it'll say **Look in:** and there'll be a dropdown box.  Click the box, choose "other".  A new dialog will open up, on the left there'll be a panel, one of the items in the panel will be "Filesystem".  Choose that.

I believe that's what he was referring to.
When I use NAUTILUS, I only see a text box above the list of icons which says SEARCH.  I enter "hdparm.conf" and hit enter and it says 0 RESULTS.  I am IN the FILESYSTEM at the time of the search.

When I go to my SEARCH option (Places and APPLICATIONS...accessories...search) I receive a window entitled DESKTOP SEARCH and have options EVERYWHERE...APPLICATIONS...CONVERSATIONS...etc.  Similarly when I enter "hdparm.conf", and select EVERYWHERE, it also reports 0 files found.  This is UBUNTU edgy with GNOME and NAUTILUS.

If I then click on the empty result pane, I can get into a mode which allows me to + additional search criteria.  So I can then select FILE SYSTEM as a WHERE, but when I go to add the OTHER file type, I get a list box full of MIME types, and there is not an option to include ALL FILES OF ALL TYPES.  

Surely there must be a way to search here.  Sorry if I'm being a little dogged here, but I cannot go fishing if I have to tell just what kind of fish I want to catch!  I don't know the type of a .CONF file for example, as opposed to a .CONF.BAK or .CONF~ file.

I want to see them all.

Thanks, hope I'm clear about this.

---

### Post by jocko on 2007-01-15
This is how the  search function looks like in edgy. Notice the second option from the top "look in this folder:" (translated from swedish). If it doesn't look like this you probably have installed beagle, which would explain your problems.

If that's it, try hitting Alt + F2 and type "gnome-search-tool" in the "run program" dialogue to get the standard search tool.

---

### Post by ~LoKe on 2007-01-15
**Places -> Search for Files...**
[[IMG]http://img522.imageshack.us/img522/3291/search1dg5.th.png[/IMG]](http://img522.imageshack.us/img522/3291/search1dg5.png)

Click the dropdown box and choose "Filesystem".
Type your text and hit **Find**.

[[IMG]http://img522.imageshack.us/img522/7930/search2lm0.th.png[/IMG]](http://img522.imageshack.us/img522/7930/search2lm0.png)

---

### Post by allwin on 2007-01-15
> **jocko said:**
> This is how the  search function looks like in edgy. Notice the second option from the top "look in this folder:" (translated from swedish). If it doesn't look like this you probably have installed beagle, which would explain your problems.

If that's it, try hitting Alt + F2 and type "gnome-search-tool" in the "run program" dialogue to get the standard search tool.
Aha.  Thank you!  You're right...I was messing with AUTOMATIX and decided to install Beagle...which placed itself in the SEARCH menu in GNOME.  So now I'm going to get rid of BEAGLE.  Yes, the gnome-search-tool is what I was looking for, and I didn't realize BEAGLE was getting invoked instead, and that it didn't offer the functions I was after.

Case closed!  Now I just have to be on the lookout for cruft that obliterates USEFUL utilities, eh?

---

### Post by glabouni on 2007-01-29
I've experienced the same kind of problem since I've installed beagle 

I found the builtin find feature not as powerful or useful as commands such as slocate or find

---

### Post by allwin on 2007-01-29
> **glabouni said:**
> I've experienced the same kind of problem since I've installed beagle 

I found the builtin find feature not as powerful or useful as commands such as slocate or find

Thanks.  I fixed it by removing BEAGLE.  Then all the search facilities began to work according to my own particular requirements.

---

