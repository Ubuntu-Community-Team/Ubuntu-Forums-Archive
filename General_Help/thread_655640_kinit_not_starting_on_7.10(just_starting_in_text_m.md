---
title: "kinit not starting on 7.10(just starting in text mode)"
date: 2008-01-01
forum: General Help
---

### Post by dopple on 2008-01-01
Hi folks. I have had my gutsy gibbon installation working fin but all of a sudden it's not working. I think I have had some updates recently but can't say for sure.
I have googled it and tryed
```
sudo /etc/init.d/gdm start
```
and it says "*Starting GNOME Display Manager" but nothing actually happens.

As it's starting I get the lines

kinit: trying to resume
kinit: No resume image, doing normal boot

then I am asked to log in.

This irritates me as I am forced to use windows and am trying to convince myself to eliminate windows from my machine altogether (almost have no reason to keep windows... yay!)

---

### Post by dopple on 2008-01-02
bump

---

### Post by pointone on 2008-01-03
The kinit lines are just Ubuntu searching for a resume image that would have been created if you used the hibernate feature. This isn't your problem.

However, you still haven't explained what your problem is. "It's not working" is simply far too vague for anyone to offer you any help. What exactly happens when you try to boot?

---

### Post by dopple on 2008-01-03
Sorry. Basically when I start up, the spash screen with the loading bar will display and it looks like all is well, then it seems to change to verbose mode (I think that's the term when it starts telling you what is being started and all lines end in [OK].

Well eventually, it prompts me for my login details and stays in text mode. I have tried a few things to get the gui desktop working but nothing has helped so far. I will post further results back tonight when I get back to my laptop (I'm at work just now).

---

### Post by Thug14 on 2008-01-14
I get the same error; until recently i have been using feisty fawn with no problems at all.The problem started after I upgrade to gutsy, and I havent been able to start Gutsy normally ever since.It asks for the login details as mentioned above and stays in the text mode only.

Mine is a Dell Inspiron 6000 with an Ati X300 card

---

