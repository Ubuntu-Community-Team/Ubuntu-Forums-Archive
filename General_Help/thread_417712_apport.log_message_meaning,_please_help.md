---
title: "apport.log message meaning, please help"
date: 2007-04-21
forum: General Help
---

### Post by pachequin on 2007-04-21
Hi everyone, I was running a program called charmm (to do molecular dynamics of proteins) but suddenly it crash with a message: "Segmentation fault (core dumped)", when I check on /var/log for any citation to my software i found this lines on the apport.log:

################
apport (pid 14938) Sat Apr 21 19:51:18 2007: called for pid 14936, signal 11
apport (pid 14938) Sat Apr 21 19:51:18 2007: executable: /backup/c28b2/exec/gnu/charmm (command line "charmm")
apport (pid 14938) Sat Apr 21 19:51:18 2007: executable does not belong to a package, ignoring
apport (pid 18479) Sat Apr 21 19:58:47 2007: called for pid 18477, signal 11
apport (pid 18479) Sat Apr 21 19:58:47 2007: executable: /backup/software/c28b2/exec/gnu/charmm (command line "/backup/software/c28b2/exec/gnu/charmm")
apport (pid 18479) Sat Apr 21 19:58:47 2007: executable does not belong to a package, ignoring
apport (pid 18482) Sat Apr 21 19:58:51 2007: called for pid 18480, signal 11
apport (pid 18482) Sat Apr 21 19:58:51 2007: executable: /backup/software/c28b2/exec/gnu/charmm (command line "/backup/software/c28b2/exec/gnu/charmm")
apport (pid 18482) Sat Apr 21 19:58:51 2007: executable does not belong to a package, ignoring
###############

Does any know what does this message means? and how to solve it?

thank for any help.

---

