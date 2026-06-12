---
title: "bash shell variable completion help"
date: 2007-10-02
forum: General Help
---

### Post by jasonlp on 2007-10-02
I need some help with bash's shell variable completion feature.

When I was using RedHat ES2's bash, the command line:

    $ ls $SOME_<tab>

would complete the shell variable name.  This would happen regardless of the command I was using (cd, gvim, etc.).

I'm now using Ubuntu v7.04 and this feature of bash has apparently gone away or been replaced with less than useful behavior.  For example, the 'ls' example from above does nothing in Ubuntu (except beep at me).  If I use the 'cd' command:

    $ cd $SOME_<tab>

It's replaced with:

    $ cd \$SOME_VERY_LONG_NAME_FOR_A_PATH 

Prefixing an undesirable backslash to the dollar sign.

What configuration change do I need to make to get bash to complete shell variable names (without prefixing a backslash) for any command?

Thanks,
Jason

---

### Post by jamvegan on 2007-10-03
I don't know how to make TAB behave as you desire, but you can use ESC-$ instead of tab to do what you want to do (not as convenient as TAB, I know, but maybe more convenient than typing really long variable names).

---

### Post by bodhi.zazen on 2007-10-04
You can do this with zsh, but I have not seen it with bash

---

### Post by dougleduck on 2007-10-20
I've been trying to work out the same problem, though I've yet to try it possible solution files at [http://www.caliban.org/bash/index.shtml#completion](http://www.caliban.org/bash/index.shtml#completion).

---

