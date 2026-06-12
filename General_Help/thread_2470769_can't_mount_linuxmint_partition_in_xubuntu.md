---
title: "can't mount linuxmint partition in xubuntu"
date: 2022-01-10
forum: General Help
---

### Post by Seadevil on 2022-01-10
can't mount Linuxmint partition .  typed in  "disks"  in the search bar but nothing pops up.

anyone know how i can mount this?

nevermind,  problem solved.

---

### Post by Bashing-om on 2022-01-10
hello Seadevil

Show us what there is to work with.

Please post back - between code tags - the results of terminal commands:
```

sudo blkid -c /dev/null -o list
sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And then we can discuss the options to mount partitions,

[INDENT]there is a process
[/INDENT]

---

### Post by yancek on 2022-01-10
What search bar are you referring to?  There are numerous sites with explanations/tutorials on how to mount a partition for access such as the link below.

[https://askubuntu.com/questions/1029040/how-to-manually-mount-a-partition](https://askubuntu.com/questions/1029040/how-to-manually-mount-a-partition)

---

### Post by Seadevil on 2022-01-10
OK,  FOUND THE SOLUTION VIA GOOGLE SEARCH.   

HAD TO ENTER  GNOME-DISK-UTILTY  in the Terminal  to mount  partition.

thanks for your response.

---

### Post by Bashing-om on 2022-01-11
Seadevil; Good Deal ^

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]up up and away
[/INDENT]

---

