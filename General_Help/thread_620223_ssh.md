---
title: "ssh"
date: 2007-11-22
forum: General Help
---

### Post by just1812 on 2007-11-22
Hi 
Im attempting to connect to anouther box with ssh the command that I'm using is ssh -l /home/test/.ssh/sshkey -l user computer ls file.txt > file2.txt

this command works when I run it in a perl script but when it runs as a cron job it returns a blank file. 

I also added the -o batchmode=yes option it never helped.

Any help would be appreciated thanks!

---

### Post by mannih2001 on 2007-11-22
Have you tried '/usr/bin/ssh' instead of just 'ssh'?

---

