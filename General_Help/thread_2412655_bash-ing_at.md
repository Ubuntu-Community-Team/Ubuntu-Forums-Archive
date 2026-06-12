---
title: "bash-ing at"
date: 2019-02-15
forum: General Help
---

### Post by Langstracht on 2019-02-15
I have been trying - and failing miserably - to produce the following:

an .sh file which, when opened, would start a stream of commands that would, after chunks of time, open web pages.

So, something like this:

```


#!/bin/sh
#----------------------------------------------
at now + 1 min firefox "https:://anysite.com"

at now + 2 min firefox "https://anothersite.com"


```

I have played around with the order of the command contents and with the "-f" option.  And get nothing but "Last token" and "garbled time" error messages.

If someone could point out what I am doing wrong I'd muchly appreciate it.

If, on the other hand, someone can point out that what I am trying to do is not possible ... well, I'd appreciate too ... but maybe a little less

TIA

---

### Post by spjackson on 2019-02-15
at doesn't get command(s) to run from the command line; it gets them from standard input or from a file (with -f).
```
echo 'firefox "https:://anysite.com"' | at now + 1 min
```
I don't know about running a gui program from at - I've never done that. I suspect it could be problematic

---

### Post by Langstracht on 2019-02-15
Thanks so much for taking the time to get back to me.

I'm not sure if you were offering up the code as what might possibly work ... or you had used it successfully yourself.

In any event it did not work for me.

I hadn't realized that "echo" could be used to start a command - thanks for that nugget.

Sorry to say I don't understand your reference to a GUI programme.  I understood "at" to be in CLI country ...

---

### Post by again? on 2019-02-15
The "at" manpage says...
> As at is currently implemented as a [**_setuid_**]("https://www.computerhope.com/jargon/s/setuid.htm") program, other environment variables (e.g. LD_LIBRARY_PATH or LD_PRELOAD) are also not exported. 
This may change in the future. As a workaround, set these variables explicitly in your job.

This works for me.
```
at now + 1 minute -f /home/glen/scripts/aatest.sh
```

The script at calls..._**/home/glen/scripts/aatest.sh**_
```
#!/bin/bash

export DISPLAY=:0.0
export DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus

firefox "https://duckduckgo.com" &
sleep 60
firefox "https://www.wikipedia.org" &

```

I'm not an expert at this stuff but I have had to export those 2 environment variables to start a GUI application with a systemd service.
Check your environment variables with...
```
env
```
or individually with... 
```
printenv DISPLAY
printenv DBUS_SESSION_BUS_ADDRESS
```

You may only need to set the DISPLAY env variable, as this will also launch firefox for me using at..
```
echo "export DISPLAY=:0.0 ; firefox https://duckduckgo.com" | at now + 1 min
```

What I did notice is that the command "**at now + 1 minute**" does not run in one minute's time but at the start of the next minute in the time of day.
I.E when the seconds hit :00

Wouldn't it be easier to just run a bash script using sleep intervals.
```
#!/bin/bash

sleep 60
firefox "https://www.wikipedia.org" &
sleep 60
firefox "https://duckduckgo.com" &

```

---

### Post by Langstracht on 2019-02-16
Thanks guber2 for your response.

It'll take me a while to work through it.  But, that said, I hadn't thought of sleep(ing).  And, for sure it would be a whole lot simpler.

I'll be trying that first.

Thanks again!

---

### Post by spjackson on 2019-02-16
> **Langstracht said:**
> Sorry to say I don't understand your reference to a GUI programme.  I understood "at" to be in CLI country ...
"at" is CLI country but "firefox" is a GUI program. Setting the environment variables as per gruber2's post may be enough.

---

### Post by Langstracht on 2019-02-17
I am happy to report that I now have 3 .sh files that do exactly what I want.

I should have been able to go to sleep by myself.  But I guess you live and learn.

Thanks for your much appreciated help.

---

