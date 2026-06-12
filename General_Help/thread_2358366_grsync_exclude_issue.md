---
title: "grsync exclude issue"
date: 2017-04-12
forum: General Help
---

### Post by cmcanulty on 2017-04-12
I am trying to exclude my virtual machines from the grsync process as they cause it to run for hours. I thought I had the correct syntax but apparently not as it still tries to backup the VB. Here is what I have in the text box at the bottom of the advanced settings. Thank you

```
--exclude=/home/cmcanulty/"VirtualBox VMs"
```

---

### Post by dragonfly41 on 2017-04-12
I'm also starting to use grsync to copy from internal drive to external drive.
But in my case I've been researching how to copy hidden folders and files.

From what I've read so far you might achieve your aim by using this.

--exclude="~/VirtualBox VMs"

or define excludes in a file you create ... containing "~/VirtualBox VMs"
but I avoid using spaces in folder names as a general practice.

--exclude-from="~/rsync_exclude.txt"

Run .. rsync -help .. to see the options.
Note .. not grsync -help

--exclude=PATTERN    exclude files matching PATTERN
--exclude-from=FILE     read exclude patterns from FILE

---

### Post by cmcanulty on 2017-04-12
I thought spaces were OK as long as they were in quotes?
--exclude="~/VirtualBox VMs" doesn't work either

---

### Post by ajgreeny on 2017-04-12
I would also suggest you put the complete path in quotes rather than just the final folder.

I totally agree with dragonfly41 about avoiding spaces in folder or file names, but as you will be aware, VBox defaults set the pathway of the VMs to **VirtualBox VMs** which I find very annoying; I am sure there are ways to change that pathway but whenever I have attempted to do so I must have missed something and lose the ability to boot my VMs as far as the VBox Manager window is concerned.  I have not yet looked very hard yet for ways to change this but might do so after reading this thread.

---

### Post by dragonfly41 on 2017-04-12
Perhaps you can use a search pattern .. I'm not too familiar with them in rsync
but a wildcard after ~/Virtual

---

### Post by Dennis N on 2017-04-12
change: 
**--exclude=/home/cmcanulty/"VirtualBox VMs"**
to:
**--exclude=VirtualBox***
You don't want the full path here.

---

### Post by cmcanulty on 2017-04-12
--exclude=VirtualBox* worked! Thanks . I guess by relative path they mean relative to the source of the backup. So now I made a grsync session with exclude VB for a normal fast backup and not delete on destination and a session including VB and delete on destination for when I have hours to waste. Not sure why VB backs up so slow. It must recopy the entire 52GB not as normal in grsync that just grabs the changes as my entire backup excluding VB runs in a few minutes for 200GB

---

