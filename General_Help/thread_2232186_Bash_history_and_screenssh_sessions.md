---
title: "Bash_history and screen/ssh sessions"
date: 2014-06-30
forum: General Help
---

### Post by DigiAngel on 2014-06-30
So this isn't really Ubuntu specific, but I've always wondered what happens to commands I type when from a remote ssh session or screen session.  These do not show up in my .bash_history file as expected.  Thanks for any tips...I usually just end up logging everything to syslog.

---

### Post by bashiergui on 2014-06-30
Each user has their own bash history created in their home directory. So to see the history of the ssh user you need to look at his home directory.
```
/home/ssh_username/.bash_history
```

---

### Post by Lars Noodén on 2014-06-30
I guess you would have to add two lines to .bashrc to get multiple sessions to save/load the Bash history:

[http://trivialconversations.com/blog/2013/04/20/appending-command-history-from-multiple-shells-into-bash_history/](http://trivialconversations.com/blog/2013/04/20/appending-command-history-from-multiple-shells-into-bash_history/)

---

### Post by sudodus on 2014-06-30
> **Lars Noodén said:**
> I guess you would have to add two lines to .bashrc to get multiple sessions to save/load the Bash history:

[http://trivialconversations.com/blog/2013/04/20/appending-command-history-from-multiple-shells-into-bash_history/](http://trivialconversations.com/blog/2013/04/20/appending-command-history-from-multiple-shells-into-bash_history/)

Thanks for sharing :-)

This solved a long lasting problem for me. (I skipped history -n)

---

### Post by DigiAngel on 2014-06-30
Thanks so much...that's just what I needed.

---

