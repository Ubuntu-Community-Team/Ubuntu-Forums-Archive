---
title: "auto shut down"
date: 2007-12-21
forum: General Help
---

### Post by markp1989 on 2007-12-21
my friend uses his computer to download his torrents, and his dad goes mad if he leaves the computer on when no one is in the house, so i was wondering if there is a script that will shut the computer down automaticaly at 4:15 pm (his dad normally gets in at 5pm), unless the user stops it, perhaps a dialog box with a count down?


im not sure how i would let a script to run at a certian time, and i dont know the command to shut the computer down.

any help given will be appreciated and i thank you in advanced

---

### Post by nick_h on 2007-12-21
The easiest way would be just to use the shutdown command.
```
sudo shutdown -h 16:15
```
It will give users a warning before actually shutting down and can be cancelled with:
```
sudo shutdown -c
```
For the manual page type:
```
man shutdown
```

---

### Post by Nano Geek on 2007-12-21
I think, to do all of that, you would need to write a somewhat complex script.
Unless of course you can find a program to do that in the repositories.

---

### Post by Majin Zero on 2007-12-21
...just set a schedule in the torrent client...

---

### Post by markp1989 on 2007-12-22
> **Majin Zero said:**
> ...just set a schedule in the torrent client...

how would i go about doing that in deluge

---

