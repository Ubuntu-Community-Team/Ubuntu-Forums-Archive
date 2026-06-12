---
title: "Bash script variable subsitution for partial commands"
date: 2007-03-01
forum: General Help
---

### Post by ykhun on 2007-03-01
Hi,

I'm trying to make my life simpler by "silencing" all the job status output of a bash script by just controlling a single bash variable. On the shell, i could type this cmd directly:
```
echo "Job status is blah blah blah" |&> /dev/null
```

In a shell script i'm trying to do this:
```
JOB_OUT="|&> /dev/null"
echo "Job status is blah blah blah" $JOB_OUT
```

Well, it didn't work. I'd tried all the combination of defining JOB_OUT possible, none worked. The bash tutorials i found never actually touched on whether it is possible to set shell-commands into variables in a shell script.

Is this even possible? Thanks!

---

