---
title: "Sudo rdiff-backup"
date: 2020-04-08
forum: General Help
---

### Post by Quarkrad on 2020-04-08
I'm looking at running riff-backup locally (to physically separate HD) and think(!) that because I want to include **/etc** in my backup (as well as** /home**) I need to run the command **sudo usr/bin/rdiff-backup .......etc**.  But .... this obviously asks me for a password.  My rdiff-backup command will go into a script and be automated but I need to get over this password issue.  Everything I've read so far re using rdiff-backup without a password involves a remote server using ssh scenario, but mine is local. I'm currently reading all I can about using nopassword via changes to the etc/sudoers file but this seems excessive (system wide).  Can you make a change via etc/sudoers so that only the rdiff-backup command can run without a password?  Or am I looking down the wrong road completely?

---

### Post by TheFu on 2020-04-08
Please be careful.

```
etc/sudoers
```
    and
```
/etc/sudoers
```
are NOT usually the same.  Those leading / matter, always, for every command, every option, almost always.  The difference between relative and absolute paths is important.

if you post your exact, complete, script, someone might be able to help.

---

### Post by Quarkrad on 2020-04-09
I have done what I wanted but not sure it is the most effective way or if it matters - in that it works(?).  My aim is to run a command in an executable script that contains **sudo /usr/bin/rdiff-backup ...... etc** and being able to run without asking me for a password.  Rather than having no password prompt for any sudo command I enter I want to be able to have no password prompt for just myself (dad) when using rdiff-backup.  So I created a file in /etc/sudoers.d called config by executing the command **sudo visudo -f /etc/sudoers.d/config** and then entered the command **dad ALL=(ALL) NOPASSWD: /usr/bin/rdiff-backup**  Whether this is correct, should be improved/altered I'm not sure.

---

