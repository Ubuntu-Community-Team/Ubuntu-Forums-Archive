---
title: "Broke my gnome-terminal"
date: 2018-06-11
forum: General Help
---

### Post by evespirit on 2018-06-11
Hello.
During a setup of a gameserver under my VM, I have accidentally broke the system terminal executable and was unable to repair it ever since. If anybody could post a how-to, that would be helpful. I would usually just make a new VM, but there is a ^2 crapton of things and dependancies that I have a hard time both understanding and installing, and I've barely just got it all done after 4 hours work (might be a good thing to point out that a person that is not_me.jpg would literally take like 15 minutes max.), so that's not an option.

Here is the output of xterm after running [B]git clone "the_gameserver's_gitrepo_url":
```
[/B]bash: /usr/bin/gnome-terminal: /usr/bin/python3: bad interpreter: No such file or directory[B]
```

[/B][Here]("http://ubuntuhandbook.org/index.php/2017/07/install-python-3-6-1-in-ubuntu-16-04-lts/") is also the tutorial that I have followed which very certainly was the one that broke the terminal. I have followed this one with every single command, and am suspicious of that "bug workaround".
```
python -V
```
returns
"Python2.7.15rc1", Ubuntu version should be 18.04, desktop release.

I'm pretty confident there's an easy solution to this, but I'm just too stupid to see it. Thanks.

---

### Post by evespirit on 2018-06-11
I give up.

---

### Post by QIII on 2018-06-11
Already?

---

