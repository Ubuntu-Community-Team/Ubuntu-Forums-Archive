---
title: "at Job"
date: 2006-07-27
forum: General Help
---

### Post by mathon on 2006-07-27
hello,

I want to define an atJob to start a script in one minute.

I tried it that way:

[16:37:45]patrick@Achatschitz:~$ at -f test now + 1 minutes
warning: commands will be executed using /bin/sh
job 1 at Thu Jul 27 16:39:00 2006

But after one minute nothing happens. The test script only contains an echo command which displays a message. But after the one minute the echo message is not displayed.

Is there anything wrong?

---

### Post by mathon on 2006-07-27
Has nobody an idea why this does not work? :confused:

---

### Post by cpugeniusmv on 2006-07-27
The script is probably running, but the output, much like in cron, doesn't display directly on the screen---it gets sent to your mailbox on the system (which may or may not actually be set up. I don't remember if a mail transfer agent is installed by default).

Instead of using echo to print something to the standard output, change your script to create a file in your home directory to verify that it is in fact running. Here's an example of how to do that:

```
#!/bin/sh
touch $HOME/newfile
```

---

### Post by Lord Illidan on 2006-07-27
I told it to run gnomad2, for example. It didn't work.

---

### Post by cpugeniusmv on 2006-07-27
The reason is because the shell that the job runs under is a new shell that doesn't know anything about your X session.

Here is an alternative way to start an application after a delay:

```

#!/bin/sh

# Wait for 60 seconds before starting the program
sleep 60

# And then start it, overlaying the current process.
exec gnomad2

```

Is that all you need to do, or is there something else you're trying to accomplish?

---

