---
title: "Setting a shortcut key for Terminal Reset"
date: 2017-04-23
forum: General Help
---

### Post by mikeglaz on 2017-04-23
I tried setting the Terminal Reset shortcut key to Ctrl+K but then when I try it, it doesn't work.  Only typing 'reset' works.

---

### Post by #&amp;thj^% on 2017-04-23
Maybe try a differnt key combo...For myself I use>> "Ctrl+Shift+e"

---

### Post by mikeglaz on 2017-04-24
That doesn't work.  What I realized as well, is that from the menu, Terminal->Reset doesn't work either, regardless of whether a key is assigned to it or not.

---

### Post by #&amp;thj^% on 2017-04-24
What Terminal are you using? IE (gnome-terminal, xfce4-terminal, mate-terminal)
Probably doesn't matter for most users, but the behavior of reset is dependent on the terminal.
For example my mate-termnal I have to use A combo of "Ctrl+L"
And the **"reset"** works here for mate-terminal.

---

### Post by mikeglaz on 2017-04-24
gnome-terminal

---

### Post by #&amp;thj^% on 2017-04-24
> **mikeglaz said:**
> gnome-terminal

Curious??...as that was the terminal that was displayed in my screenshot above.
have you tried the "Ctrl+L" combo yet?

---

### Post by mikeglaz on 2017-04-24
Ctrl+L does a 'clear', I need it to do a 'reset'.

---

### Post by #&amp;thj^% on 2017-04-24
Well now I'm kind of at a loss here...but there is  amore aggressive approach...But:
Please be aware your mileage may vary here...so use at your own risk    
I have run these commands myself with no ill effects on my end...so it should be ok for others that have not made any changes to their system...IE "~.bashrc"
Ubuntu 16.04

This simple command works in Ubuntu 16.04.

```
dconf reset -f /org/gnome/terminal/legacy/profiles:/
```

Reset only the default profile

However, if you want to reset only the default profile, which uses UUID b1dcc9dd-5262-4d8d-a863-c897e6d979b9 by default, you can use

```
dconf reset -f /org/gnome/terminal/legacy/profiles:/:b1dcc9dd-5262-4d8d-a863-c897e6d979b9/

```
For Unity
Fingers Crossed:)
EDIT: BTW have you changed or added to your ~.bashrc file?

---

### Post by vasa1 on 2017-04-24
See if [https://askubuntu.com/questions/25077/how-to-really-clear-the-terminal](https://askubuntu.com/questions/25077/how-to-really-clear-the-terminal) helps. One comment suggests the use of "tput reset" .

---

### Post by mikeglaz on 2017-04-25
In gnome-terminal from the menu, Terminal > Reset does nothing.  But Terminal > Reset and Clear works.  So I'll just map a hotkey to this.

---

