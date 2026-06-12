---
title: "Delete Terminal history?"
date: 2012-11-14
forum: General Help
---

### Post by PDA1 on 2012-11-14
How do I easily and permanently delete the Terminal history (all of the stuff I've typed in Terminal)?

Thanks

---

### Post by pqwoerituytrueiwoq on 2012-11-14
[Alt]+[F2]
```
rm ~/.bash_history
```

---

### Post by PDA1 on 2012-11-14
I tried your commands but when I type "history" I still see all of the commands I've entered.

Any ideas?

---

### Post by pqwoerituytrueiwoq on 2012-11-14
if the terminal was open when you ran that that is expected, new windows should be empty
if you run **rm ~/.bash_history** in a termnal and type exit yuor history will have exit and rm ~/.bash_history

---

### Post by Stonecold1995 on 2012-11-15
Every time you exit a Terminal session, it saves the history to ~/.bash_history (that's to prevent multiple Terminal instances' history from interfering).  So if you have a lot of history and then do "rm ~/.bash_history" but then you exit, everything you typed into the current session (including "rm ~/.bash_history") will be saved to a new history file.  You have to do this to remove it all:
1) Exit any of your current Terminal sessions (which saves it to ~/.bash_history)
2) Open a new Terminal session and run "rm ~/.bash_history"
3) Exit that session

That should work.  One thing I do if I don't want everything I typed in one session to be saved is I run "kill -9 $$" instead of exit.  That forcibly kills the bash process and causes it to crash and close Terminal without saving history, while still preserving history from past sessions (kind of like an "incognito mode" for Terminal).  I wouldn't always recommend that though because it kills bash, so if bash is trying to save anything that data might be corrupted, though I've never had a problem.

---

### Post by stinkeye on 2012-11-15
Edit: ALREADY SAID.

---

### Post by Impavidus on 2012-11-15
If you issue the command```
HISTFILE=
``` during your session the history won't be saved either. I thinks it's a cleaner way. Putting```
export HISTFILE=
``` in your .bashrc file disables your history permanently.

---

### Post by mörgæs on 2012-11-15
I believe that you can just type 

```
history -c
```

but I'm not on Buntu now so can't test it.

---

### Post by VooDooSyxx on 2012-11-15
> **mörgæs said:**
> I believe that you can just type 

```
history -c
```but I'm not on Buntu now so can't test it.


Yep it'll work. That's a built-in of the bash shell so it doesn't matter what distro it is, as long as bash is the login shell.

---

### Post by mc4man on 2012-11-15
history -c will only 'delete' the history of the current open terminal not clear ~/.bash_history

As mentioned just delete ~/.bash_history

---

### Post by Lyfang on 2012-11-29
BleachBit can delete the Terminal history too.

---

