---
title: "Problem Setting up default terminal editor"
date: 2008-02-12
forum: General Help
---

### Post by rahnen on 2008-02-12
I've been trying to setup Nano as my default editor for the command line

I put the following into .bashrc

# Sets default Editor
export EDITOR=/usr/bin/nano
 
...saved it, logged out, logged back in, went back to terminal, yet when I

rick@rick-desktop:~$ echo $editor

rick@rick-desktop:~$ 

...no echo from editor pointer!

If I type "nano" on the command line I get the nano to come up...but without the pointer/echo scripts choke.

What am I doing wrong???????:(

---

### Post by geraldm on 2008-02-12
perhaps you can confirm that you have learned that bash is case sensitive?

~/.bashrc gets executed by bash for non-login shells
~/.bash_profile gets executed by bash for login shells, (but may source ~/.bashrc if it exists)

Gerald

---

### Post by rahnen on 2008-02-13
Yes..that was it Case Sensitive...thanks.

Now one more question, How could I have debugged this myself?

i.e.: some hot key to watch the .baschrc script after login?...adding an "echo" & a  "pause" or something to see the result?

---

