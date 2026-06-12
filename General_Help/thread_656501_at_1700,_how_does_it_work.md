---
title: "at 17:00, how does it work?"
date: 2008-01-02
forum: General Help
---

### Post by holihue on 2008-01-02
How does the "at" command work?


I know it will run some commands at for example 17:00.


Thanks

---

### Post by Jussi Kukkonen on 2008-01-02
man is your friend, in this case "man at".

examples (first with standard input, then with file-option):```

echo "command_to_run" | at 17:00
at -f script_file_name 11am tomorrow
```

---

### Post by ~LoKe on 2008-01-02
So is this like a miniature cronjob?

---

### Post by PinkFloyd102489 on 2008-01-02
Yeah you could say so.

---

### Post by holihue on 2008-01-02
it didn't work:

```
$echo "gedit" | at 23:34
warning: commands will be executed using /bin/sh
job 24 at Wed Jan  2 23:34:00 2008

```

but 23:34 I it didn't run gedit (no gedit window on my screen).

---

### Post by Borbus on 2008-01-02
A difference between at and cron is that at does not run as a daemon. If you run at in a terminal, and then close the terminal, it will not be run. at must keep running until the time you specify so that it can execute the command.

cron on the other hand runs in the background all of the time. I would use cron instead of at every time but at can be useful if you don't have permisson to use cron in your shell (you can run at in screen for example).

---

### Post by ~LoKe on 2008-01-02
> **holihue said:**
> it didn't work:

```
$echo "gedit" | at 23:34
warning: commands will be executed using /bin/sh
job 24 at Wed Jan  2 23:34:00 2008

```

but 23:34 I it didn't run gedit (no gedit window on my screen).

It worked for me.  I did:
```
echo "mpc stop" | at 17:43
```
and MPC stopped at 5:43 (17:43).

Finally, I can have MPC turn off in the middle of the night so it doesn't keep playing...

---

### Post by Borbus on 2008-01-02
> **holihue said:**
> it didn't work:

```
$echo "gedit" | at 23:34
warning: commands will be executed using /bin/sh
job 24 at Wed Jan  2 23:34:00 2008

```

but 23:34 I it didn't run gedit (no gedit window on my screen).

Try using absolute paths, ie. /usr/bin/gedit also remember you need to keep at running so keep the terminal open. cron would be better to use if you wanted to stop mpc every night. cron definitely needs absolute paths though because it runs commands in a very basic shell so you would need to use /usr/bin/mpc not just mpc.

---

### Post by ~LoKe on 2008-01-02
> **Borbus said:**
> cron would be better to use if you wanted to stop mpc every night. cron definitely needs absolute paths though because it runs commands in a very basic shell so you would need to use /usr/bin/mpc not just mpc.

I don't have a very consistent sleep schedule so it would probably be a little easier to just manually set it to stop at a certain time that night.

---

### Post by holihue on 2008-01-02
> **Borbus said:**
> Try using absolute paths, ie. /usr/bin/gedit also remember you need to keep at running so keep the terminal open. cron would be better to use if you wanted to stop mpc every night. cron definitely needs absolute paths though because it runs commands in a very basic shell so you would need to use /usr/bin/mpc not just mpc.

It still doesn't work.

---

