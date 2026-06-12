---
title: "Nautilus freeze on large files"
date: 2008-06-07
forum: General Help
---

### Post by cozmicharlie on 2008-06-07
I am having problems with folders that contain a large number of files.  I am using Hardy.  I have folders that hold music files.  When I open these, Nautilus locks up in the file browser.  I let it run and eventually I can access the files - I mean a long time (hours is some cases).  Once it does go through this I can access the files fine but it takes so long to get to that point.  It does not lock up the computer and I can close the folder but I can't access any files in the folder until Nautilus finishes whatever it is doing.  I can actually access the files easier by ssh through another computer. I have read a number of posts about Hardy locking up but I don't think this is the same. 

Any help is very appreciated.

---

### Post by happyhamster on 2008-06-07
Try disabling the "Preview sound files" feature. In nautilus, choose Edit-->Preferences-->Preview-->Preview sound files-->never.

You'll probably have to restart nautilus to let it take effect (close all nautilus windows, or issue "killall nautilus" in a terminal).

Good luck.

---

### Post by cozmicharlie on 2008-06-08
> **happyhamster said:**
> Try disabling the "Preview sound files" feature. In nautilus, choose Edit-->Preferences-->Preview-->Preview sound files-->never.

You'll probably have to restart nautilus to let it take effect (close all nautilus windows, or issue "killall nautilus" in a terminal).

Good luck.

Thanks for the suggestion, I really appreciate the help.  Unfortunately I tried your suggestion but no luck - still have the same problem.  The first time I open the folder is when this happens - if I let it run it's course, I don't have the problem again until I shut down and restart the computer.  It is just the first time I try and access the folders so I think your suggestion is on the right track - Nautilus is doing something that is taking a long time.  I also disabled the "browse media when inserted" and "count number of items" but no change.

---

### Post by happyhamster on 2008-06-08
- Try running nautilus from a terminal (it might print error messages). First let it do a self-check:

nautilus -c

- Then start nautilus:

nautilus

- and use it to browse the music folder. Also, there could be a "nautilus-debug-log.txt" in your home dir with error information.

- There are several bugs on launchpad that appear similar to your problem, but most of them are marked solved. For example, see:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/164971](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/164971)
[https://bugs.launchpad.net/ubuntu/+source/esound/+bug/183411](https://bugs.launchpad.net/ubuntu/+source/esound/+bug/183411)

- BTW, did you install any nautilus plugins?

- Also, how many files are in the music folder? Does it help when decreasing that number?

---

### Post by cozmicharlie on 2008-06-08
Thanks again for all your help.  I will do as you suggest later when I have some time to devote to it.  

I can answer a few of the questions - I have not added any Nautilus plug-ins. I have other subfolders of the main directory that do not have as many files and the problem does not occur with these.  It is only in the folder with the large number of files.  

FYI - this folder contains approx 8,000 individual files in 250 GB.  I have a lot of Grateful Dead live shows (and others) so I have a Grateful Dead main folder and sub folders labeled 70's, 80's 90's.  The folder I refer to above is just the 70's folder.  All the GD folders have this problem.  I have other music folders under the main directory (music) that have fewer music files and these do not have the problem.  I could break it down to more subfolders and I may have to but I was hoping i would not have to do that.  I had this many files in Gutsy and did not have this problem so I assume it is something in Hardy.

I will try your other suggestions later when I have time and report back. I tend to search the forums and forget about the bug reports so your post was a good reminder that I need to search both. 

Again, thanks for all your help - it is very appreciated.

---

### Post by cozmicharlie on 2008-06-08
It looks to me like this bug is what I am experiencing [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/164971](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/164971)

I have a temporary work around until they fix it.  I installed PCMan File Manager and it works great.  No problems even with my large music files.  For those with a similar problem here is what I did:
[LIST=1]
[*]Install all the dependencies listed here [http://pcmanfm.sourceforge.net/build.html](http://pcmanfm.sourceforge.net/build.html) from Synaptic.
[*]Instead of using the PCMan in Synaptic (it is an older version) i installed the deb from here [http://www.getdeb.net/release/2374](http://www.getdeb.net/release/2374).
[/LIST]

This is a nice file manager and I may even keep it when Nautilus gets fixed.  

Thanks again for all you help "happyhamster".

---

