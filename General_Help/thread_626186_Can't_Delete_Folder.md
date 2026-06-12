---
title: "Can't Delete Folder"
date: 2007-11-28
forum: General Help
---

### Post by hotrod1 on 2007-11-28
Well I tried chmod already and rm rf and i know the risk of using that and I stupidly deleted my desktop but we only learn from our mistakes and I would like to know how to change permission on parent folder as seen in the attached screenshot so I can delete realplayer, thanks!

[[IMG]http://img526.imageshack.us/img526/3074/screenshotms5.th.png[/IMG]](http://img526.imageshack.us/my.php?image=screenshotms5.png)

---

### Post by dpar on 2007-11-28
How about > gksudo nautilus
Then browse the the desktop folder and delete the offending file.

---

### Post by diatribe on 2007-11-28
if you lack permission to delete something using sudo ie 'sudo rm -rf /etc/whatever' will allow you to delete as root, or do anything else as root for that matter

---

### Post by hotrod1 on 2007-11-29
Unfortunately when I did gksudo nautilus it doesn't show that folder on my desktop but it shows other files on my system and I do need root permissions because root is the owner of the file but I just want to be sure this time because I tried to do rm rf on the folder but it couldnt find it then it deleted my whole desktop.

---

### Post by geirha on 2007-11-29
What's the output of this? ```
ls -la ~/Desktop/
```
(I can't make out the name of the folder)

---

### Post by nikoPSK on 2007-11-29
sudo chown -R yourname foldername

so this is an example:

sudo chown -R niko usr/bin

then just go to the folder and remove it as you normally would.

---

### Post by hotrod1 on 2007-12-02
> **nikoPSK said:**
> sudo chown -R yourname foldername

so this is an example:

sudo chown -R niko usr/bin

then just go to the folder and remove it as you normally would.

Thanks so much, this solved my problem.

---

### Post by nikoPSK on 2007-12-02
welcome, remember that command. It is quite useful. Please mark this thread as SOLVED.

---

