---
title: "[SOLVED] timeout a command line command?"
date: 2007-08-09
forum: General Help
---

### Post by watermark on 2007-08-09
Is there a way I can run a command for a certain length of time?

I'm going to cat /dev/video0 with a pvr-250, which should run indefinitely unless I halt it.  So a timeout command should work too.

Any commands come to mind?  Otherwise I'll prob just write a little java app to do it.

---

### Post by girishv on 2007-08-09
you can use watch command to do this

watch -n1 'cat /dev/video0'

will repeat the command cat /dev/video0 every 1 second. You can choose the interval (in sec) which suits you best.  At any time if you want to stop the execution, kill it with
ctrl-c or in any other terminal with
pkill watch


Girish

---

### Post by stylishpants on 2007-08-09
You want the 'timeout' command.  It's not part of the standard UNIX toolchain so you'll have to install it from the repositories (package name is 'timeout'.)
```

fhanson@fhanson:~$ timeout --help
usage: timeout [-signal] time command.
```

---

### Post by apetresc on 2007-08-09
These kinds of solutions will only partially work. Because of the way cat is built, it buffers a *lot* of output and then sends it all at once. As a result, even after you kill it, it may still have massive amounts of data still being sent to stdout.

Do this experiment.

1. Open up two terminals
2. In one of the terminals, type: cat /dev/urandom . Random junk will start filling the screen
3. In the other terminal, type "ps aux | grep -v grep | grep urandom". This will give you the process id of the cat process
4. In the second terminal, type "kill pid" where "pid" is the process ID you got in the last step
5. Type "ps aux | grep -v grep | grep urandom" just to be really sure you did kill the cat process.
6. Now look back to the first terminal. Even though you've killed its process it is still dumping out huge amounts of random junk to the screen. Its accumulated a huge buffer which stdout is now processing in spite of cat no longer being there. Cat is a LOT faster than stdout can print to a terminal!

So depending on what you plan to do with this, it may not really work for you.

---

### Post by stylishpants on 2007-08-09
> **AdrianP said:**
> These kinds of solutions will only partially work. Because of the way cat is built, it buffers a *lot* of output and then sends it all at once. As a result, even after you kill it, it may still have massive amounts of data still being sent to stdout.


Your experiment shows buffering effects from gnome-terminal, not from cat.

The criticism would apply if you intended to print the output to a terminal.  Since the odds are that the output from cat will be sent to a file or a consuming program, it is never actually rendered by the terminal, and the terminal buffer doesn't come into play.


"timeout 7 cat /dev/video0 > file" should produce a file containing about 7 seconds of raw video every time.

---

### Post by apetresc on 2007-08-09
> **stylishpants said:**
> Your experiment shows buffering effects from gnome-terminal, not from cat.
Actually, I didn't use gnome-terminal, I used two raw tty's.

> The criticism would apply if you intended to print the output to a terminal.  Since the odds are that the output from cat will be sent to a file or a consuming program, it is never actually rendered by the terminal, and the terminal buffer doesn't come into play.
I know, it won't affect mediums where the rate of transmission is somewhere near to the rate at which cat streams, which is why I said it may not work "depending on what you plan to do with this." However, I do think it may affect situations where the buffer is much slower than cat, like file i/o. Maybe. I'm not trying to nullify your suggestion or anything, just proactively pointing out what could turn into a source of annoying but hard-to-find bugs.


> "timeout 7 cat /dev/video0 > file" should produce a file containing about 7 seconds of raw video every time.
Ah, okay, so I guess you've tried it experimentally and it works, then. I was just trying to throw a warning out there (I've run into a similar problem before, but I guess timeout is different from a simple "sleep 5; kill `pidof something`")

Good luck :)

---

### Post by psusi on 2007-08-09
Wow, I am surprised that someone actually wrote such a command.  You can accomplish this with nothing but shell builtin commands.  To kill command "foo" after it has run for 8 seconds, you just do:

foo & sleep 8 ; kill $!

The & runs foo in the background, then the two commands sleep 8 and kill are run one after the other in the foreground.  $! is a shell variable for the pid of the most recently executed background job.

---

### Post by psusi on 2007-08-09
Oh, and you can background that entire thing if you want by wrapping it in () and following with another & to background the whole group.  Then it will do its thing in the background while you can continue to use the terminal, and after the 8 seconds, foo is killed automatically.

---

### Post by watermark on 2007-08-09
I'm sure the timeout command would have worked too, but I used psusi's version....just a clever combo of existing commands.  Worked like a champ...You the man psusi.

---

### Post by psusi on 2007-08-10
Such is the awesome power of a unix shell ;)

Many tiny parts that do very specific things in the simplest way possible, allowing you to combine them together in an infinite number of ways to accomplish anything.

---

