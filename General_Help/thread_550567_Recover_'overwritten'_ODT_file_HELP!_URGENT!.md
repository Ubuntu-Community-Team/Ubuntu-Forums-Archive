---
title: "Recover 'overwritten' ODT file? HELP! URGENT!"
date: 2007-09-14
forum: General Help
---

### Post by helwitch on 2007-09-14
I just accidentally 'overwrote' several weeks of biology notes, by copying a file of the exact same name into the same directory, only the copied file was several weeks older. the file type was ODT, which photorec apparently won't search for. Is there any way I can try and find this? I did debugfs lsdel, it said 0 deleted inodes found. 
Edit-I've come to the conclusion I'm out of luck, since debugfs found 0 deleted inodes. I'm gonna go sleep a bit, to prepare for going through the text book trying to recreate my notes.

---

### Post by dcstar on 2007-09-14
> **helwitch said:**
> I just accidentally 'overwrote' several weeks of biology notes, by copying a file of the exact same name into the same directory, only the copied file was several weeks older. the file type was ODT, which photorec apparently won't search for. Is there any way I can try and find this? I did debugfs lsdel, it said 0 deleted inodes found. 
Edit-I've come to the conclusion I'm out of luck, since debugfs found 0 deleted inodes. I'm gonna go sleep a bit, to prepare for going through the text book trying to recreate my notes.

There may be a file with a "~" sufffix (that is not displayed by default), that is a backup version of an edited file.

Open a terminal window in that directory and do:
```
ls -al
```

---

### Post by splintercellguy on 2007-09-14
> **helwitch said:**
> I just accidentally 'overwrote' several weeks of biology notes, by copying a file of the exact same name into the same directory, only the copied file was several weeks older. the file type was ODT, which photorec apparently won't search for. Is there any way I can try and find this? I did debugfs lsdel, it said 0 deleted inodes found. 
Edit-I've come to the conclusion I'm out of luck, since debugfs found 0 deleted inodes. I'm gonna go sleep a bit, to prepare for going through the text book trying to recreate my notes.

The lesson you should learn from this experience: keep backups, no excuses.

---

