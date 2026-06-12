---
title: "Strange problem with the find command"
date: 2006-12-03
forum: General Help
---

### Post by madtinkerer on 2006-12-03
I'm having an odd problem.  I'm trying to run the find command but I keep getting an error.  Here is what I am trying to run.
```

find /home/user/new -mtime +6 -type l -print 0 | xargs -0 rm -f

```
and I get the following error
```

find: paths musts precede expressions

```
My path is preceding my expression and the command will only work if I strip everything from it except
```

find /home/user/new -mtime +6

```

Any suggestions?

---

### Post by engla on 2006-12-03
It is "-print0", without the space. Is that enough?

---

### Post by madtinkerer on 2006-12-04
That was the problem.  Thanks.  I have another problem with the same command though.  The files in that directory are all links created by a script I run with a cron job.  When I run the command under sudo, I get permission denied errors.  However, if I run just  ```

sudo rm -f

```
in the directory it works fine.  Any ideas why?  The only thing i can think of is that the pipe to rm -rf isn't run by the sudo command but I can't see that as possible

---

### Post by engla on 2006-12-04
no, you're on the right track there. The pipe connects inputs but it doesn't  mean that the processes are more closely connected than that, so you have to have sudo on the xargs rm end rather than the find end!

---

### Post by madtinkerer on 2006-12-04
But how do I split the actions while still piping the info to the rm command?  Can you give me a code example?

---

### Post by engla on 2006-12-04
"find ... | sudo xargs rm -rf" should work, sudo will just let the pipe connect right through it.

One option could be to drop into a root shell 
"sudo -s"
and then run the command without bothering with sudo or such things. Be careful anyhow!

---

