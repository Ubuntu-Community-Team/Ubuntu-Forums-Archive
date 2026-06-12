---
title: "[SOLVED] wrong umask when logged in through ssh"
date: 2008-01-13
forum: General Help
---

### Post by schola on 2008-01-13
At first a big 'Hello everybody!' since this is my first post in here.

My problem: I have two computers 'webrahmen' and 'webstuhl'. I set the umask to 007 on both via /etc/profile . When I'm logged in directly and type 'umask' I get '0007' but when I'm logged in through ssh I get '0022'.
Does someone know the reason for this and how I can set the umask so it is always '0007' ?

Schola

---

### Post by geraldm on 2008-01-14
Read the manpage for the shell you are using to see which files it reads under restricted access.
Try setting the mask in the home directory files, do not rely on any of the files in /etc.
Check ~/.bashrc with the bash shell.

Gerald

---

### Post by schola on 2008-01-14
That did help me, thank you. I use the "fish" shell and i thought it would read /etc/profile as "bash" does and blindly set the umask there. But /etc/profile is only for Bourne compatible shells and fish is not compatible to these. Now i set the umask in /etc/fish/include/PUTAFILEHERE.fish and my problem is gone.

But this leaves two questions for me:

        1. Why was the umask set correctly when i logged in directly on the machine when it was only set in /etc/profile ? None of the config files of fish does source it.
        2. Why did you advice me not to rely on any of the files in /etc ?

Many thanks for you help!

Schola

---

