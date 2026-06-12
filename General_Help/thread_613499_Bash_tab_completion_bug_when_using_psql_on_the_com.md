---
title: "Bash tab completion bug when using psql on the commandline"
date: 2007-11-15
forum: General Help
---

### Post by johnclegg on 2007-11-15
I have recently converted over from debian and I have come across a bug with bash . We sometimes experience lock up of the bash shell if we tab complete directories or file names. The only one I have been able to replicate with any regularity is using psql.

In a given directory, I use bash tab completion to complete a file name it locks up the terminal.

eg. 

# cd /tmp
# psql -f  a**[PRESS TAB NOW]** 

shows this on the xterm and locks up the xterm

# psql -f aPassword: 

Background info:

We are using ubuntu 7.04 and bash GNU bash, version 3.2.13(1)-release (i486-pc-linux-gnu)

postgresql-8.2               8.2.4-0ubuntu0.7.04 

etc...

We're using vanilla 7.04 . ie we have not change any of the .bashrc files etc.

Any suggestions on how to fix ?

Cheers

John

---

