---
title: "sudo and dirvish ..."
date: 2007-10-21
forum: General Help
---

### Post by stephan0h on 2007-10-21
hello,

I'm running feisty. I wanted to use dirvish as a backup solution. I ran into the problem, that initializing the archive (i.e. dirvish-vault) wit *sudo dirvish --vault system --init*  leads to a broken pipe error of rsync - immediately after entering my user's password for the second time. Trying to fix it i tried vairous combinations of sudo - the best result I got with:

sudo sh -c "/usr/sbin/dirvish --vault system --init"

but still this crashes eventually. Interestingly in the course of running I get asked many more times to reenter my user's password - this must be a sudo-issue, I think. Somehow in the course of processing, the dirvish command needs root-access which it apparently does not have. But why? Haven't I started the command with sudo in the first place? And the broken-pipe issue happens after reentering the password. So, how to start this command so that it stays in a root-context? Any hints?

Thanks,
Stephan

---

### Post by jwcgator on 2007-10-21
try:

sudo -i
(enter password)

then you should have a root prompt.

Then try

sh -c "/usr/sbin/dirvish --vault system --init"

if it still doesn't work, since it's in the sbin

dirvish --vault system --init 

should work.

---

### Post by stephan0h on 2007-10-22
unable to test this now unfortunately - but I got a question regarding this:
after I enter the root session via 'sudo -i': if i call another shell/process from within this shell - will this also run in 'root-mode', or will it have to do a sudo again?

---

### Post by jwcgator on 2007-10-22
Any process you run from the root shell will be run as root.

---

