---
title: "any way to 'restore' broken things after a crash?"
date: 2007-06-26
forum: General Help
---

### Post by hsarcrebyc on 2007-06-26
I had a small video card problem, didn't get any output while booting so without knowing that the boot process was actually fine I resetted my pc while it must have been in the middle of booting into ubuntu.

Some things I fixed but some things are still 'broken', I have to set my keyboard to azerty every time I boot up and log in, my nvidia drivers didn't work anymore but I reinstalled them and now they're fine. I'm sure there's more stuff still glitched though. 

My question is: what's the best solution? I would think there must be something better than a reinstall.

---

### Post by AlexThomson_NZ on 2007-06-27
Re-installing is not too major is it?  I try to keep my stuff (themes, docs, music, etc.) on another partition, so doing re-installs is pretty painless.  Personally I HATE having an uncertain system, as if anything goes wrong, it's always in the back of my mind.  If I was in your shoes, I'd backup and re-install...

---

### Post by charleseddy on 2007-06-27
Right, unlike Windows, there's no system restore function.  It'd be pretty hard to make, I'm sure, considering the different directory structure . . .  The best I can offer you is a reinstall, or the endurance to take a long, slow repair process.  Thanks,

ce

---

### Post by hsarcrebyc on 2007-06-27
I was thinking more along the lines of maybe there's a function that thoroughly checks the integrity of all installed packages or that just reinstalls all packages. But yeah, a reinstall isn't that bad.

---

### Post by charleseddy on 2007-06-27
You can run these three commands:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get --fix broken

Those will clean it out a little bit and possibly help with *some* of your problems, but to check the integrity you'd have to have a checksum for your filesystem, which changes on a day to day basis.

ce

---

### Post by Qu4k3R on 2007-06-27
What are those broken things ?

EDIT:
You could start your session as the failsafe session.
You could also start your session within those framebuffer terminals with Ctrl+Alt+Fx  ("x" stands between 6 and 1)
Then repair the machine.
:popcorn:

---

### Post by hsarcrebyc on 2007-06-27
> **Qu4k3R said:**
> What are those broken things ?

EDIT:
You could start your session as the failsafe session.
You could also start your session within those framebuffer terminals with Ctrl+Alt+Fx  ("x" stands between 6 and 1)
Then repair the machine.
:popcorn:

Define 'repair the machine'.

---

### Post by DougieFresh4U on 2007-06-27
I always do a:
[B]sudo apt-get update
sudo apt-get -f install
sudo dpkg --configure -a[/B]

Good luck

---

### Post by dabl on 2007-06-27
> **DougieFresh4U said:**
> I always do a:
[B]sudo apt-get update
sudo apt-get -f install
sudo dpkg --configure -a[/B]


Yep, those are good.  And then I finish it with

```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```
:D

---

### Post by Qu4k3R on 2007-06-28
are apt-get and dpkg commands working ?

You can also:
> 
cat ~/.bash_history

To see the last commands that you have given to the terminal.

---

