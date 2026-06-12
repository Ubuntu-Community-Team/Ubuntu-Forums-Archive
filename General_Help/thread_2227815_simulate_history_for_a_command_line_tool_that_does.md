---
title: "simulate history for a command line tool that doesn't have a history itself"
date: 2014-06-04
forum: General Help
---

### Post by freak42 on 2014-06-04
Hi,

I seem to have a somewhat unusual (but maybe interesting!) problem (as I was unable to find any solutions nor discussions to my issue):
At work I use a command line application tool which has it's own prompt (like if you start mysql or python on the command line).
Unfortunately this tool doesn't have a history function which is very(!) annoying. I was wondering if it was possible to somehow simulate a history function with an external 
tool (or an application which wraps this command line tool and actually passes the keystrokes along to give a similar history functionality as in bash)?

I greatly appreciate any input.

---

### Post by sudodus on 2014-06-04
1. Maybe it would work to pipe the input and output via tee to a file and the screen. (I tested that it works with ***bc***).

Dialogue:
```
[COLOR=#0000ff]tee -a tlog|bc|tee -a tlog[/COLOR]
10*10
100
11*9
99
quit
^C
```

output log file:
```
[COLOR=#0000ff]cat tlog[/COLOR]
10*10
100
11*9
99
quit

```


2. If you tell us more about the command line application tool, someone might have an alternative. But there are real script gurus at the Ubuntu Forums, who know much more than I, so let us hope there is a good solution also if redirection and piping do not work.

3. If you can get the source code, you can modify it to write a log file when requested.

---

### Post by dragonfly41 on 2014-06-04
If you can elaborate further on the target command line application tool it might be possible to suggest editing the source code to include logging.   Is it written in python?

If you cannot edit the source code of the tool then you could install **Autokey** from Ubuntu Software Centre and use to log key strokes when the tool is invoked.

By expanding more on what command line tool you are using you can avoid us just guessing.

[color=maroon]Later edit ...

This is what sudodus wrote above .. explain more about the tool.
[/color]

---

### Post by freak42 on 2014-06-04
Hi guys,

thanks for inputs, the application is Intersystems Caché, and no I can neither replace it with anything else unfortunately, nor do I (or will I ever) get access to the source code. That's why I've asked the question in such a general manner.

Basically what I am looking for at this moment (as this system is so closed down) is an application that effectively simulates a history feature for (any) command line tool. I.E.: An application that sits in between my terminal and the actual app, records key strokes and plays them back if I use history functionality (such as up arrow..etc).

Hope this helps

---

### Post by dragonfly41 on 2014-06-04
I've looked at Intersystems Caché video .. Tools for Caché

and I would still bet that Autokey (in Ubuntu) or its equivalent AutoHotKey (in Windows)
would allow you to build an abstraction to log keys and history of usage.

Are you trying to monitor history of commands run in Terminal or Studio?

---

### Post by sudodus on 2014-06-04
> **freak42 said:**
> Hi guys,

thanks for inputs, the application is Intersystems Caché, and no I can neither replace it with anything else unfortunately, nor do I (or will I ever) get access to the source code. That's why I've asked the question in such a general manner.

Basically what I am looking for at this moment (as this system is so closed down) is an application that effectively simulates a history feature for (any) command line tool. I.E.: An application that sits in between my terminal and the actual app, records key strokes and plays them back if I use history functionality (such as up arrow..etc).

Hope this helps

Did you test the simple trick with ***tee***?

> **dragonfly41 said:**
> I've looked at Intersystems Caché video .. Tools for Caché

and I would still bet that Autokey (in Ubuntu) or its equivalent AutoHotKey (in Windows)
would allow you to build an abstraction to log keys and history of usage.

Are you trying to monitor history of commands run in Terminal or Studio?

I have not tried ***Autokey*** (in Ubuntu) or its equivalent ***AutoHotKey*** (in Windows) but it looks promising (and a bit more advanced than the simple tee trick).

Good luck :-)

---

### Post by dragonfly41 on 2014-06-04
I have an afterthought ... which does not require tools such as AutoKey.

perhaps you could list all the system commands to your InterSystems Cache methods ..

and then create a similar list of aliases which can be added to .bashrc file.

Then the idea is that each alias acts as a "proxy" to first invoke a trace/log function in a bash script before passing the call on to the true InterSystems Cache method.

For example, I use an alias in .bashrc to switch different versions of python.

---

### Post by freak42 on 2014-06-06
Hi Guys,

thanks for your input(s). I have tee & autokey briefly and wasn't very successfull, but maybe I'm not yet using autokey correctly.

Dragonfly41's input goes in the right direction, imo. The "proxy" thing is really what I think is the right direction. However are bash alias evaluated before passing them to a command line app (if the app is already running)?

I guess I'd also have to look into writing my own proxy for the command line. (I've never written any complex terminal applications, so I am a bit stumped on where to start..)

---

### Post by dragonfly41 on 2014-06-06
Here is the general rough idea ...

In /usr/bin/ you'll find the apps which are launched.

I don't know what apps are launched through cache API (which is why I suggested you list these for us to read).

Take /usr/bin/mysql for example (not a cache app).

You could rename [COLOR=#0000cd]mysql[/COLOR] to (for example) [COLOR=#0000cd]mysql_proxy[/COLOR]

Then in /usr/bin/ place a proxy script named mysql. Make this executable.

Calling mysql from say Cache Studio would then pass through the proxy which would call mysql_proxy instead of mysql.

No need for aliases in this case.

Incidentally I did read the download option but couldn't see any way of installing cache in ubuntu to test this idea.

---

### Post by sudodus on 2014-06-06
You can also develop the simple tee trick like this example with ***bc***

- **tin** (file for input)
- **tut** (file for output)
- **tlog** (for for input and output in due order (like in the terminal)

and you can use ***gedit*** to monitor the files. It will show when the file is modified and prompt you to update it. It is easy to scroll the input to mark and paste if you want to repeat a command or maybe modify it.

 ```
gedit tin tut tlog &
```

```
tee -a tlog tin|bc|tee -a tlog tut
```

---

