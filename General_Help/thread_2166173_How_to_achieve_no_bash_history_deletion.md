---
title: "How to achieve no bash history deletion"
date: 2013-08-08
forum: General Help
---

### Post by shantiq on 2013-08-08
Like many in Ubuntu i use the amazing 
[incremental history searching  ]("http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/")

Now I have noticed over a few years that the entire bash history gets wiped out from time to time rendering the incremental search null and void;  having to start all over again and remembering commands :KS

Reading around it seems when it get to a certain numbers it wipes out all the history
Am I right in thinking that?


and using ```
gedit  ~/.bashrc
```   and finding 

HISTSIZE=1000
HISTFILESIZE=2000   you will see the numbers are set quite low

I understand when it reaches one of those numbers it will WIPE all memory of previous history


so to set them much higher say

HISTSIZE=100000
HISTFILESIZE=200000    and then enter ```
. ~/.bashrc
```  should keep me happy until next OS clean upgrade



But surely there must be a way to set it to infinite so your incremental history search is ALWAYS secure

i found [this]("http://www.cyberciti.biz/faq/clear-the-shell-history-in-ubuntu-linux/#comment-96800") online to do the reverse [ie keep no history]

> Prevent a bash history file from ever being saved


Add the following commands to ~/.bashrc file:
echo 'unset HISTFILE' >> ~/.bashrc
echo 'export LESSHISTFILE="-"' >> ~/.bashrc


so there must be an equivalent command to do what it is i wish for:  ie unlimited bash history


Might some of you know what it is please?

---

### Post by SlugSlug on 2013-08-08
It wont wipe it all, it justs overwrites the oldest entry. Setting the number higher should be enough

---

### Post by shantiq on 2013-08-08
hhmmmm    so the wiping out must be when i have a freeze and have to pull the lead out...     so it happens when i do an "emergency stop"  ...   i always wondered what the cause was

thanx for that  ...    still there must be a way to write this infinity line  ...    but academic i suppose   100000   should be enough   ::]]]

---

### Post by mc4man on 2013-08-08
You should keep in mind that the larger the history file the slower your terminal will open, though slow is quite relative.
Unfortunately bash doesn't have any great means to prevent duplicate entries except in a current terminal session so if you look you'll find many common commands duped numerous times. 
Without dupes it's quite unlikely you'd need much more than 5000 or so, if that..

You can make use of HISTIGNORE= to prevent some from being duped though I've found that to be a bit of a pita for various reasons except for a few basic ones.
Here I do backup .bash_history from time to time & also make use of a script to clean dupes. (I always back up before cleaning
(there are several scripts floating around, the one I currently use doesn't quite keep ordering, one that does seemed to not work as well, ie. removed some commands completely.

Anyway you can search this out easily (.bash_history does not erase dups), currently I'm using the perl script from here, reply 3, under  "But I still need to remove duplicates from time to time:" - 
[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/189881](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/189881)

The ordering, if changed,  doesn't matter here as I use a recall  previous command search based on char(s) typed rather than going back in order with arrow key..

---

### Post by shantiq on 2013-08-08
Hi mc4    great info also [here]("http://www.thegeekstuff.com/2008/08/15-examples-to-master-linux-command-line-history/#more-130") in 8 9 and 10    on dupes   ;)



[B]PS:
[/B]

also my tip to chase "old"   commands      > history|grep -i  asectionofthecommandyouarelookingfor    works better for me than any other i have tried   and there are repeats that way ut it is fast and i always see what i am looking for straightaway


example:

>  **history|grep -i bash **
  28  echo "HISTCONTROL=ignoredups" >>~/.bashrc
   29  leafpad  ~/.bashrc
   54  gnome-open .bash_history
   55  echo "HISTCONTROL=ignoredups" >>~/.bashrc
   56  leafpad  ~/.bashrc
71  history|grep -i bash





---

### Post by coldraven on 2013-08-08
This is a good tip, in fact it is the best one. 
[http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/](http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/)

---

### Post by shantiq on 2013-08-09
[absolutely]("http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/") Coldraven     but > [COLOR=#000000]*history|grep -i asectionofthecommandyouarelookingfor*[/COLOR]    is for command you do not remember the first 2 or 3 first letters of;   but  remember a key word     seee what i mean  ::]]
[COLOR=#000000][/COLOR]

---

### Post by coldraven on 2013-08-09
> **shantiq said:**
> [absolutely]("http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/") Coldraven     but     is for command you do not remember the first 2 or 3 first letters of;   but  remember a key word     seee what i mean  ::]]


I've sobered up enough now to understand :)  I will definitely use it, thanks.

---

