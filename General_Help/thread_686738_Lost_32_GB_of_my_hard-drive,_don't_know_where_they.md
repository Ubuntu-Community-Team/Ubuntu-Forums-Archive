---
title: "Lost 32 GB of my hard-drive, don't know where they are!!!"
date: 2008-02-03
forum: General Help
---

### Post by juanm on 2008-02-03
Hello,
I was trying to free some memory from my hard drive, so I decided there were a bunch of backups that were not useful anymore, so I proceeded to delete them. However, the backup program was not deleting them, and I decided to sign in as root and send to the trash the files. I sent them, but to my surprise, the Disk Usage Analyzer tells me that my hard drive is 32GB less than what i is supposed to be. That was the exact figure of data that I deleted from the backups. 
I believe I really screwed up with this one.
Thanks.

---

### Post by LaRoza on 2008-02-03
Empty the trash.

---

### Post by forestpixie on 2008-02-03
have you checked that they're not in root's trash - sending them to trash won't delete them till you empty it

SNAP :D

---

### Post by flamer on 2008-02-03
Go to the terminal and type

```
sudo apt-get autoclean && sudo apt-get clean
```

---

### Post by juanm on 2008-02-04
Hi people,
thank you for your replies. Yes, the first thing I did was to empty the trash, and then I ran autoclean, autoremove, and I even removed orphan packages. 
I just signed in as root but there is no trash to be emptied.
Any more ideas? Thanks in advance.

---

### Post by CupofDice on 2008-02-04
Try baobab. I think it comes with gutsy, but I may have downloaded it from the repository. Either way, just type baobab in the terminal, and scan your home and file system to see what is taking up your space. Also the trash in root is located at /root/.Trash. Show hidden folders to see it.

---

### Post by juanm on 2008-02-05
Thank you CupofDice, I was able to do it at last. I just forgot to show the hidden files while I was root. Simple, yet great solution. I can feel stupid from now on, and the topic can now be closed.
Thanks.

---

