---
title: "Firefox bookmarks lost"
date: 2007-05-17
forum: General Help
---

### Post by fzf3 on 2007-05-17
I'm running Dapper. It hung on me and I had to power off. On rebooot, all my Firefox bookmarks have disappeared. Any way to recover these?

---

### Post by total wormage on 2007-05-17
ok for as far as i can see you can do two things (taken from [http://kb.mozillazine.org/Lost_bookmarks]("http://kb.mozillazine.org/Lost_bookmarks"))

first:

close firefox, go to the terminal and type:
```
firefox -profilemanager
```
this should pop up a window in which you can select your profile, if there are more than one this was probably the reason your bookmarks disappeared. select yours (guess) and boot firefox from there :]

when you try to boot the profile manager and firefox just boots up you need to kill all firefox processes, because was still running in the background. you can do this with the commandline tool called 'top' or with 'gnome-system-monitor' and then go to processes and kill all things with 'firefox' in it

second:
if that doesn't fix it you can copy your bookmarks file like this:
"Bookmarks -> Organize (or Manage) Bookmarks... -> File -> Import... -> from File"

the file should be somewhere in your /.mozilla/firefox/ folder within your home folder.

good luck! :]

oh and i can't help myself here. i think sitebar client with a sitebar account is also a very nice way to manage your bookmarks :]]
take a look at this site: [http://sitebar.org/]("http://sitebar.org/")

---

### Post by fzf3 on 2007-05-17
Thanks but that didn't work. The popup box just contained a "default" profile and none of my old (hundreds of!) bookmarks.

This has unsettled me a bit. I've been running Dapper for about 8 months now with very few problems.  I know the answer is BACKUP YOUR FILES REGULARLY but even so, I'm disappointed to have this happen. 

Any other ideas, anyone?

---

### Post by fzf3 on 2007-05-17
OOps!!  The second solution worked a treat. I have my bookmarks back. Apologies for the previous post.


Thankyou Thankyou Thankyou  :D

---

### Post by total wormage on 2007-05-17
good ;]]
:popcorn:

---

