---
title: "Setting prompt in tcsh - no luck"
date: 2008-07-10
forum: General Help
---

### Post by protogenesis on 2008-07-10
Running latest Ubuntu server.

Have installed tcsh.

Have created a .tcshrc within my $HOME.

Added a line that says setenv PROMPT 'Hostname-> '


No dice.

Have even tried to set the prompt from a command line, still no change.  The prompt is the system standard which is 'hostname : pwd % '

I cannot, for the life of me, figure out why I cannot set the prompt.  Typing 'env' shows that my prompt has been set by my .tcshrc, but my output doesn't reflect that.  

Thoughts?

---

### Post by sdennie on 2008-07-10
Rather than "setenv" try:

```

set prompt = "whatever prompt you want"

```

---

### Post by protogenesis on 2008-07-10
...well, I'll be damned, that worked! 

Whatever happened to using 'setenv' for such things?  Used to be the way to go.  Did I not get the memo?


Thanks!

---

### Post by sdennie on 2008-07-10
I dunno.  I have a .tcshrc that's about 10 years old that I initially wrote on Solaris and it's using "set prompt" instead of "setenv PROMPT" whereas everything else in the .tcshrc is using "setenv FOO".  Must be just a quirk of tcsh.

---

