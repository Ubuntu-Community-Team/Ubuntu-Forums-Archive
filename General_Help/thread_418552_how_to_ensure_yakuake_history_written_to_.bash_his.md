---
title: "how to ensure yakuake history written to .bash_history"
date: 2007-04-22
forum: General Help
---

### Post by aleska on 2007-04-22
I use yakuake for terminal access.  I have noticed that history within yakuake doesn't necessarily jibe with .bash_history.  I've found I have to close the shell in yakuake by typing "exit" to commit my most recent commands to .bash_history.

Is this expected behavior?  I don't like it; because often I get wrapped up in stuff, have hidden yakuake from sight, and might log out from the overall session without remembering to type "exit" in the yakuake shell.  Then when getting back into yakuake in my next session, I've lost all the most recent history.

Any ideas?  Is there a way to ensure yakuake is writing to .bash_history automatically?

TIA

---

### Post by rich.bradshaw on 2007-04-22
sudo gedit .bashrc

add

shopt -s histappend
PROMPT_COMMAND='history -a'

to the end of this file.

That should do the trick!

---

### Post by aleska on 2007-04-22
I believe the reply I'm looking for is, CHEERS!  
Thanks very much that worked like a charm.  I had to enter the command bash to get it going.  
Very cool.  Thanks!

---

