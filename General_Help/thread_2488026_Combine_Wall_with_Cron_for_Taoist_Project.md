---
title: "Combine Wall with Cron for Taoist Project"
date: 2023-06-20
forum: General Help
---

### Post by mrbenmould on 2023-06-20
Sup peeps, love yall, been reading your advice forev but never bothered to actually ask for help. I'm not the worlds best linux user, which is sad because i've been using it for over a decade now. Anywhoo, I wrote a personal translation of the Dao De Jing, and I want to use the wall command or some other command to display each of the chapters on an hourly basis. I've tried combining wall with cron but it hasn't seem to work out, I think I will find out at the top of the next hour, cross my fingers. Thanks yall, you is the bestest.

---

### Post by MAFoElffen on 2023-06-21
How do you have the text that you want to send as a message to 'wall' stored? I'm thinking what would be best is either snippets in files or in a database...

The wall command syntax wise is (from the man page)
```

wall [-n] [-t timeout] [-g group] [message | file]

```
So if it were stored in files, and in a script, you randomized the calling of which file is going to be displayed, then that script could be called from cron each hour.

That is the basic logic I see to do that.

On the other hand, if the quotes are stored as one liners, in one file, then this would work using 'wall' and 'rl' (RE: [https://manpages.ubuntu.com/manpages/trusty/man1/rl.1.html](https://manpages.ubuntu.com/manpages/trusty/man1/rl.1.html)) form crontab:
```

0 * * * * /usr/bin/wall -n $(/usr/bin/rl -c 1 /home/UserName/Documents/DaoDeJing.txt)

```
But the last time I saw that utility, was in the 20.04 Repo's in package  randomize-lines_0.2.7_amd64... I don't see that in the repo's for 22.04.

EDIT:
Utility 'shuf' does the same thing (RE: [https://manpages.ubuntu.com/manpages/jammy/man1/shuf.1.html](https://manpages.ubuntu.com/manpages/jammy/man1/shuf.1.html))
```

0 * * * * /usr/bin/wall -n $(/usr/bin/shuf -c 1 /home/UserName/Documents/DaoDeJing.txt)

```

---

