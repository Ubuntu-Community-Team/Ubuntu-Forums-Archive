---
title: "Reset Password without reboot or sudo"
date: 2015-01-11
forum: General Help
---

### Post by hailholyghost on 2015-01-11
Hello,

I forgot my password, which is also the root password to my linux box at work.  I can still log in remotely and get shell access.  I don't enter password at login because I use sshkeys (perhaps this is how I can get the password back?)

I cannot reboot because people are using the machine, and I don't have root access anyway.

I am getting desperate, and I realize this is my own fault for not writing it down.

any help is appreciated,
-Dave

---

### Post by ajgreeny on 2015-01-11
Are there any other admin users on that machine that could be persuaded to reset your user password on your behalf with a temporary password, and  then, for security, you can immediately change it to something else known only by you.

Of course, if it is essential that you get back to your original password you may have a problem.

---

### Post by llamabr on 2015-01-11
You don't need sudo to change your password once you're logged in.  Just issue the passwd command.

---

### Post by Mark Phelps on 2015-01-11
> how I can get the password back?

Basically -- you can't!  

So-called password recovery apps only allow you to blank or reset an existing password, not recover it.

Also -- been a while since I used the "passwd" command, but (as indicated in the linked description), it firsts prompts for the EXISTING password -- which, if you don't get it right, I believe exits the command:  [http://manpages.ubuntu.com/manpages/hardy/man1/passwd.1.html]("http://manpages.ubuntu.com/manpages/hardy/man1/passwd.1.html")

---

### Post by deadflowr on 2015-01-11
> **llamabr said:**
> You don't need sudo to change your password once you're logged in.  Just issue the passwd command.

You still need to enter the old password...

---

### Post by hailholyghost on 2015-01-11
hello deadflowr, llamabr, and ajgreeny,

it looks like I'm going to have to talk to the other user in real life and ask him when I can reboot and go through standard password reset procedures.  Otherwise I have to bring my laptop in every day to log in with ssh keys, which is silly.

I've been using Ubuntu for 8 years now and never had this problem... lesson learned.... I got overconfident.

-Dave

---

### Post by hailholyghost on 2015-01-15
Hello,

I found a solution to this this morning:

if you logged in with ssh keys, all you have to do is tarball your ~/.ssh directory and copy to a new computer to log in.  I think of the .ssh directory as like the password I forgot.

An additional solution to my problem, which is gone now, thank God.

-Dave

---

