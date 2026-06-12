---
title: "Ctrl-c does not work"
date: 2019-04-22
forum: General Help
---

### Post by rrlangly2 on 2019-04-22
I just did an update to 18.04 from 16.04 and Ctrl-c does not kill a running job. I initially noticed this when the prefix key for tmux would no longer work.

Thoughts?

---

### Post by 1clue on 2019-04-22
Why does everyone map to control-a? I haven't remapped anything, my tmux works fine.

You're likely colliding with some keyboard shortcut configured in Ubuntu. Check your keyboard control panel for shortcuts using C-a. Also check other things like window manager tweaks tool and such if you have it installed.

---

### Post by rrlangly2 on 2019-04-22
Sorry, I changed the question when I noticed it was more than tmux, and you replied at the same time. I can't even get ctrl-c to work in bash.

People change to Ctrl-a for various reasons, easy to hit ctrl-a w/ one hand instead of two, or used to it because they came from screen, etc...

---

### Post by rrlangly2 on 2019-04-22
I looked at Settings->Devices->Keyboard and see no setting for Ctrl + c. What should this be set to, to make it work in bash when killing jobs?

---

### Post by rrlangly2 on 2019-04-22
I just reset all in Settings for keyboard shortcuts and all seems well now.

---

### Post by 1clue on 2019-04-22
I came from screen, decided that rather than monkey with every one of the dozens of systems I use, I'd learn the default bindings.

Control-c being copy and having special meaning in the terminal, I'd suspect that somehow you inadvertently bumped a setting in either this version or the previous.

That, or it's possible you somehow changed keyboard layouts to something very similar to the one you use now, but slightly different.

The world may never know.

Good to hear you got it working.

---

