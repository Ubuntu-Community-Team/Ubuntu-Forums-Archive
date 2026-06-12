---
title: "Opensuse, pageup bash"
date: 2017-07-12
forum: General Help
---

### Post by biz122 on 2017-07-12
Hello everyone,

Recently I was on opensuse doing things, and noticed that you could use PageUp in the terminal to jump to the last used command if you started to type it.

Like say I entered $ ssh example.com
Then I type $ ssh[PageUp] and it jumps to $ ssh example.com

What is this and how do I get this neat functionality into my ubuntu laptop?

Cheers

---

### Post by Habitual on 2017-07-12
```
### bind fix for interactive shell history
iatest=$(expr index "$-" i)
if [[ $iatest > 0 ]]; then bind '"\e[A": history-search-backward'; fi
if [[ $iatest > 0 ]]; then bind '"\e[B": history-search-forward'; fi
```

in your ~/.bashrc
After editing, **reload ~/.bashrc** several ways, easiest is 
close terminal and re-open terminal
A more direct method in the same session would be to issue
```
source ~/.bashrc
``` a "more diirect method" I mention may include a non-GUI situation.
I have used this code snippet for 7 years now and I hope you find it as useful as I have.

up and oh yeah, down works also, should you scroll too far. ;)
The keys are Up Arrow and Down Arrow for the above code.
ssh <up arrow> 
IDK how to "map" PageUp/PageDown to do as you have asked. Sorry about that.

---

### Post by biz122 on 2017-07-13
Thanks man!

> I have used this code snippet for 7 years now and I hope you find it as useful as I have.
I have no doubt! It will save me a few minutes here and there entirely out of my *convenience -* I think that's pretty cool :)

I did some searching and found the pgup/pgdown-way, shall anyone be interested:

> 
# bind fix for interactive shell history (pgup/pgdown)
if [[ $iatest > 0 ]]; then bind '"\e[5~": history-search-backward'; fi
if [[ $iatest > 0 ]]; then bind '"\e[6~": history-search-forward'; fi


Cheers

---

### Post by Habitual on 2017-07-13
You are welcome.
And good work finding the Page{Up,Down} codes"
Glad it worked out.

---

### Post by efflandt on 2017-07-13
Up/Down cursor keys are the default method in **bash** to bring up previous commands from history (up to go back). But that is not necessarily a default for other shells. 

Shift+PgUp/Shift+PgDn can navigate previous pages of terminal output that are still in the terminal buffer (in terminal "window" mouse wheel or scrollbar can do that as well).

---

