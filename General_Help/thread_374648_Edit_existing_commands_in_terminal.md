---
title: "Edit existing commands in terminal"
date: 2007-03-02
forum: General Help
---

### Post by NZ-Wanderer on 2007-03-02
Hi all, Just wondering if there was a way to edit the list of commands that you have typed into terminal???

to explain a little further, everything you type into Terminal is saved, so that if you do an Uparrow at terminal prompt it scrolls though all the previous commands that you have typed in..
What I would like to do (if possible) is to actually edit some of the commands out of it, I'm guessing that the list of commands is saved somewhere as it always remembers them even after re-installs of Kubuntu/Ubuntu..
Problem is I wouldn't know ehere to start looking (although I presume it has to be somewhere in my home/john partition...

Could anyone help locate this please???

---

### Post by taurus on 2007-03-02
I think you are talking about the ~/.history.

```
nano ~/.history
```

---

### Post by flyingbrass on 2007-03-02
You can clear your history by typing:

history -c

Edit: That doesn't clear everything out of .bash_history.  Maybe it's only for the current session.

---

### Post by NZ-Wanderer on 2007-03-02
thanks for the quick replies....

I don't have a .history - but in my home/john partition I do have a .bash_history which does contain a lot of the commands I have used (could this be it?)

I don't want to clear the whole history of what I typed, just edit out all the mistakes I made :) :)

---

### Post by taurus on 2007-03-02
Yes, it's the same thing.

```
nano ~/.bash_history
```

---

### Post by NZ-Wanderer on 2007-03-02
Many thanks, will edit that file and get rid of all the mistakes I typed into it :)

---

### Post by flyingbrass on 2007-03-02
Editing .bash_history won't change the items displayed with the up arrow.  The current history is cached.

You can remove specific entries with:

history -d <number of the entry>

---

### Post by NZ-Wanderer on 2007-03-02
Ahh, that explains why my latest commands aren't in the list...

I presume that if I reboot my computer the cache will be saved to the bash_history file which I will be able to edit the new stuff after reboot :)

> **flyingbrass said:**
> Editing .bash_history won't change the items displayed with the up arrow.  The current history is cached.
You can remove specific entries with:
history -d <number of the entry>

---

