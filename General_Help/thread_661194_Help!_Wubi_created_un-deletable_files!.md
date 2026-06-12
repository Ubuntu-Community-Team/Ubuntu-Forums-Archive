---
title: "Help! Wubi created un-deletable files!"
date: 2008-01-07
forum: General Help
---

### Post by 888gavin on 2008-01-07
I installed Wubi, but it didn't work, so I un-installed it. I planned on removing everything, so that I could install it again to see if it would work.

Wubi (I think) created a folder in C:\ called ".Trash-Ubuntu" I tried to delete it, but an error came up saying that the file name was invalid, so I renamed the folder to test, and tried to delete it again. The error came up again. I looked inside the folder, and there were two files. They are both files with ABSOLUTELY NO DATA! NO NAME, EXTENSION, NOTHING. I cannot rename them, and I cannot delete them. The first file is named " " (without quotes) and the second file is named " (copy)". I have tried using some program called Delete-On-Next-Reboot (something like that), but it still wouldn't work. Then, I tried to delete the file with a few different DOS methods, but they didn't work either. Someone, please help me delete these files!

---

### Post by 888gavin on 2008-01-07
**[COLOR="SeaGreen"]PROBLEM SOLVED![/COLOR] PROBLEM HAS NOTHING TO DO WITH WUBI - APOLOGIES**

When I booted the Ubuntu LiveCD to try out Ubuntu, it mounted all of my other hard drives. It added those files and folders to C:\ automatically. All I had to do to delete them was boot into the Ubuntu LiveCD, mount the affected drive(s), press Ctrl-H (to view hidden files and folders), then I simply deleted .Trash-Ubuntu.

This is quite a problem with the LiveCD, as normal computer users wouldn't have a clue what to do. The LiveCD should have a script on it, that says:

```
when computer=shutsdown goto DeleteStuff()
task DeleteStuff()
delete .Trash-Ubuntu
```

That's not really code, but you get what I mean. :wink:

---

