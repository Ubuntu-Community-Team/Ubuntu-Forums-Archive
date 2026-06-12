---
title: "Error-kde su"
date: 2008-05-30
forum: General Help
---

### Post by Rocky37 on 2008-05-30
ralph@ralph-laptop:~$ sudo apt-get install synaptic (or other)
>>> sudoers file: syntax error, line 12 <<<
sudo: parse error in /etc/sudoers near line 12
ralph@ralph-laptop:~$ 


This error is returned under administrator mode:
Error-kde su
su returned with an error

Can't do anything having to do with a terminal or administrator mode and updates don't work either

---

### Post by pointone on 2008-05-30
You'll need to boot into recovery mode and run "visudo" to edit your sudoers file and see what on line 12 is causing the problem.

---

### Post by Rocky37 on 2008-05-30
Well that was a learning experience!!!  Spent much of this PM reading and learning 3 or times over. Shades of DOS 

At long last got it corrected.

Thanks much for the fast help

---

