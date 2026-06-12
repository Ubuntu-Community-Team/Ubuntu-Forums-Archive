---
title: "how to use the at command"
date: 2007-04-26
forum: General Help
---

### Post by Mateo on 2007-04-26
I don't get how to use it.  I have read the man page so please don't suggest that.  I've tried a couple of different ways:

```
whatever command | at 2035
```

But this makes the console wait for the command.  I just want to add a command to be executed by daemon.  So if you do this:


```
at 20:35 < file
```

is supposed to run the commands listed in **file**.  But again, I don't want to make a special file each time I run at.  I just want to add a command to the daemon.  How do you do this!  It's frustrating because the people who design man pages act like you already know how to use it.

---

### Post by Mateo on 2007-04-26
figured it out.  for those wondering do something like this:

```
at 9:00pm
```

and then it will show something like this:

```
at>
```

and there you enter your command (or commands).  then press **ctrl+d** to save the command.  You can see what's scheduled by using the **atq** command.  the **atrm** command will remove selected queues.

---

