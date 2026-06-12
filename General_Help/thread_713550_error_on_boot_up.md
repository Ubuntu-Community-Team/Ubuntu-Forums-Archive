---
title: "error on boot up"
date: 2008-03-02
forum: General Help
---

### Post by whistltn on 2008-03-02
When I tried to start Ubuntu 7.10, the following error messages showed up-
/dev/hda3: Unattached inode 119344
/dev/hda3: Unexpected Inconsistency  
It then goes through a fsck routine-- then
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: command: command not found
bash: The: command not found
root@brightwood-desktop:~#
after pressing control-D, the whole thing repeats and Ubuntu never boots up--

Any suggestions about how to get Ubuntu working again would be appreciated.

---

### Post by iris-n on 2008-03-02
It found an error in your filesystem. Try ```
fsck /dev/hda3
``` to check it. Ctrl+D is just to skip the process, i.e., it's bound to fail.

---

### Post by whistltn on 2008-03-03
Thank you iris-n.  The fsck /dev/hda3 command led through a series of file systems checks and corrections and now Ubuntu boots up great :)  Glad you're out there!

---

