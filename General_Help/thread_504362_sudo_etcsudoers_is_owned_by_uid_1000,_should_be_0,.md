---
title: "sudo: /etc/sudoers is owned by uid 1000, should be 0, can't sudo"
date: 2007-07-19
forum: General Help
---

### Post by sarahsilverman on 2007-07-19
"user's $home/ .dmrc file is being ignored. this prevents the default session and language from being saved. file should be owned by user and have 644 permissions. user's $home directory must be owned by user and not writable by other users."

i can't access any of the administrative tools on the panel, i can't change any users. i tried testing it on guest, but all i got was the error message to the top.

i can't do anything sudo, nor can i install any applications.

outputs:

ls -l /home: total 8
drwxr-xr-x  2 jonathan jonathan 4096 2007-07-17 18:39 guest
drwxr-xr-x 37 jonathan jonathan 4096 2007-07-18 20:49 jonathan

another output i can't remember what i typed in the terminal: ---s--x--x 1 jonathan jonathan 91508 2006-10-09 01:37 /usr/bin/sudo

any help is greatly appreciated thanks :biggrin:
:guitar:

if you need anymore information just post so or pm me. thanks i love you all.:popcorn:

---

### Post by dreadlord_chris on 2007-07-19
> **sarahsilverman said:**
> "user's $home/ .dmrc file is being ignored. this prevents the default session and language from being saved. file should be owned by user and have 644 permissions. user's $home directory must be owned by user and not writable by other users."

i can't access any of the administrative tools on the panel, i can't change any users. i tried testing it on guest, but all i got was the error message to the top.

i can't do anything sudo, nor can i install any applications.

outputs:

ls -l /home: total 8
drwxr-xr-x  2 jonathan jonathan 4096 2007-07-17 18:39 guest
drwxr-xr-x 37 jonathan jonathan 4096 2007-07-18 20:49 jonathan

another output i can't remember what i typed in the terminal: ---s--x--x 1 jonathan jonathan 91508 2006-10-09 01:37 /usr/bin/sudo

any help is greatly appreciated thanks :biggrin:
:guitar:

if you need anymore information just post so or pm me. thanks i love you all.:popcorn:

You've got some problems there - your permissions are **all** screwed up. **sudo** should be owned by root, **not** by jonathan - and I have a feeling that's only one small part of the problem. The first part of you post indicates that there are permission problems with you $HOME directory too.

I have a feeling it might be easier to just reinstall your OS than fix all your permissions problems

---

### Post by aysiu on 2007-07-19
Did you change ownership of your entire Ubuntu installation to the user Jonathan? If so, your system is screwed. You could attempt to repair it, but it'd probably take longer than a reinstall.

---

### Post by krcabrer on 2007-09-23
> **dreadlord_chris said:**
> You've got some problems there - your permissions are **all** screwed up. **sudo** should be owned by root, **not** by jonathan - and I have a feeling that's only one small part of the problem. The first part of you post indicates that there are permission problems with you $HOME directory too.

I have a feeling it might be easier to just reinstall your OS than fix all your permissions problems

I got the same problem.

How do I reinstall ubuntu without losing my data? I mean the \home\user partition.
I have \home\user directory in a differente partition.

Thank you for your help.

Kenneth

---

