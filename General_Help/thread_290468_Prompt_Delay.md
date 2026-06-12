---
title: "Prompt Delay"
date: 2006-11-01
forum: General Help
---

### Post by AstroKid on 2006-11-01
Just installed 6.10

Does anyone know what could be the cause of a Terminal Delay Prompt. I'm encountering two issues:
1. When opening a Terminal, there is approx. 15~20 seconds before a prompt is actually displayed.
2. When SSH'ing to the box the same delay occurs.

Running Top while attempting either of the above show that BASH and then SED use about 97% of the CPU. Didn't see anything weird in any of the login or .rc files. 

I have attempted to use ZSH and that appears to shorten the delay by about 8 seconds.

Specs:
P4 2.8 Ghz
2GB Ram
320GB HD

Any help would be greatly appreciated.

Thanks

---

### Post by llamakc on 2006-11-01
Wow, that's some delay. My system is about 1/2 of your specs and I don't have that result.

You didn't carry over an old /home/username from an earlier install did you? Is the delay with ssh AFTER the password is accepted--try running with the -v flag to watch the output.

Otherwise, have you tried xterm or aterm to compare?

---

### Post by AstroKid on 2006-11-01
Nope, this was a fresh install on a new HD. (it isn't partitioned but I didn't think that could cause this delay... but i'm grasping for straws)

Delay is after the password is accepted. It's weird, the password prompt has no delay it's just before the command prompt is displayed.

Didn't think to try any other terms, just tried xterm and still had the same response.

Thanks anyway.

---

### Post by AstroKid on 2006-11-01
Found it, it kept getting delayed when it sourced the /etc/bash_completion part of the login script. 

mv'ed that file to .bak and everything is much better now.

Thanks again.

---

