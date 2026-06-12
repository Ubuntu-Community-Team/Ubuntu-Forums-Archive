---
title: "Automated deletion of empty folders?"
date: 2007-03-07
forum: General Help
---

### Post by fictivetoast on 2007-03-07
Is there any sort of terminal command by which to delete folders containing no contents in a certain directory?

Through various migrations between different music playing software across windows and linux over the year, my Music folder has become quite a mess...

---

### Post by moore.bryan on 2007-03-07
[I]i don't know if you can do this terminally, but couldn't you do an advanced search using the gnome-search-tool for folders with size "0" and then delete from there?  it's not really "automated," but it might be a solution for you...
[/I]

---

### Post by ArieT on 2007-03-07
What about this:
```

find -type d -empty -exec rm -R {} \;

```
Use at your own risk!

---

### Post by SuSUntu on 2007-03-07
> **fictivetoast said:**
> Is there any sort of terminal command by which to delete folders containing no contents in a certain directory?

Through various migrations between different music playing software across windows and linux over the year, my Music folder has become quite a mess...

Are you sure you're not Darko Beta?

[http://ubuntuforums.org/showthread.php?t=375491](http://ubuntuforums.org/showthread.php?t=375491)

I thought I was going crazy when I read your post. :)

---

### Post by lloyd_b on 2007-03-07
>  Is there any sort of terminal command by which to delete folders containing no contents in a certain directory?

Just run "rmdir *" in that directory.  The rmdir command will fail for any directory that actually contains files, so running that in your music directory will clear out all empty subdirectories.

Lloyd B.

---

### Post by Darko Beta on 2007-03-07
Hey!  That *was* weird.  I recommend you take a look at the thread susuntu pasted.  I have done a few rounds of testing on the code, and all seems to work just fine!  I plan to test it some more and when I am confident I'll probably set up a monthly cron to clean the empties out.

---

