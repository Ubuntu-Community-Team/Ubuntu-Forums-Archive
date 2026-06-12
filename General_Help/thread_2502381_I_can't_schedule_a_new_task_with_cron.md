---
title: "I can't schedule a new task with cron"
date: 2024-11-12
forum: General Help
---

### Post by chetinho10 on 2024-11-12
[COLOR=#000000]Hello.

I am not being able to schedule a task with crontab to execute a .run file, I put the path to the executable and it does nothing.

I have also tried creating the task with the Crontab UI interface, but it does not execute either.

I guess it's because it asks for the $DISPLAY variable when I run the file from the terminal.

I would appreciate if there is any way I can run it through a scheduled task with crontab.

Greetings.[/COLOR]
[COLOR=#000000]
[/COLOR]

---

### Post by TheFu on 2024-11-13
You can't run GUI programs from the crontab without providing a GUI session for that connection. Usually it is best to find a different timer technique since GUI programs aren't meant to be run from crontabs.

But you can setup an Xvfb if you like. Just be ready for failures.  [https://en.wikipedia.org/wiki/Xvfb](https://en.wikipedia.org/wiki/Xvfb)  25 yrs ago, I had to do this at work for some terrible server software created by Oracle that didn't actually need a GUI, but their programmers included some X/Windows libraries, I suppose due to habit or convenience, that mandated it.  We pointed it out to them, saying they should be embarrassed for a server process to require any GUI.  It wasn't enough to make them change it, unfortunately.

Of course, using the Xvfb you don't get to access the GUI or interact with the tool in anyway except though some client/server methods. For server software, this is expected anyway, so it shouldn't matter.

BTW, .run file is meaningless.  Extensions don't matter to Linux/Unix. They are only useful for humans and arbitrary ... or can be completely wrong, since the OS doesn't care.

Lastly, if you want help with your crontab line, you'll need to post it here.  Seems pretty obvious, right?

---

