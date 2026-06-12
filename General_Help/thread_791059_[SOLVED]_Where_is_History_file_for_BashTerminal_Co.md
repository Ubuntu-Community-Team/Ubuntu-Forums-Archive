---
title: "[SOLVED] Where is History file for Bash/Terminal Commands?"
date: 2008-05-11
forum: General Help
---

### Post by OzzyFrank on 2008-05-11
I use my up and down arrows a lot in the terminal, recalling previous commands so I don't have to type them, or find them in my text file of useful commands and copy/paste them. Obviously there is a history file somewhere, so can someone enlighten me as to where it is? I could then remove commands I'll never use again, and in theory should be able to create a backup with only my most-used commands and restore over the current one when need be. Cheers

---

### Post by amingv on 2008-05-11
~/.bash_history
Pretty straightforward :).

---

### Post by Monicker on 2008-05-11
/home/username/.bash_history

---

### Post by tgalati4 on 2008-05-11
There is a utility (I can't remember it's exact name, but you can search in the forums for "top ten" commands) that sorts/counts your history file and prints out your top-ten list.  It's helpful to cut-and-paste this list over time to a stickie for reference.

---

### Post by OzzyFrank on 2008-05-11
Cool. Never noticed that hidden file before. Now I'll just have to figure out how to write a little script that will replace that with a backup copy. Cheers

---

### Post by jw5801 on 2008-05-11
Also, for a neat trick to search your bash history press ctrl+r then type the start of the command you're looking for.

---

### Post by russo.mic on 2008-05-12
Wow, what an awesome trick.  I'm very glad I stumbled onto this thread.

Russo

---

### Post by jw5801 on 2008-05-12
There's a thread full of them!

[http://ubuntuforums.org/showthread.php?t=204382](http://ubuntuforums.org/showthread.php?t=204382)

---

### Post by vlke on 2010-06-09
After I upgraded to new LTS I was getting worried I would have to search all forum again for "tricks" but now I just went into file from my previous LTS of Ubuntu and got all of commands ... VERY COOL ! I love Ubuntu more and more.
Thanks a bunch guys.

---

### Post by OzzyFrank on 2010-06-10
Don't forget you can make "**[COLOR="Purple"]aliases[/COLOR]**" to save typing long and complicated commands:

[http://ubuntugenius.wordpress.com/2009/08/31/custom-terminal-shortcuts-via-bash-aliases/](http://ubuntugenius.wordpress.com/2009/08/31/custom-terminal-shortcuts-via-bash-aliases/)

---

