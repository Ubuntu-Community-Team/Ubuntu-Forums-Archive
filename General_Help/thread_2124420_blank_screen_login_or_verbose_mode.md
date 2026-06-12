---
title: "blank screen login or verbose mode?"
date: 2013-03-10
forum: General Help
---

### Post by macminiuser on 2013-03-10
I would rather login with a black screen than a graphical login,what do you have to change in order to do that?

---

### Post by Bashing-om on 2013-03-10
macminiuser; Hi !
You do not say what version you are running. In 12.04 and earlier, one may make an edit in /etc/default/grub to achieve that result. It is always advisable to make a backup of any file that one edits.
> # Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
just delete the "#" character to "Uncomment" in the #GRUB_TERMINAL line.
then after saving your changes do terminal code:
```
sudo update-grub
```to write the change to the config files.[INDENT=4]
hth

[/INDENT]

---

### Post by macminiuser on 2013-03-12
Thanks for the info!!

---

### Post by Bashing-om on 2013-03-12
macminiuser; Glad to assist.
If That works for you, please mark this thread as solved:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
Problem still ? ->graphical instruction:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)[INDENT=3]happy ubuntu'n
[/INDENT]

---

