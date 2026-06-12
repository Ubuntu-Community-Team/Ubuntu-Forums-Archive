---
title: "[SOLVED] Clear command history of another user"
date: 2008-06-19
forum: General Help
---

### Post by picopir8 on 2008-06-19
Is there any way to clear another users history without first using su to become that user and then running history -c?  I can not use su because I am putting this within a bash script and when I exit from the su, the script thinks that it should terminate.  The script will run with root privileges.

I tried:
sudo -u USERNAME history -c

but that does not work.  the history command can not be found when called via sudo.

Any suggestions?

---

### Post by mempman on 2008-06-19
If you are using firefox...then i guess you could go into /home/user/.mozilla/profiles/something/something... and delete the history.  Sorry, i don't know the exact location (im currently on windows) but im sure it can be done this way.

---

### Post by bodhi.zazen on 2008-06-19
-deleted-

```
sudo -u USERNAME bash -c "builtin history -c"
```

---

### Post by lswb on 2008-06-19
If you are referring to the user's shell command line history, for bash it is kept in ~/.bash_history. So if your your script is running as root you could just delete that file in the users home directory.

---

### Post by bodhi.zazen on 2008-06-20
> **lswb said:**
> If you are referring to the user's shell command line history, for bash it is kept in ~/.bash_history. So if your your script is running as root you could just delete that file in the users home directory.

That was my thought, but if you do that bash does not automatically make a new

.bash_history

so you could :

echo "" > ~USERNAME/.bash_history

---

### Post by picopir8 on 2008-06-20
Thanks!  Wiping .bash_history did the trick.  There is one small difference vs running "history -c" which I can live with but is worth mentioning.  That is, any open terminal windows or ttys will have their histories cached.  So the change will only effect new terminal windows/ttys.  Good enough for my application though!

---

### Post by ddales on 2008-06-20
cat /dev/null > /home/username/.bash_history

---

