---
title: "Launch script on closing of BluRay Drive"
date: 2015-09-04
forum: General Help
---

### Post by rks1789 on 2015-09-04
There are a fair number of posts and guides on this subject (launching a script when a disc is inserted), but I have not found one that works yet on my newly updated 15.04 Ubuntu install.

first I tried to use the Gnome "what should I do when a disc is inserted), I created a .desktop file, it shows up when I look for it. 

It does NOT show up when I try to select "other programs.  I have tried lots of things, nothing made it show up in that menu.


So I gave up on that (only a hour or two wasted) to try to get incrontab to work.  The issue it seems is that at some point the events that get issued stopped matching what incrontab was programmed to look for.  The specific example is when I use inotify it shows that ACCESS happens.  incrontab expects that to be IN_ACCESS.

If I put ACCESS in the field in my incrontab entry when I save it converts it to "0" (no quotes), and neither of them actually kick off the script.

I have looked, and found no details on where the headers are to potentially update incron to the new events.

I did see someplace a udev solution that was more steps than I had time to try so far.

Does anyone have a tested method on Ubuntu 15.04 to kick off a script when the blu-ray drive is closed and mounted?

Thanks!

Rich

---

### Post by pqwoerituytrueiwoq on 2015-09-05
in xfce i have a 'removable devices and media' section i can use to run a command
[url=http://i.imgur.com/96qFbWN.png]
  [img]http://imgur.com/96qFbWNl.png[/img]
[/url]
does that not work on blueray drives? if not id guess it is cause of the encryption on retail disks making it a pain to determine content type

---

### Post by rks1789 on 2015-09-06
Apparently in previous versions of Gnome (the default desktop, this is a primarily headless server so I don't care much about what desktop I run) there was a place to type a command.  The current version does not have a way to do so, which is why I tried to create a .desktop file for it, but that does not show up in the list of options no matter what I have tried.  I tried to get a screenshot, but my default vnc is not gnome, and for some reason the remote connection isn't working right now (connection refused) <edit> still can't get the default login to work, and still out of ideas.</edit>

---

### Post by rks1789 on 2015-09-11
I have just about given up, nothing I've tried has gotten this to work.  I am under the impression I should come back to this when incrontab has updated to the "new" events, or the gnome version of "what to do when a disk is inserted" has a "run this command" again.

---

