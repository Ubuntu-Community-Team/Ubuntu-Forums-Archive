---
title: "PCmanFM won't copy/move files"
date: 2013-06-25
forum: General Help
---

### Post by furtom on 2013-06-25
This is an odd one.

PCmanfm simply won't copy or move files. It is otherwise fully functional.

This is true regardless if I use keyboard shortcuts or try to drag files with the mouse. Simply nothing happens.

I tried to start the program with at the terminal so I could get a look at possibly what was happening, but this doesn't work! starting pcmanfm at the terminal works fine, but the command exits and doesn't display info while it's running. I've never seen that before, either.

In any case, I can't recall when this started happening, because the first time it occurred  I just didn't think about it enough. Thinking maybe I was trying to do something without permissions, etc. But this is not the case.

I've been using Thunar instead, which works fine, but I'd like to figure this out if possible.

Thank you.

---

### Post by m3tro on 2013-07-09
Hello,
I am having the same problem. It works if I right click and hit copy, right click and paste. But it just doesn't do anything if I drag and drop or use Ctrl+C and Ctrl+V. This is really annoying....

In my case it originally worked and it stopped working after some automatic update of lubuntu.

---

### Post by furtom on 2013-07-09
Hey, Good job on finding this thread. I am still working around this issue.

You are in better shape than me. My right clicking doesn't work, either. I can right click, copy; but when I try to copy the file right click paste is grayed out, just like it would if I didn't have permissions for the directory, but this isn't the case.

It's very strange.

---

### Post by Dennis N on 2013-07-09
> **furtom said:**
> ...My right clicking doesn't work, either. I can right click, copy; but when I try to copy the file right click paste is grayed out, just like it would if I didn't have permissions for the directory, but this isn't the case.

It's very strange.

Your symptoms are the same as in this post. Check and see if the solution found applies in your case:

[http://ubuntuforums.org/showthread.php?t=2159027](http://ubuntuforums.org/showthread.php?t=2159027)

---

### Post by garethfoxwilliams on 2013-09-09
I have a similar problem on several machines. Copy/paste **does **work but I can't drag/drop.

I'm using Lubuntu 13.04 with PCManFM 1.1.0

I there a simple way of perhaps updating to the latest version, without compiling ?


(that's assuming the bug has been fixed...... )

---

### Post by kalehrl on 2013-09-09
Yes, there is.
Add this ppa:
[https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily/+index?field.series_filter=raring](https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily/+index?field.series_filter=raring)
and then:
```
 sudo apt-get update && sudo apt-get upgrade
```

---

### Post by garethfoxwilliams on 2013-09-10
Thanks for the lead. that's got me up to version 1.1.99.0, but unfortunately some problems still persist.

For example, I can drag a file from the PCManFM window to the desktop, but not back.

Within the window, however, I can drag rom the desktop to other directories.

---

### Post by furtom on 2013-09-13
> **garethfoxwilliams said:**
> Thanks for the lead. that's got me up to version 1.1.99.0, but unfortunately some problems still persist.

For example, I can drag a file from the PCManFM window to the desktop, but not back.

Within the window, however, I can drag rom the desktop to other directories.

Are you running [COLOR=#000000]Parcellite by any chance?[/COLOR]

[COLOR=#000000]I had the same issues it that was the culprit. Try exiting out of it and see if your problems don't disappear.[/COLOR]

---

### Post by humpty88 on 2014-07-15
It's still buggy in Ubuntu 14.04.
You can use the Copy/Paste from the Edit>pull down menus , they work o.k.
But sometimes you cannot copy/paste by dragging between panels.

---

### Post by ibjsb4 on 2014-07-15
> PCmanfm simply won't copy or move files. It is otherwise fully functional.
I am not seeing that problem in PCmanFM-Qt.  I do not run lubuntu so I do not know for sure, but it may be an option for you.

---

