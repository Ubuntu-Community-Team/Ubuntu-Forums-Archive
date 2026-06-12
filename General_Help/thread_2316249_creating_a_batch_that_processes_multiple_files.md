---
title: "creating a batch that processes multiple files"
date: 2016-03-06
forum: General Help
---

### Post by goofprog on 2016-03-06
I asked someone how do I pass a field of arguments to another application via command line to do a batch process and I was suggested to use the xargs command.  The problem with that command to me is it does not pass each line into a command line variable for processing.  Maybe I am doing something wrong.  I believe there is another way and that is to pump the output (stdout) to something like gawk and print each line out to a command line variable.  So I guess my problem is how do I capture stdout and line by line funnel it to a variable like $1?
Thx in adv.

.add
I may just have to break down and code something again.  I do not coding anymore, but I guess I will have to if I cannot find a easy command shell solution.
again Thx.

.add
never mind.  I will just use windows command line batch scripts from wine to get my work done.
Please close this umm ........ ticket?
My solution
[B]for %%a in (%*) do (
<do some stuff> -f %%a <blah blah blah>
)[/B]

thanks guys.

---

### Post by nerdtron on 2016-03-06
There is a for loop on bash:

```
 for var in `listings/source here`; do
commands here
more commands here
done

```

---

