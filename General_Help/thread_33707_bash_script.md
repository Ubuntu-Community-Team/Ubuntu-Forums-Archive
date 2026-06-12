---
title: "bash script"
date: 2005-05-11
forum: General Help
---

### Post by crash369 on 2005-05-11
hello all

i hope someone here will be able to help me out.  i am trying to run a short bash script that does 3 things.

1. opens an Eterm terminal
2. runs screen in that terminal
3. runs irssi in that terminal

(yes, those 3 are installed and work fine)

this is the script i wrote (which doesn't work correctly)
```
#!/bin/bash
Eterm -g 95x55+5+160 -name IRC --icon-name IRC --scrollbar-popup 0 --scrollbar 0
screen
irssi
```
i would appreciate any help.

p.s. - i am not set on using a bash script, it is just the first thing that came to mind.  if there is another way to do the 3 things outlined above in one command, i will be glad to hear about it.

---

### Post by JonahRowley on 2005-05-11
When you run eterm, it'll start a subshell.  To make things run in that subshell, look at the -e option to eterm.  To run irssi in screen, put it on the end.  So, to chain all this together:

```
Eterm <your eterm options here> -e screen irssi
```

Give this a try.  It doesn't check to see if screen is already running in the background though, so if you need this script to be able to reattach to backgrounded screens, it's going to be a little more complex.

---

### Post by crash369 on 2005-05-12
thank you very much Jonah, that works very well!

now about the reattaching?  would it be too difficult to make the script mimic
```
$ screen
$ irssi
```
instead of
```
$ screen irssi
```

---

### Post by JonahRowley on 2005-05-12
I'm not sure I know what you mean?

```

$ screen
$ irssi

```
The screen command will start a subshell, the irssi command will be run in the subshell.  This is the same as running **screen irssi** from outside screen.

Screen actually has options to resume sessions by name.  So, change the Eterm command to something like this instead:
```

Eterm -e screen -RS irc irssi

```
Now, the first time screen starts, it creates a new screen with the session name **irc**.  But the next time, it will reattach to the **irc** session instead.  I think this is just what you need.

---

### Post by crash369 on 2005-05-13
actually, my problem is that if i detach or quit irssi, my eterm exits.  i want it to stay open, so that i could attach a different irssi session to it.

---

