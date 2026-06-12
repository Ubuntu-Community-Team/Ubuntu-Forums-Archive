---
title: "Send process to background using &amp;"
date: 2013-03-28
forum: General Help
---

### Post by matimont on 2013-03-28
Hi,

I'm running this command in the background:

grep -r "word" &

Now, when I type in "jobs" I get this:
[1]+ Stopped grep -r "word"

Why it stopped? I run then "fg" and comes up fine. But if I leave it there it won't run at all

Help!

---

### Post by ajgreeny on 2013-03-28
Try using **& disown** after the command and it should work fine.

There is no man page in ubuntu for disown, but you can find out about it from ```
man bash | less +/"^ +disown"
``` or even ```
help disown
``` in terminal as it is a built-in bash shell command.

---

### Post by Slim Odds on 2013-03-28
Since you didn't give it a filename, its waiting for input from stdin (i.e., the keyboard). Since its in the background there is no keyboard.

---

### Post by matimont on 2013-03-28
> **Slim Odds said:**
> Since you didn't give it a filename, its waiting for input from stdin (i.e., the keyboard). Since its in the background there is no keyboard.

Thanks, so I could run something like this?:
grep -r "word">results.txt &

---

### Post by sudodus on 2013-03-28
grep searches files or data streams for patterns. in your case you search for ***word*** recursively (in the current directory and below). But you have not entered any file name. And you should not redirect the output to where you search, so I suggest something like this

```
grep -r "word" ***.txt** > /tmp/results.txt &
```

to search for word in txt-files in the current directory and below.

---

