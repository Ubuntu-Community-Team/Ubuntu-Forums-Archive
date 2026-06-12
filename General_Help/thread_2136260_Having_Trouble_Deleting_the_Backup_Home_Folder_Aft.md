---
title: "Having Trouble Deleting the Backup Home Folder After Encrypting My Home Folder"
date: 2013-04-17
forum: General Help
---

### Post by jooge on 2013-04-17
Hi everyone,

I'm having a problem here. I just encrypted my home holder successfully and all the different tutorials that I read say that the final step is to delete the backup home folder that was created:

[[IMG]http://thumbnails106.imagebam.com/24939/e59244249387538.jpg[/IMG]]("http://www.imagebam.com/image/e59244249387538") 

It wont let me delete it by right clicking and using the drop menu. What can I do? I tryed:

sudo rm -rf /home/user.random


But it doesn't seem to work. Can someone plz help me. Thx

---

### Post by Impavidus on 2013-04-17
I guess the guide told you to delete it with sudo rm -rf user.random? It actually meant that you substitute the actual user name and random sequence:```
sudo rm -rf /home/jooge.j9ISaBtS
```unless that was an l instead of an I, I can't tell from your screenshot. Or type /home/jooge.j<tab>, it should autocomplete.

If you prefer the graphical file manager, open it from a terminal with **gksudo nautilus**. It will give you root privileges to delete that directory.

---

### Post by jooge on 2013-04-17
Awesome! Thx [**[COLOR=#000000]Impavidus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1417721") worked like a charm.:)

---

