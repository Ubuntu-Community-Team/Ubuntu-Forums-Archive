---
title: "[SOLVED] Program on terminal"
date: 2008-04-29
forum: General Help
---

### Post by rolodoom on 2008-04-29
How can I run a program from the terminal, and send it automatically to background so the terminal line is available again for another command??

---

### Post by forrestcupp on 2008-04-29
As far as I know, you can't do it.  The terminal is used the entire time the program is running to give any error output for anything that happens the entire time the program is running.

The next best thing is to open a new tab in your terminal and type commands there.

Edit:
I'm stupid.  You just put a **&** after it.  ie
```
nautilus&
```

---

### Post by Sukarn on 2008-04-29
You can either put an ampersand after it like forrestcupp suggested, or you could run it in a detached screen session.

For example, if I wanted to run transmission like this, I would type
```

screen -dmS torrents transmission

```
what this does is that it starts a new terminal in the background and runs the command "transmission" in that new terminal, and gives the name "torrents" to that new terminal.

For more information, type
```

man screen

```
or
```

screen --help

```

With this method, all the output from that program is sent to that new terminal which is running in the background.

With the method suggested by forrestcupp, you will get all the output from the program you ran, in your current terminal, which kind of messes up everything when outputs from multiple programs appear inter-mixed in the same terminal. It is worse when you're trying to type some command in that terminal and you're getting some outputs in the terminal as well. Imagine running "ls -hl" while some program is throwing out information about some random stuff. This mixed output can confuse you sometimes, it confuses me.

---

### Post by rolodoom on 2008-04-29
Ampersand was the one I was Looking for.

---

