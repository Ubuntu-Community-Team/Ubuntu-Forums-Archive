---
title: "E:The package lists or status files could not be parsed or opened"
date: 2017-01-10
forum: General Help
---

### Post by ehawk on 2017-01-10
Hi,

Using Ubuntu 14.04
The computer hanged while web browsing (only have 1GB RAM), so I was eventually forced to do a hard restart (holding power button in till everything shut down). 
Afterward, an error message appeared, at one point mentioning that /tmp could not be accessed. I did a memory test which revealed no problems. Was dropped to Grub and selected Ubuntu. Upon being greeted by the Unity desktop, there is a red circle with a minus (-) sign. Right clicking indicates that 

Error: Opening the cache (E:Read error -read (5: Input/output error), E:The package lists or status file could not be parsed or opened.)'. This usually means that your installed packages have unmet dependencies. 

Upon attempting to open Synaptic, the window appears, attempts to load the build tree, but fails, the windows closes and an error window appears indicating that the application failed. I sent a report after being prompted, and could see the details. I tried to open Synaptic again, and reach the same point, with the exception that I am no longer informed about the details of the failure. Clicking to send a report merely closes the window and generates the same error window (forced to continue/cancel and close the window). 

Entering

sudo -H synaptic

at the command line geneartes

```
Traceback (most recent call last):
  File "/usr/sbin/update-apt-xapian-index", line 106, in <module>
    indexer.incrementalUpdate()
  File "/usr/lib/python2.7/dist-packages/axi/indexer.py", line 692, in incrementalUpdate
    self.updateIndex(dbpath)
  File "/usr/lib/python2.7/dist-packages/axi/indexer.py", line 652, in updateIndex
    cache = self.aptcache()
  File "/usr/lib/python2.7/dist-packages/axi/indexer.py", line 423, in aptcache
    self.apt_cache = apt.Cache(memonly=True, progress=aptprogress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 107, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 151, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Read error - read (5: Input/output error), E:The package lists or status file could not be parsed or opened.
```

entering

sudo dpkg --configure -a

at the command line generates nothing but a new prompt.

After doing this, entering

sudo synaptic

at the command line generates the same errors as above.

I appreciate any helpful suggestions you can offer. I am guessing that there is a way to use dpkg to remove and reinstall synaptic and then reconfigure it.

---

### Post by slickymaster on 2017-01-10
First make sure that update-manager, synaptic, etc... are all closed and not running somewhere. Then open a Terminal and enter the following commands
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update
```

---

### Post by ehawk on 2017-01-10
Yay! Worked perfectly! Thankees! :)

---

### Post by slickymaster on 2017-01-10
You're welcome. Glad it's fixed and running.

Please don't forget to mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by ehawk on 2017-01-10
I tried to do this, clicking the link, then going to the top drop-down menu tab and selecting, "mark thread as solved." When I reload the web page, the tab in Chrome features "[SOLVED]", so I am hoping that did it. Thanks again!

---

