---
title: "To backup or not to backup"
date: 2008-02-12
forum: General Help
---

### Post by cdtech on 2008-02-12
I'm using a backup script that I wrote using tar. I have two files; do-backup and dont-backup. My question is which are the most important items to backup or what don't you need to restore a complete system from the root directory.

For example my dont-backup file includes:
```
*.mp3
*.mpg
*.avi
*.wav
*.mov
*.asf
*.rm
*.iso
*.flac
*.zip
*.exe
data.bin
/usr/local/fonts
/usr/local/games
/usr/local/j2re
/usr/local/j2re1.4.0
/usr/local/winbackup
/var/cache/apt/archives
/mnt
/backup
/dev
/var/lock
/var/run
/tmp
/var/tmp
```
I've never had to restore so far but I've kept a complete backup of my setup including an incremental (using a lastbackupdate variable). Every thing works great, I just don't want to be shocked if I do need my backup and I missed something.

You know what I mean?
Thanks........

---

### Post by apetresc on 2008-02-12
That looks pretty safe. You also don't need /proc.

Out of curiosity, how come you *aren't* backing up your .avi/.mp3/etc files? Usually those are the *only* things people tend to back up :P

---

### Post by cdtech on 2008-02-12
> **AdrianP said:**
> That looks pretty safe. You also don't need /proc.

Out of curiosity, how come you *aren't* backing up your .avi/.mp3/etc files? Usually those are the *only* things people tend to back up :P

I store all of my media stuff on my server and back it up independently. Yes those are the most important items I can't afford to lose.

---

