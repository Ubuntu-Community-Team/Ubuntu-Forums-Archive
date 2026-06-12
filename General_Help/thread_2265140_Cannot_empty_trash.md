---
title: "Cannot empty trash"
date: 2015-02-12
forum: General Help
---

### Post by findingthebalance on 2015-02-12
Ubuntu 14.04. Just started happening, I am unable to completely empty the trash and when I try, my computer freezes. I used the terminal to empty the trash and some folders did delete, but some folders still won't go and when I try my computer freezes. What can I do?

---

### Post by v3.xx on 2015-02-13
A bit drastic, but you are stuck. 
Mount the file system with the live dvd and then remove the trash.

---

### Post by findingthebalance on 2015-02-13
What do you think is causing the problem?

---

### Post by MrSteve on 2015-02-13
please try this command in a terminal ...

sudo rm -rvf .local/share/Trash/

---

### Post by findingthebalance on 2015-02-14
Thank you MrSteve. I am running that now, it is taking a fair bit of time to complete, is it supposed to?

---

### Post by findingthebalance on 2015-02-14
Just finished took awhile and it worked. Note to anyone else having a similar problem it did take a bit to get started and to finish, around an hour for me, so just let it run.

Thank you again

---

### Post by haplorrhine on 2015-02-14
I had this problem after unmounting a flashdrive that I had deleted files from, although it fixed after reboot.  Perhaps because I removed the index of the file but not the actual file data.

---

### Post by lisati on 2015-02-14
> **findingthebalance said:**
> What do you think is causing the problem?

> **findingthebalance said:**
> Thank you MrSteve. I am running that now, it is taking a fair bit of time to complete, is it supposed to?

Were there a lot of files in the trash? If so, it could have slowed things down while your system did its preliminary preparations for emptying the trash.

---

### Post by findingthebalance on 2015-02-14
[COLOR=#000000][FONT=Verdana]There were only five files in the trash. There was a file named "FtZ1" I have no idea what the file was as every time I tried to look in it or empty the trash my computer would freeze and so when I ran terminal to delete the trash folder almost every file that was being deleted started with the name "FtZ1 ", and there seemed to be hundreds. It is now gone, but I still do not know what the file was.[/FONT][/COLOR]
Cheers

---

### Post by v3.xx on 2015-02-14
Don't forget :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by daveharas on 2015-05-09
Mr Steve - Thank you, this solved a problem I was having with my recycle bin also. I have made a note of the command just in case I have the same issue in the future.

:D:D:D:D:D:D

---

