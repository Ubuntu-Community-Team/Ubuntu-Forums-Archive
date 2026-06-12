---
title: "Windows partition and user access"
date: 2007-02-15
forum: General Help
---

### Post by tylersontag on 2007-02-15
I put all my music as a backup of my desktop on my windows partition on my laptop.  I like listening to it but the problem is that since its on my windows partition, i can only access it by running amarok through "sudo amarok" in the shell.  what i'd really like to do is copy those files to my linux partition and make them accessable by my default user name.  but in addition to not knowing how to change access, im having trouble actually copying them over, i run sudo nautilus and copy all of them, but when i root up out of my windows partition i can't paste them, the paste cache is just empty.

just mostly looking for suggestions on this one.

---

### Post by robcarr2 on 2007-02-15
If you just want to copy all your MP3s from your Windows partition to your Linux partition try this:

mkdir MP3s
sudo cp /media/WindowsPartition/*.mp3 ~/MP3s

Hope this helps

---

