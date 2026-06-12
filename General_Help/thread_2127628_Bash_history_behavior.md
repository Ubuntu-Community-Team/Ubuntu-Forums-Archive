---
title: "Bash history behavior"
date: 2013-03-20
forum: General Help
---

### Post by argentum2f@gmail.com on 2013-03-20
Not sure where best to ask this question, so it's going here.

In bash I can push the up arrow to cycle through previous commands. I've found that some command line utilities - in particular 'octave' (and maybe others) have an additional feature that if I type in the first part of a command, then press the up arrow, it will cycle through previous commands that start with whatever I've typed in. So, for example  I can type "for"  and then press the up arrow to cycle through all the previous commands I issued starting with for. It is extremly helpful for me and I really wish bash would also behave in the same manner.

Is there a simple way to enable this feature? 
If not, what would it take? If nothing else it seems like you could set the uparrow to a custom command.

---

### Post by howefield on 2013-03-20
Try this thread.

[http://ubuntuforums.org/showthread.php?t=2119383&p=12526445](http://ubuntuforums.org/showthread.php?t=2119383&p=12526445)

---

### Post by argentum2f@gmail.com on 2013-03-26
Thanks so much!

The answer was in reply #5 (along with a some other useful bits):

gedit .inputrc
"\e[A": history-search-backward
"\e[B": history-search-forward

Edit:
Why can't I mark this as 'solved'?

---

