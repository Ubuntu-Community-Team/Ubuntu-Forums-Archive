---
title: "How to start background service?"
date: 2006-07-12
forum: General Help
---

### Post by AlliumPorrum on 2006-07-12
Hi!

I aleardy searched the forums, but did not find an answer to my problem...

I made a small Java application that I would like to be running all the time on the background. How can I do this from the CLI? I mean, how can I start my own Java application to be running kind of a daemon?

---

### Post by taurus on 2006-07-12
You can add that to your /etc/crontab or do something like this from a terminal.
```

<program name> &

```

---

### Post by AlliumPorrum on 2006-07-12
That's what I already tried, I gave a command to run my own script like this:

./myapp.sh &

Anyway, that didn't seem to work; if I closed the console where I gave the command, the java process was also killed. BUT, when I added that '&' to the end of 'myapp.sh', and then executed it normally, that was it and now it works! 

BTW, if I want to connect to that process later on, how can I do that? If I for example want to check that what it has been writing to the console. 

And hey, thanks!

---

