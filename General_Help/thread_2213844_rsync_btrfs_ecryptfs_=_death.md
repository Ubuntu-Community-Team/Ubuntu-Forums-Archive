---
title: "rsync btrfs ecryptfs = death?"
date: 2014-03-28
forum: General Help
---

### Post by reyals140 on 2014-03-28
So I'm running a back up script snd when it's backing the .Private folder it nearly dies
rsync -a /home/.ecryptfs/<username>/.Private /media/backups
It runs at an amazingly slow 2MB/s

However if I run rsync on the home folder it works fine
rsync -a /home/<username> /media/backups
I get a much more reasonable 30MB/s

To make matters weirder if I rsync to a remote computer
rsync -a -e ssh 192.168.1.21:/home/.ecryptfs/<username>/.Private ~/test
I get a little slower, but still about 15MB/s

/home is on a single btrfs disk and /media/backups is a 3 disk btrfs array

Thoughts?

---

