---
title: "Make a Terminal command run in the background?"
date: 2007-02-22
forum: General Help
---

### Post by Tipo on 2007-02-22
Hey everyone

How would I go about making a shell command run the the background?

My scenario is: I want to ssh into my ubuntu box at home, and execute a wget command to download something. However, it's a big file (an iso) and I don't want to leave my ssh session open for that long, so I want to be able to run the command in the background so I can close the session without cancelling the download...

I remember there is a character you put after the command, but can't remember what it was... and Google hasn't helped:confused:

---

### Post by nereid on 2007-02-22
Just start the command with an ampersand at the end

```

wget url &

```

The ampersand tells the shell to put it in the background. There are also some other nifty tools for that: fg, bg, jobs and the keycombo CTRL-Z (send to sleep).

jobs lists all running programms, so while wget runs in the background jobs will show this one. You can get your wget again with a fg (foreground) and the job number. With CTRL-Z you can halt the program (but not terminate it). jobs will list the program again and with the help of bg (background) you can send wget again into the background. Take a look at their corresponding manpages.

**EDIT:**
BTW have you ever heard of screen? A kind of window manager for the terminal. It allows you to run multiple terminal sessions in one terminal and you can also detach them, so they will do their work in the background (has nothing to do with the jobs background).

---

### Post by Tipo on 2007-02-22
Ahh, thanks for the good tip! :)

---

### Post by reclusivemonkey on 2007-02-22
> **nereid said:**
> Just start the command with an ampersand at the end

```

wget url &

```

**EDIT:**
BTW have you ever heard of screen? A kind of window manager for the terminal. It allows you to run multiple terminal sessions in one terminal and you can also detach them, so they will do their work in the background (has nothing to do with the jobs background).

Yes, screen is necessary for this. If the OP is loggin in over ssh, and just uses the ampersand method, then wget will go into the background, but only for the terminal he is logged into. When he logs out, that terminal will close, and wget will close. Using screen, the job will stay running and you can activate that screen again.

Incidentally, if you use wget to download a large file, and for whatever reason wget is killed, you can use the -c flag to resume downloading where you left off;

```

wget -c *url*

```

If you are going to do this a lot, its worth reading the man page for screen; its a very powerful application.

---

### Post by Tipo on 2007-02-22
Thanks for the tips on screen guys, I'll look into it.

I tried the first tip wth the & at the end, and everything seems to be working fine.  It's posting output into a wget-log, which I can view the progress by opening it in nano after logging in another time. :)

---

