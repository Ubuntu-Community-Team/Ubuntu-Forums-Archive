---
title: "trouble with vi"
date: 2013-01-16
forum: General Help
---

### Post by ZenMasta on 2013-01-16
Having trouble using vi.

I'm trying to edit a conf but after I press insert pressing the arrow keys in attempt to move the curosr instead inserts characters.

Up arrow = A
Down Arrow = B
Right Arrow = C
Left Arrow = D

Normally when I you press Insert (on other servers etc), the lower left corner usually toggles between --INSERT-- or --REPLACE--.

And right now it does not say anything when I press insert.

---

### Post by percent20 on 2013-01-16
try pressing `i` or `a` to get into insert mode. Also `h`, `j`, `k`, and `l` move you around when not in insert mode.

---

### Post by r-senior on 2013-01-16
> **ZenMasta said:**
> Having trouble using vi.
Arrow keys work OK in insert mode for me on 12.04. What do you get if you run this?

```
ls -l /etc/alternatives/vi
```

---

### Post by ZenMasta on 2013-01-16
I'm running 12.10 it's only a couple weeks old.
zen@zen-RJ181AA-ABA-a1600n:~$ ls -l /etc/alternatives/vi
lrwxrwxrwx 1 root root 17 Dec 12 07:42 /etc/alternatives/vi -> /usr/bin/vim.tiny
zen@zen-RJ181AA-ABA-a1600n:~$

---

### Post by 3246251196 on 2013-01-16
> **ZenMasta said:**
> I'm running 12.10 it's only a couple weeks old.
zen@zen-RJ181AA-ABA-a1600n:~$ ls -l /etc/alternatives/vi
lrwxrwxrwx 1 root root 17 Dec 12 07:42 /etc/alternatives/vi -> /usr/bin/vim.tiny
zen@zen-RJ181AA-ABA-a1600n:~$

You have the "tiny" version of VI which is the cause of this, I believe.

I also believe you do not get the "improved" version as standard. Either way, it is part of the standard repository. You should remove your current version and

```
sudo apt-get install vim
```

---

### Post by ZenMasta on 2013-01-16
That's strange but thanks. All good now :)

---

### Post by jonobr on 2013-01-16
`h`, `j`, `k`, and `l` on old keyboards used to have arrows on them, thats why they were used.

I remember my first vi class, the guy said 'l' moves the cursor right, I thought "what genius though this up"
Now that Im feeling old, Ill put on my slippers, sit by the fire and recount old times......

---

### Post by efflandt on 2013-01-17
I normally do not use vi, but ran across this on a Raspberry Pi that runs an arm version of Debian wheezy. Apparently that is the same in my Ubuntu 12.04.

With the default setup, if you run it as **vi**, it acts like vi and arrow cursor keys to not work, unless you do **:set nocp** to put it into vim mode.   It tells you that right on the opening screen if no file is in the command line.

If you run it as **vim.tiny** then cursor keys do work.  Or to make that simpler to type do **sudo ln -s /usr/bin/vim.tiny /usr/bin/vim**

---

