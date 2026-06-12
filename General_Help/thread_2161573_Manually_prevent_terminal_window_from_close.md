---
title: "Manually prevent terminal window from close"
date: 2013-07-11
forum: General Help
---

### Post by nsk7even on 2013-07-11
Hi,

assuming this is not possible I will ask nevertheless. I tried to find s. th. via search machine but it is difficult as I only find scripting solutions.

But my use case is different:
Manually prevent a terminal window that was opened via an arbitrary command that is called from arbitrary sources from automatic close after end of command.

Why?
To be able to read a) the command(s) b) the result

Example:
After showing a dialog that it could not automatically download update files flashplugin-installer update mechanism launches some download commands in a terminal window which I would like to read as I don't know whether they succeed or not and it makes any sense therefore to always run this update. Because this includes typing my password for root access and so on...

But this is an example only, so please please don't argue anything about flashplugin! This is not the question as there are similar situations everywhere (e. g. plymouth selection, launched via BUM).

As introduced above, I accept an answer that may be: not possible

---

### Post by sudodus on 2013-07-11
One way is to use xterm and the hold option.

```
xterm -hold
```

Compare these two commands

```
xterm -e cat /etc/mtab
```

```
xterm -hold -e cat /etc/mtab
```

---

### Post by nsk7even on 2013-07-11
Thanks for the answer this is interesting in general.
But I am not the author of the command call. What I am searching for is a possibility to kind of "grab" the popped up terminal window and kind of "hold" it to prevent it from being closed automatically.

---

### Post by steeldriver on 2013-07-11
Have you tried changing the default gnome-terminal profile's behavior to "When command exits: Hold the terminal open"? (Edit --> Profile preferences --> Title and Command tab). Might work.

---

### Post by sudodus on 2013-07-11
I see what you want, I have no solution but I think there is one. If you are lucky one of the real shell-script gurus will see this thread and help you.

---

### Post by sudodus on 2013-07-11
What happens if you start that program from a terminal window? Will it write to that window (which will stay open), or will it open a new window that will be closed anyway? 

And please let us know the result of steeldriver's suggestion!

---

### Post by nsk7even on 2013-07-11
> **steeldriver said:**
> Have you tried changing the default gnome-terminal profile's behavior to "When command exits: Hold the terminal open"? (Edit --> Profile preferences --> Title and Command tab). Might work.
Aaah thats a good idea!

> **sudodus said:**
> What happens if you start that program from a terminal window? Will it write to that window (which will stay open), or will it open a new window that will be closed anyway?
In both cases a new terminal is opened which - of course - is main part of the problem as I tried already to launch the calling commands from terminal, just to see if the output may be copied there additionally ... but - as expected - this was not the case.

I just saw an update of flashplugin-installer in update-manager, but it installed without questioning me this time! :D
 Now it may take some time until the next update arrives.

I don't remember another example which may be triggered manually. The plymouth theme selection via bum calls xterm and not gnome-terminal (additionally this example was not as important as flashplugin-installer, because I found out how to call the plymouth command directly)

Therefore: thanks to all answers for now!

---

### Post by nsk7even on 2013-07-12
I forgot that when having flashplugin-installer updated at home, the same will expect me at work.
Therefore I had the chance to test steeldriver's proposed solution - and of course this worked! :)

[IMG]http://www.nskcomputing.de/tmp/screen-no-close-works-of-course.png[/IMG]

This is not an all-in-all solution because of its specific configuration setting of gnome-terminal profile, but in this actual case this works well. Now I can read the output and confirm that it makes sense to: click on the action button and type in my password and click on close of the underlying dialog on 2 machines at work plus 2 machines at home which is much work! :D

So thanks again to all answers.

---

