---
title: "Change Ubuntu command line prompt?"
date: 2007-07-03
forum: General Help
---

### Post by jnorthr on 2007-07-03
My ubuntu bash command line prompt shows:
jim@jim-laptop:~Desktop 

though i prefer to see the full path declaration like:
jim@jim-laptop:/usr/home/jim/Desktop

can this be changed? I thought i read that the PROMPT_COMMAND environ.variable was the place to fix this but where does this var get declared ?  Looked for .profile on my machine but i don't understand the FIND command well enough to search from the root for a file like .profile

any ideas ?
ta

---

### Post by gborzi on 2007-07-03
You can also change the PS1 variable in your .bashrc, more details here [http://tldp.org/HOWTO/Bash-Prompt-HOWTO/]("http://tldp.org/HOWTO/Bash-Prompt-HOWTO/").

---

### Post by jnorthr on 2007-07-04
many thanx for that tutorial - always great to find something i (kinda) understand !!

---

