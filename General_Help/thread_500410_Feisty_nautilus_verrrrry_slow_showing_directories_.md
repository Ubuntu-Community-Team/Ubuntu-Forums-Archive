---
title: "Feisty: nautilus verrrrry slow showing directories &amp; files"
date: 2007-07-13
forum: General Help
---

### Post by mdurham on 2007-07-13
If I click on (say) /usr/lib which has quite a few dirs & files, it takes around 3 to 4 mins to show the result. I created a new user and found that Nautilus runs as normal, takes 2 to 3 seconds to show the /usr/lib result.
Does anyone have a clue as to what could be slowing Nautilus down when I'm under my normal user.
Cheers, Mike

---

### Post by mdurham on 2007-07-14
one last try!

---

### Post by Mr. C. on 2007-07-15
Perhaps a problem with one of the .nautilus files ?  Try :

```
mv $HOME/.nautilus to $HOME/.nautilus.prev
```

\logout and then back in as you to see if this helps.

MrC

---

### Post by mdurham on 2007-07-15
Thanks for your suggestion Mr. C. but it made no difference, still 5 mins to show /usr/lib or any other dir with lots of entries. I installed Thunar to try that and it exhibits the same problem, though it only takes maybe 1 or 2 mins. So, I guess it's not a Nautilus problem, but what could cause it? As I said before a newly created user (or root, NOT sudo) works fine.
While waiting the several mins for the entries to appear in (Thunar or Nautilus) the drive light is off most (90%?) of the time, just intermittently flashing on.
Cheers, Mike

---

### Post by Mr. C. on 2007-07-15
I have no specific knowledge about what these clients are doing internally, only general knowledge about how such programs must work based upon system internals, and years of experience.

I doubt it is a permission issue, as most files / directories in /usr/lib have world readability.

My bet is still that there is some customization or extra work being done for your login session, but not for the other user's.  Without using various forms of diagnostics, it will be difficult to determine the root of the problem.

I would create a new user, and copy all the .files and .directories from your home directory to the new user, log in as that user.  This will determine if the source is some dot file or directory.  If it is, start by moving 1/2 of them out of the way, until you find which half causes the problem.  Do this repeatedly with the remainder of the dot files and directories, until you nail exactly which one is causing the delays.

MrC

---

### Post by mdurham on 2007-07-17
Thanks for your help Mr. C. but I've given up on that, it's too time consuming. I'm moving on to Gutsy (which works at the moment!). I've found Feisty to be the most problematic distro, all other distros had their problems but for me, Feisty has the most.
Cheers, Mike

---

### Post by fragos on 2007-07-17
If you look at Nautilus Preferences-> Preview tab you'll find that a number of file types default to Preview.  Folders with a large number of files are slower to come up but you can improve that speed some by disabling some of the preview types.  The 1st time you open a folder with nautilus that has image and video files the open will take longer to make thumbnail images which are saved for the next time you access the folder.

---

### Post by Mr. C. on 2007-07-18
The caching delay would also occur for the new user, where the OP indicated there was no delay.  The delay occurs always for his UID, but not a new UID.

Caching delays wouldn't account for these two problems I don't think.

MrC

---

### Post by mdurham on 2007-07-18
Thanks for replying fragos, but I think 6 mins to display /usr/lib is a little bit excessive, don't you? And, it also happens with Thunar, though Thunar is a bit quicker.
Cheers, Mike

---

