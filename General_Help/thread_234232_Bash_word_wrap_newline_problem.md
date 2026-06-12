---
title: "Bash word wrap newline problem"
date: 2006-08-11
forum: General Help
---

### Post by Bigglez on 2006-08-11
Hi - I have searched and googled but to no avail.

I am on Kubu 6.06 with all the updates done.

When I open a terminal and type a long command -- as it gets to the right-hand side, it wraps around but does not go down one line, so the text continues over the line already typed.
Pressing Enter runs the command ok, so it's only a visual thing.

This happens in Konsole, Xterm as well as a normal tty text screen.

Any clues?

---

### Post by Bigglez on 2006-08-11
It seems to be my custom prompt:

```
PS1='\033[01;32m\W\033[00m\]:\$ '
```

What do I add to that to make it work?

---

### Post by mlind on 2006-08-11
Edit your ~/.bashrc file to include that. Search the section where PS1 is defined.

---

### Post by Bigglez on 2006-08-11
mlind, thanks-ish.
I listed my PS1 string in the second post. Is there something wrong with it? I'm pretty sure that the problem lies there!

---

### Post by BoneKracker on 2006-08-17
I had a similar problem with the shell is incorrectly determining the space left on the line.  It started doing this as soon as I added color to my PS1 prompt.  Simply put, it thinks the non-printing characters take up space on the screen, but they don't.

To correct this, I identified the non-printing characters by enclosing each non-printing portion of your prompt within an additional set of codes (kind of like brackets).  The codes used for this are \[ and \].

So, for example, instead of:> PS1='\033[01;32m\W\033[00m\]:\$ '

Use:
```
PS1='\[\033[01;32m\]\W\[\033[00m\]:\$ '
```

Also, if you're using a recent version of Bash, you can use e instead of 033:
```
PS1='\[\e[1;32m\]\W\[\e[0;0m\]:\$ '
```

---

### Post by Bigglez on 2006-08-17
Thanks! Great info. 

Could you enlighten me as to what all the Debian-chroot stuff is in this example:
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\W\[\033[00m\]:\$ '

Ah, my prompt is healthy again. I am so happy :)

---

