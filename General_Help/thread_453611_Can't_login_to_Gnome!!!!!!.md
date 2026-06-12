---
title: "Can't login to Gnome!!!!!!"
date: 2007-05-24
forum: General Help
---

### Post by juniorsonny on 2007-05-24
When I enter my user name and pasword, it gives me a error message that says (I was loggedin only for 10 sconds and to use an alternetive session to login. And that one cause may be not enough disk space)  I know I made my root partition a little small, I only had 25 to 50 megs left.  Could this be the problem? Could I resize it?  And are there other things that could cause this?

---

### Post by juniorsonny on 2007-05-24
*When I enter my user name and pasword, it gives me a error message that says (I was loggedin only for 10 sconds and to use an alternetive session to login. And that one cause may be not enough disk space) I know I made my root partition a little small, I only had 25 to 50 megs left. Could this be the problem? Could I resize it? And are there other things that could cause this?*

---

### Post by scrooge_74 on 2007-05-24
is not so much your root partition, your /home folder is full

Enter in recovery mode, so you are log as root, then go to /home/your_user/.Trash
then type rm -rf *.*

depending on your config it should be good to delete files in /var/log

delete compress file

also do sudo apt-get autoclean

---

### Post by obrient on 2007-05-24
This actually happened to my coworker while he was messing with permissions. If removing the trash stuff didn't work you might want to check out your /home permissions. He had changed his to read only on his /home/user_name folder when they should be ```
drwxr-xr-x
```. Just in case the above didn't work this would be the next place you might want to check. I think he had an additional error.

---

