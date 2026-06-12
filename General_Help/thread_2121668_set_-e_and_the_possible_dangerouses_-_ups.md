---
title: "set -e and the possible dangerouses - ups"
date: 2013-03-02
forum: General Help
---

### Post by rnerwein on 2013-03-02
hi
for all folks have a look here and read it.

# set -e and the possible dangerouses - ups
# related to the thread:  [ubuntu] SSH connection immediately dropped on 'sudo su'
# !! read it
# saw the thread - ssh to a server and su on an server results in a logout.
# if my english isn't so good - i am a german 

i tought about that situation and remember that i got a similar situation
( about 12 years ago on a solaris high end server - no joke that wasn't funny).

what i figured out was: they installed new startups scripts including a
--> set -e in the procedures :-)) --> those scripts was called  with "." !

now i checked the ubuntu in-soureced files (hope nobody will use a set-e in
the .bashrc)

OK - here is the way to figured out what the problem on ubuntu is.
it should be easy for developer to debug this down.
i came to the resolution that it happens in a in-sourced procedure - here in
---> "/etc/bash_completion"

the last log i got was:
#OK this point was reached - richi
echo "[COLOR=#ff0000]in bash_complpletion[/COLOR] calling __reassemble_comp" >/home/richi/bugs/reassemble

---> this point wasn't reached !!!!!!!
#OK this point was not reached - richi
echo "in bash_complpletion calling __reassemble_comp [COLOR=#ff0000]done[/COLOR]" >>/home/richi/bugs/reassemble

---> the last message in my logfile was:
in bash_complpletion there is the call: calling __reassemble_comp (that's my "echo")
nothing else. that means the end [COLOR=#0000cd]wasn't[/COLOR] reached !!!

!!!!!!!!!!! ---> it is alowed !!!!! to use "set -e" and i even think this behavior can be the problem for a couple of threads i have seen ( login - back to screnn
etc. .....)

hope the developer have fun to debug it down. told my students (long ago)
 ==> a computer is an high speed idiot
 ciao
       richi

P.S. oh yes -  i switched my debug back ! ;-)
     and - this don't happen with the /root/.bashrc - permission problem ??? !!

---

