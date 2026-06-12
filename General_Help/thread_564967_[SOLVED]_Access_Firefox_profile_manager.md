---
title: "[SOLVED] Access Firefox profile manager"
date: 2007-10-01
forum: General Help
---

### Post by pack74743 on 2007-10-01
I need to know how to access the FF Profile Manager in order to create a new profile.  The profile I migrated from Windows has no working extensions nor themes.  They show up in "Add- ons" but don't work.  Is the new profile route the best solution?  Thank you.

---

### Post by por100pre1 on 2007-10-01
```
firefox -ProfileManager
```

Migrate your bookmarks, try to setup everything else manually, it'll give you better results.

Hope it helps. :)

---

### Post by pack74743 on 2007-10-02
That worked.  I copied over several other things successfully, but then started from scratch with extensions and theme.  Thanks much.

---

### Post by philidox on 2007-11-11
I made a youtube video for accessing firefox profile manager here is the url:

[http://www.youtube.com/watch?v=fSlQJlr1QlU](http://www.youtube.com/watch?v=fSlQJlr1QlU)

---

### Post by por100pre1 on 2007-11-11
> **philidox said:**
> I made a youtube video for accessing firefox profile manager here is the url:

[http://www.youtube.com/watch?v=fSlQJlr1QlU](http://www.youtube.com/watch?v=fSlQJlr1QlU)

That's a good tip, specially for those not using the version from the repositories. Thank you for posting it. :)

---

### Post by philidox on 2007-12-16
I found an even EASIER way to access firefox profile manager

BEFORE YOU DO THIS MAKE SURE FIREFOX IS **NOT** RUNNING, even in the background.  The best way to do this is to look at all you desktop background and ensure its not running on either of them and then go to System>>>Administration>>>System Monitor. Go to the "Processes" tab and look for firefox.  If its not there you good to follow those simple steps if it is in your processes then highlight it and click "End Process" in the bottom right hand corner of the window.

Step 1: Press "Alt+F2"
Step 2: In the search bar type "firefox -profilemanager"

If there is any confusion follow the link to the youtube video:
[http://www.youtube.com/watch?v=iqIBO_P79nw](http://www.youtube.com/watch?v=iqIBO_P79nw)

---

