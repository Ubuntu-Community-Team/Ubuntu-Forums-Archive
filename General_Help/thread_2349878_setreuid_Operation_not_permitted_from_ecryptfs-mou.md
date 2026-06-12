---
title: "setreuid: Operation not permitted from ecryptfs-mount-private"
date: 2017-01-19
forum: General Help
---

### Post by yiminli on 2017-01-19
Hello, 

Not sure exactly how this happened - when I started my old computer again trying to consolidate all of my kids pictures.  I was not able to log into Ubuntu desktop and discovered the entire $HOME is empty.  Only left with a couple of files.  One of them is a README.txt with the content below,

[INDENT]*THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.*[/INDENT]


[INDENT]*From the graphical desktop, click on:*[/INDENT]
[INDENT]* "Access Your Private Data"*[/INDENT]
[INDENT][/INDENT]
[INDENT]*or*[/INDENT]
[INDENT][/INDENT]
[INDENT]*From the command line, run:*[/INDENT]
[INDENT]* ecryptfs-mount-private*[/INDENT]


I ran the "ecrpytfs-mount-private" command but run into a permission issue with setreuid, 

[INDENT]*user@host:~$ **ecryptfs-mount-private***[/INDENT]
[INDENT]*Enter your login passphrase:*[/INDENT]
[INDENT]*Inserted auth tok with sig [c702e0432cfe57ac] into the user session keyring*[/INDENT]
[INDENT]***setreuid: Operation not permitted***[/INDENT]



then I sudo executed the command and run into fopen: file not found error.  I later found out I should not be running the command with sudo.

Please help and thank you very much!

---

