---
title: "Can someone explain how processes are linked to the shell?"
date: 2006-11-13
forum: General Help
---

### Post by Peepsalot on 2006-11-13
I have a problem.  Sometimes I want to just open a terminal to invoke an X program.  Then I want to close the terminal and get it out of the way.  This seems to work ok for some programs(Edit: actually, I'm not sure this works for any programs, maybe I imagined it.), but for others closing the terminal causes the X program to quit also.

I thought that putting an ampersand & after the command was supposed to alleviate this, but it is not working.

---

### Post by lazyart on 2006-11-13
If you call it from the terminal, then closing the terminal kills the program.  Using the & will give you back the cursor so that you can run another program from the same terminal.

To run one without a terminal window I use Alt-F2.

---

### Post by stylishpants on 2006-11-13
You want "disown".

Since this command is built into the shell, there is no man page for it. 

```

$ help disown
disown: disown [-h] [-ar] [jobspec ...]
     By default, removes each JOBSPEC argument from the table of active jobs.
    If the -h option is given, the job is not removed from the table, but is
    marked so that SIGHUP is not sent to the job if the shell receives a
    SIGHUP.  The -a option, when JOBSPEC is not supplied, means to remove all
    jobs from the job table; the -r option means to remove only running jobs.


```

The short version is, do this:
```

$ xprogram &
$ disown
<close terminal>

```

---

