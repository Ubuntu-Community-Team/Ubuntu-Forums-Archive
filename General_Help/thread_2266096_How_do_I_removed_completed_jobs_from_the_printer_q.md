---
title: "How do I removed completed jobs from the printer queue"
date: 2015-02-19
forum: General Help
---

### Post by TerryDixon on 2015-02-19
I have several hundred completed jobs in the print Q that I can't remove. 
a.) Trying "Cancel All Jobs" via CUPS administration ([http://127.0.0.1:631](http://127.0.0.1:631)) requests a password. If I use my user login it fails to authenticate.

b.)Using  "cd /var/spool" then "sudo ls -l cups" will list all the files in the cups directory.
However a subsequent "sudo rm cups/*" will give me:

"rm: cannot remove ‘cups/*’: No such file or directory"

Can anyone give me a hint of what I need to do to remove these files.

I am using ubuntu 14.10

Thanks

---

### Post by HermanAB on 2015-02-20
Read this:
[http://linux.die.net/man/1/lpq-cups](http://linux.die.net/man/1/lpq-cups)

and then read all the others mentioned at the bottom.

---

