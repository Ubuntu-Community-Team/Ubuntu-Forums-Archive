---
title: "stoping bash programs"
date: 2007-09-06
forum: General Help
---

### Post by peromalosutra on 2007-09-06
Is there any way to stop the program that is running in terminal window without closing the terminal windows itself? For example, if i type "ping localhost" in terminal window (without specifing -c argument) it wil execute ping command every second, but this process cannot be stoped by any combination of keys that i know (for example ctrl+d, or simple 'q') and it will run until i close terminal window with x button.. Ping is jus one example, there is a lof of other programs running in the terminal that behave similar (mbmon is another example).  This is not big problem in X, but what if I am in the recovery console? I would have to reboot? :s

So,  how can I regain control of my terminal window (or bash shell)? :)

Thanks.

---

### Post by reckless2k2 on 2007-09-06
stop the ping and most programs from bash just hit ctrl+c together.

---

### Post by peromalosutra on 2007-09-06
It's working, thanks alot. (i knew there must be a combination like that, I tried ctrl+d, but that didn't worked.. anyway, now I know, thanks again.)

---

### Post by reckless2k2 on 2007-09-06
not a problem at all. glad to be of help.

---

### Post by apetresc on 2007-09-06
reckless2k2 is correct; Ctrl+C sends what is called a "SIGTERM" signal to that process, which tells it to TERMinate. You can google further about UNIX signals for more on how that works, and how to use it in your own programs.

But to give a more general answer than reclkess', one that will also work on, say, background processes or daemons, I reccomend familiarizing yourself with the 'top' and 'ps'+'grep' commands.

'top' will give you a nicely formatted table of all the running processes on your system, which you can sort and aggregate on a variety of things. In particular, the first column gives you the PID (Process ID) of each process, which will come in handy a little bit later. You can, for example, tell top to sort processes by the amount of memory they are consuming, so you can easily get the PID of the most cumbersome processes on your system in a jiffy, simply by typing a capital 'M' while running top. Easy! Make sure to write down the PID of any processes you want to stop for later use.

Another, more specific, way is using the 'ps' command to list *all* the running processes on your system, then using the 'grep' utility to get information about a specific one. So if I wanted the PID of firefox on my machine, I would type ```
apetrescu@glucose-fructose:~$ ps aux | grep firefox
20047    15353  4.0 12.9 471756 56932 ?        Sl   15:06   0:47 /usr/lib/iceweasel/firefox-bin -a firefox
```
which tells me that the PID of my Firefox session (actually, my Iceweasel session :)) is 20047.

Now that I know the PID of the process I want to kill is, I simply type ```
kill 20047
``` or whatever the PID may happen to be. Voila! Your application will be stopped without having to close the terminal, X, etc.

Good luck! :)

---

### Post by peromalosutra on 2007-09-06
@AdrianP thank you for your detailed answer. I have tried the commands you mentioned in your post (altough I'we heard of them before, I haven't actually used them).. Seams like a good way of stoping programs with infinite loop :) I'we been doing this earlier in System Manager from X, but this is better, since i'm alredy in terminal, executing my program.. I haven't tried this yet (breaking program that is not responding) but ctrl+c shuld also work (if I'm in terminal window where my program is actualy running)?

---

### Post by reckless2k2 on 2007-09-06
yeah AdrianP is showing off. hahahaha. next thing AdrianP will will talk to you about bg, fg, and ctrl+z and all that goodness. hahahaha

---

### Post by apetresc on 2007-09-06
> **peromalosutra said:**
> I haven't tried this yet (breaking program that is not responding) but ctrl+c shuld also work (if I'm in terminal window where my program is actualy running)?
Yes, of course, Ctrl+C will also work, but only for programs where stdin is bound to a terminal you currently have open. So it won't work on background tasks, or bash scripts you run with "&" at the end. All it does is send a SIGTERM signal, similarly to how 'kill' sends a SIGKILL signal. My way is just more general and works in more situations. However, it is also longer so you should use Ctrl+C wherever it works.

> yeah AdrianP is showing off. hahahaha. next thing AdrianP will will talk to you about bg, fg, and ctrl+z and all that goodness. hahahaha
Hey, hey, just giving a thorough answer ;) POSIX signals are an interesting way to control certain things about certain processes.

---

### Post by peromalosutra on 2007-09-06
For test, i compiled this 3 useless lines:

int main(void) {
        while(1);
        return 0;
}

and started program.. Processor went to 100% but as soon as i presed ctrl+c, it all went back to normal..  As borat would said, that's niiiiceee :lolflag:

---

