---
title: "Power failure during software update, now can't do update"
date: 2024-07-28
forum: General Help
---

### Post by Ralph L on 2024-07-28
I foolishly tried to update my xubuntu system without plugging it in, and the battery ran out of power near the end of the update. Now when I run Software Updater, I get ```
The package system is broken
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
 The following packages have unmet dependencies:
```

I tried running apt-get install -f under Terminal and got ```

ralph@asp1:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?
ralph@asp1:~$ 

```

Anybody know how to fix my self caused problem????

---

### Post by Bashing-om on 2024-07-28
Hey Ralph L 

Exercising the package manager requires admin authority: sudo.
run the apt command as:
```

sudo apt-get install -f

```
advise of of the result.

-loosing power can make for a bigger issue-

---

### Post by Ralph L on 2024-07-29
Bashing-On:  Thanks for the reply. I am embarrassed. Thanks for reminding me to use sudo. I knew that but apparently didn't when I needed it.
Turns out that the program that got bashed was google earth. I fiddled around trying to update it, which I was unable to do (don't know why), but suddenly Software Updater began to run.

Thanks again.........

---

### Post by Bashing-om on 2024-07-29
Well Ralph L ...

lapses in memory happens to the best of us :D
Pleased to be a bit of assistance.

As you have the situation in hand -
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]Keep on keep'n on
[/INDENT]

---

