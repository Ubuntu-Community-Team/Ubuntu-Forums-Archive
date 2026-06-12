---
title: "how to pipe from command line?"
date: 2006-07-25
forum: General Help
---

### Post by lex1 on 2006-07-25
I was going to run this repserver.pl (perl script) 
like so in /etc/alises

someusername: | repserver.pl(path to it)

then run   newaliases.

Alternatively i could put a pipe into a .forward file in someusername's homedir. the .forward file must  be owned by that user.


i am asking for suggestions on how the command line might look?

how about
 echo '"| /path/to/repserver.pl"' >~/.forward







lex1

---

