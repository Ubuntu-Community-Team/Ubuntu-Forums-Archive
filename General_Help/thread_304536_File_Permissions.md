---
title: "File Permissions"
date: 2006-11-21
forum: General Help
---

### Post by dontgetshocked on 2006-11-21
Is there not a way to change file and or folder permissions without doing them one at a  time? I can only do one file or folder at a time, Geeezzzz!
I tried but it didnt work for me, maybe I am doing something wrong! 


Thanks,

---

### Post by meng on 2006-11-21
Sure you can chmod in the terminal with wildcards like *, and switches like -R (recursive). Are you trying to do this through Nautilus/Konqueror instead?

---

### Post by dontgetshocked on 2006-11-21
Yes, thru Konqueror, Thanks for the suggestion. So use the terminal instead?
Thanks

---

### Post by meng on 2006-11-21
Yes use the terminal! start off with the commands
man chmod
man chown

if you've never used these commands to change permissions or ownership (respectively).

Otherwise google. Otherwise post what you're trying to achieve here and maybe we can help.

---

### Post by dontgetshocked on 2006-11-21
I want to change the owner and also change to read/write

---

### Post by meng on 2006-11-21
If you aren't already the owner, then you'll probably need admin privileges. Let's say your username is meng, and you want to change all files in /home/fred to be owned by meng and read-write at the user level.
(as you know, permissions are set at 3 levels: user, group and other)

Here's how I would do it (there's more than one way to skin a cat):

cd /home/fred
sudo chown -R meng:meng *
sudo chmod -R u+rw *

---

### Post by dontgetshocked on 2006-11-21
I am listed as david as a user. I have admin privileges but am doing this as root anyway. It also shows me as david-David Elliott
Which one should i use? david or david elliott and also does case matter?

---

### Post by meng on 2006-11-21
david
Case always matters.

---

### Post by dontgetshocked on 2006-11-21
Thanks

---

