---
title: "Launchers for application in terminal suddenly don't work."
date: 2007-09-27
forum: General Help
---

### Post by AlchemyMan on 2007-09-27
I made an application launcher to run an app in terminal the other day and everything worked fine. Then I log in again today, and suddenly that same launcher is giving me an error -

Failed to execute child process "-x" (No such file or directory)

It does this consistently. I haven't altered the launcher in any way. The only things I've done since then are installing an update, and trying to play with compiz fusion (still can't get it to work). Aside from that, I don't know what the issue is.

Anyone have any ideas?

---

### Post by DagMan on 2007-09-27
It sounds like it's trying to execute the following 

**gnome-terminal -x name-of-program**
but something was messed up in the update.  Perhaps if you make the laucher actually say the above and don't select the 'run in terminal' option it will work.  It won't hurt to put quotes around the command to run if it has spaces.

example:
```
gnome-terminal -x "name-of-program --option1 --option2"
```

---

### Post by AlchemyMan on 2007-09-27
That worked quite well! Thanks. 

I do hope they fix whatever it is that's gone wrong by the next update, but this method seems just as good for the moment. 

Once again, thanks.

---

### Post by pPrdrm on 2007-10-02
Hi AlchemyMan,
I had the same problem and it was driving my crazy, but I thing I may have found what was going wrong. Check this thread: [[COLOR="Red"]http://ubuntuforums.org/showthread.php?p=3464685#post3464685[/COLOR]]("http://ubuntuforums.org/showthread.php?p=3464685#post3464685") I've made and the solution I've fount. Maybe it's what you're looking for. Please let us know if it helped.

---

### Post by louisgag on 2007-10-03
> **DagMan said:**
> It sounds like it's trying to execute the following 

**gnome-terminal -x name-of-program**
but something was messed up in the update.  Perhaps if you make the laucher actually say the above and don't select the 'run in terminal' option it will work.  It won't hurt to put quotes around the command to run if it has spaces.

example:
```
gnome-terminal -x "name-of-program --option1 --option2"
```

I had the same problem and your solution fixed it! Thanks DagMan

---

### Post by ofm on 2007-10-09
I think I'm having the same or similar problems.
I'm just trying to create a launcher to watch my mail log..should be pretty simple right?  If I use:
```
gnome-terminal -x "/usr/bin/tail -n0 f /var/logmail.log"
```

I get "there was an error creating the child process for this terminal."  (Same thing with single quotes).
When I tried the same command with x-terminal-emulator -x, I get a new terminal window, but no process (with and without quotes).  If I try it with x-terminal emulator -e, I get the same child process error.  

Yes, as you can probably tell I'm fairly new to daily *NIX usage.

I've also tried just creating a file with echo <command> > file, and allowing that to be executed & then clicking on it.  That just gives me a terminal with a flashing cursor.

---

