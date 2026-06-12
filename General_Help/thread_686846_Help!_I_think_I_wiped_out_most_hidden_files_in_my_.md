---
title: "Help! I think I wiped out most hidden files in my home folder!"
date: 2008-02-03
forum: General Help
---

### Post by Pichu0102 on 2008-02-03
I was trying to test out a backup script that I had changed a variable in (made it a hostname instead of ip address) and screwed up big time.

I was testing this in a leftover terminal from before
rsync -e ssh -varuzP --delete /home/pichu0102/ kids-laptop.local:/media/disk/pichu0102

What I didn't realize, was that I wasn't logged into this computer (pichu0102-laptop2) and instead was in an SSH session with kids-laptop. All of a sudden, I see it deleting tons of things and quickly kill the process, but it had just finished deleting the .wine folder.

How badly did I mess up my computer (pichu0102-laptop2)? Will I have to grab the backup files off my backup computer?

---

### Post by PinkFloyd102489 on 2008-02-03
If have a backup, just restore it. Also, most of the hidden folders in the home dir are just personally tweaked versions of /usr/share/.

---

