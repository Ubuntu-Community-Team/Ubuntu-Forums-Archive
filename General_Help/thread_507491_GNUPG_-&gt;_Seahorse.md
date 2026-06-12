---
title: "GNUPG -&gt; Seahorse"
date: 2007-07-23
forum: General Help
---

### Post by Requiem on 2007-07-23
I want to import private keys from an old backup.

Long time ago I generated 3 private keys for thunderbird under windows, now i'm using ubuntu and i want to use my private keys again using seahorse and evolution.

Problem is seahorse does not recognoise any of the backed up files as my private keys

the file i saved are:

gpg.conf
gpg.conf.bak
pubring.bak
pubring.gpg
random_seed
secring.gpg
trustdb.gpg

...in short my old gnupg folder on windows. I can see a .gnupg folder in my home dir and it has similarily named files, i tried overwriting them using the same permissions and ownership (is it normal that root own your private keys? it kinda makes sense)

But seahorse doesn't show my private keys, what do I need to do?

---

### Post by meurrens on 2007-11-13
if you still have access to a Windows machine,
use your backup on this machine
with the unique purpose :

**export your private keys as ascii files (with an extension .asc)**

you can do this using the commercial PGP product
(there is, may be, a demo version ?)

you can also do that using the enigmail extension for thunderbird :

OpenPGP
Key Management
select your keys
File
Export
question : do you want to include the private part ?
answer : yes

as a matter of rule, backup of public and private keys on any system
should allways be done as ascii files.

I hope you are (un)fortunate enough to still have access to Windows...
(I don't anymore since a few years :))

---

