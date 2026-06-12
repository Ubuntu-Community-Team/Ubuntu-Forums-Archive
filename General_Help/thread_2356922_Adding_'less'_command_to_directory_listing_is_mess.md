---
title: "Adding 'less' command to directory listing is messing up the output"
date: 2017-03-28
forum: General Help
---

### Post by peter1897 on 2017-03-28
I run this command on ubuntu 14.04 server:
```
ls -al /etc/ | grep ^d | nl | less
```

And i get this output:[URL="http://i.imgur.com/2AOTHxWl.jpg"]

[IMG]http://i.imgur.com/2AOTHxWl.jpg[/IMG][/URL]

It happens when i add the 'less' command.
Why does it look like this?

---

### Post by Habitual on 2017-03-28
less may have an alias doing something, so try
```
ls -al /etc/ | grep ^d | nl | \less
```

If not. in terminal type
```
type less
``` and it will show if it is.
I see
```
less is /usr/bin/less
```

---

### Post by peter1897 on 2017-03-28
'type less' shows 'less is /usr/bin/less'. I also tried with '\less' at the end but no change. No aliases for 'less' too.

---

### Post by vasa1 on 2017-03-28
> **peter1897 said:**
> ...
And i get this output:[URL="http://i.imgur.com/2AOTHxWl.jpg"]

[IMG]http://i.imgur.com/2AOTHxWl.jpg[/IMG][/URL]
...
Please note that> If you include screenshots, use the forum attachment system rather than an offsite host such as imgur.
from point #4 in [Posting Guidelines]("https://ubuntuforums.org/showthread.php?t=2158945"). To do so, click on the paperclip icon above the posting area.

Both your code and Habitual's give me the same clean output. Do you have this issue with another terminal program? Are you using the standard ~/.bashrc?

I've tried with lxterminal, xfce4-terminal, and gnome-terminal. All work.

---

### Post by steeldriver on 2017-03-28
I suspect it's a coloring alias of `grep` rather than `less` that is causing this - try

```

ls -al /etc/ | \grep ^d | nl | less

```
or
```

ls -al /etc/ | grep --color=auto ^d | nl | less

```

Alternatively, you can try to have `less` *preserve *the colors

```

ls -al /etc/ | grep ^d | nl | less -R

```

or avoid the whole issue by using (for example)

```

ls -ld /etc/*/ | less -N

```

---

### Post by vasa1 on 2017-03-28
By the way, if someone answers your question satisfactorily, we'd all appreciate your marking the thread [SOLVED]. Read [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) for how to do so and the benefits to the community when you oblige. Thanks!

---

### Post by peter1897 on 2017-03-28
> **steeldriver said:**
> I suspect it's a coloring alias of `grep` rather than `less` that is causing this - try

```

ls -al /etc/ | \grep ^d | nl | less

```


That was the issue. Thanks! By the way, what does the '\' sign do? Deactivate aliases?

---

### Post by Keith_Helms on 2017-03-28
The backslash is used to escape the following character so that the shell doesn't use its normal rules to interpret that character.  When you have a command that is also an alias, escaping or quoting all or part of the command name has the effect of ignoring aliases.  If you had an alias for grep, you could bypass that and go straight to the command by \grep, "grep", 'grep', g\rep, "g"rep, etc.  

If you enter \"grep\", the command will fail because the shell is looking for a command named "grep" (with quotes).  Entering "grep" will cause the shell to interpret and remove the quotes and look for the command grep (without quotes).

---

